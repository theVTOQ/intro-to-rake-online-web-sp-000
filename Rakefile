task :environment do
  require_relative "./config/environment.rb"
end

namespace :greeting do
  desc 'outputs hello to the terminal'
  task :hello do
    puts "hello from Rake!"
  end

  task :hola do
    puts "hola de Rake!"
  end
end

desc 'drop into the pry console'
task :console => :environment do
  Pry.start
end


namespace :db do
  desc 'migrate changes to your database'
  task :migrate => :environment do
    sql = <<-SQL
        CREATE TABLE students (
          id INTEGER PRIMARY KEY,
          name TEXT,
          grade INTEGER);
    SQL

    DB[:conn].execute(sql)
  end

  task :seed => :migrate do
    require_relative "./db/seeds.rb"
  end
end
