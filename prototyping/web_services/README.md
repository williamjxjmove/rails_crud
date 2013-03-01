# Goal Settings Web Service

## Features:


Can search by different columns:

<ul>
<li> ID </li>
<li> User </li>
<li> Phone </li>
<li> E-mail </li>
<li> First Nam </li>
<li> Last Nam </li>
<li> ... ... </li>
</ul>


## Usage:

$ cd __HERE__

$ rails server


$ In browser:

(1) http://localhost:3000/phone/1111111111.json 

(2) http://localhost:3000/user/kh.json 

(3) http://localhost:3000/fname/william.json 

(4) http://localhost:3000/lname/last.json 

## keys:

$ rails new webservice --skip-active-record

$ subl. rest/Gemfile:

require 'mongo'
  gem 'mongo_mapper', '~> 0.12.0'
  gem 'bson_ext', '~> 1.8.2'
  gem 'bson', '~> 1.8.2'
  gem 'mongo', '~> 1.8.2'


$ bundle install

$ subl. config/initializers/mongo_config.rb:

MongoMapper.connection = Mongo::Connection.new('localhost', 27017)
MongoMapper.database = "test"
 
if defined?(PhusionPassenger)
  PhusionPassenger.on_event(:starting_worker_process) do |forked|
  MongoMapper.connection.connect if forked
   end
end


$ rails generate scaffold tpouser user:string --skip-migration --orm mongo_mapper

$ rails generate model Info  first_name:string last_name:string phone:string e_mail:string --skip-migration --orm mongo_mapper

$ rails generate model Count contacts:Integer prospects:Integer closings:Integer listings:Integer --skip-migration --orm mongo_mapper


$ do coding...
