require 'rubygems'
require 'rake'
require 'spec/rake/spectask'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "grep-fu"
    gem.summary = %Q{Grep-Fu is a very fast, Rails-oriented command-line helper script for grep.}
    gem.description = %Q{Grep-Fu is a very fast, Rails-oriented command-line helper script for grep.}
    gem.email = "calamitous@calamitylane.com"
    gem.homepage = "http://github.com/Calamitous/grep-fu"
    gem.authors = ["Eric Budd"]
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

desc "Run all specs"
Spec::Rake::SpecTask.new('run_specs') do |t|
  t.spec_files = FileList['spec/**/*.rb']
end

task :test => [:check_dependencies, :run_specs]

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "grep-fu #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
