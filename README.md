# How-to-setup-a-new-rails-app

1) Create a new app
```
rails new <app-name> --database=<database-name>
eg: rails new quora --database=postgresql
```
2) Specify ruby version in `Gemfile`, eg: `ruby '2.2.1'`

3) Create a new database
```
rake db:create
```
4) Setup rspec, shoulda, and capybara(selenium driver)
  * Add following gems to 'Gemfile'
```
gem 'puma'
  
group :development, :test do
  gem 'guard'
  gem 'guard-rspec'
  gem 'guard-puma'
  gem 'rspec'
  gem 'rspec-rails'
  gem 'shoulda-matchers'
  gem 'shoulda-callback-matchers'
  gem 'capybara'
  gem 'selenium-webdriver'
  gem 'capybara-webkit'
end
```
  * Bundle install
  * Initialize rspec and guard
```
$ rails generate rspec:install
$ guard init rspec
$ guard init puma
```
  * Place the Shoulda Matcher configuration in `spec/rails_helper.rb`:
```
Shoulda::Matchers.configure do |config|
  config.integrate do |with|
    with.test_framework :rspec
    with.library :rails
  end
end
```
  * Add this line to `spec/test_helper.rb`:
```
require 'capybara/rails'
```
## Terminal command
1. To start **server**, `rails s`
2. To start **console**, `rails c`
3. To generate/destroy **model**, `rails g/d model <model-name> <attributes>`
4. To generate/destroy **migration**, `rails g/d migration <migration-name> <attributes>`
5. To start guard, `guard`

## Note
1. Rails will auto generate `README.rdoc`, change this file name to `README.md` in order to use Github markdown.

