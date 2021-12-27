source 'https://rubygems.org'

gem 'rake'

platforms :ruby do
  # Rails 5.1 is the first to work with sqlite 1.4
  # Rails 6 now requires sqlite 1.4
  if ENV['RAILS_VERSION'] && ENV['RAILS_VERSION'] < '5.1'
    gem 'sqlite3', '< 1.4'
  else
    gem 'sqlite3'
  end
end

platforms :jruby do
  if ENV['RAILS_VERSION'] == '4.2.0'
    gem 'activerecord-jdbcsqlite3-adapter', '< 50.0'
  elsif ENV['RAILS_VERSION'] == '5.0.0'
    gem 'activerecord-jdbcsqlite3-adapter', '~> 50.0'
  elsif ENV['RAILS_VERSION'] == '5.1.0'
    gem 'activerecord-jdbcsqlite3-adapter', '~> 51.0'
  elsif ENV['RAILS_VERSION'] == '5.2.0'
    gem 'activerecord-jdbcsqlite3-adapter', '~> 52.0'
  elsif ENV['RAILS_VERSION'] == '6.0.0'
    gem 'activerecord-jdbcsqlite3-adapter', '~> 60.0'
  elsif ENV['RAILS_VERSION'] == '6.1.0'
    gem 'activerecord-jdbcsqlite3-adapter', '~> 61.0'
  else
    gem 'activerecord-jdbcsqlite3-adapter'
  end
  gem 'jruby-openssl'
  gem 'mime-types', ['~> 2.6', '< 2.99']
  if ENV['RAILS_VERSION'] == 'edge'
    gem 'railties', :github => 'rails/rails'
  elsif ENV['RAILS_VERSION']
    gem 'railties', "~> #{ENV['RAILS_VERSION']}"
  else
    gem 'railties', ['>= 3.0', '< 7.1']
  end
end

platforms :rbx do
  gem 'psych'
end

group :test do
  if ENV['RAILS_VERSION'] == 'edge'
    gem 'actionmailer', :github => 'rails/rails'
    gem 'activerecord', :github => 'rails/rails'
    gem 'railties', :github => 'rails/rails'
  elsif ENV['RAILS_VERSION']
    gem 'actionmailer', "~> #{ENV['RAILS_VERSION']}"
    gem 'activerecord', "~> #{ENV['RAILS_VERSION']}"
    gem 'railties', "~> #{ENV['RAILS_VERSION']}"
  else
    gem 'actionmailer', ['>= 3.0', '< 7.1']
    gem 'activerecord', ['>= 3.0', '< 7.1']
    gem 'railties', ['>= 3.0', '< 7.1']
  end
  gem 'net-smtp' if Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.1.0')
  gem 'rspec', '>= 3'
  gem 'simplecov', :require => false
  if /\A2.[12]/ =~ RUBY_VERSION
    # 0.8.0 doesn't work with simplecov < 0.18.0 and older ruby can't run 0.18.0
    gem 'simplecov-lcov', '< 0.8.0', :require => false
  else
    gem 'simplecov-lcov', :require => false
  end
end

group :rubocop do
  gem 'rubocop', '>= 0.25', '< 0.49'
end

gemspec
