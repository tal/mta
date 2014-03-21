require "bundler/gem_tasks"

namespace :proto do
  desc "Generate ruby files from GTFS protobuf files"
  task :generate => ["require_protoc", "proto/nyct-subway.pb.rb", "proto/gtfs-realtime.pb.rb"]

  task "require_protoc" do
    unless system "which protoc >/dev/null"
      $stderr.puts "Error: You need protoc - the protoc buffer compiler"
      $stderr.puts "You can install it by running `brew install protobuf`"
      exit 1
    end
  end

  file "proto/nyct-subway.pb.rb" => ["proto/nyct-subway.proto"] do
    Dir.chdir('proto') do
      system "ruby-protoc nyct-subway.proto"
    end
  end

  file "proto/gtfs-realtime.pb.rb" => ["proto/gtfs-realtime.proto"] do
    Dir.chdir('proto') do
      system "ruby-protoc gtfs-realtime.proto"
    end
  end
end
