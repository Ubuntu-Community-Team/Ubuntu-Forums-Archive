---
title: "mysqld.sock error - but is it?"
date: 2009-03-07
forum: Server Platforms
---

### Post by mpetro on 2009-03-07
Hi folks,

I am receiving the following error and I need help resolving the issue:

Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I don't believe it is related to the mysql connections because I can connect on the command line using the credentials that are in my database.yml file.  In fact, the scaffold command in rails creates the table as described in the command.  I just can't access the views for the controllers and I receive the above error message.  I can access the rails app home page as [http://testapp](http://testapp).

Anyway here are some particulars:

Using ruby 1.8.6 and rails 2.1.0, mysql 5.0.51a, apache2 2.2 with phusion passenger 2.0.6 and Ubuntu 8.04.

Machine#1, hostname Dave, contains the mysql server.
Machine#2, hostname Fred, contains ruby, rails environment and apache2.

There are no firewalls running on either machine, as I have removed them to get this to work.  The persmissions seem to be in order, but I am not certain about this.  The virtual host file located in sites-available directory is as follows:

    <VirtualHost *>
    ServerName testweb
    DocumentRoot .../testweb/public
	    
    ErrorLog /var/log/apache2/error.log
    </VirtualHost>

The document root points to the absolute path to the public folder of the rails app and there are no entries in the error.log for the failure.

The html error page is as follows:

 Mysql::Error in ContactsController#index

Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/mysql_adapter.rb:505:in `real_connect'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/mysql_adapter.rb:505:in `connect'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/mysql_adapter.rb:183:in `initialize'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/mysql_adapter.rb:88:in `new'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/mysql_adapter.rb:88:in `mysql_connection'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/abstract/connection_specification.rb:292:in `send'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/abstract/connection_specification.rb:292:in `connection='
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/abstract/connection_specification.rb:260:in `retrieve_connection'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/connection_adapters/abstract/connection_specification.rb:78:in `connection'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.1.0/lib/active_record/query_cache.rb:8:in `cache'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/caching/sql_cache.rb:12:in `passenger_orig_perform_action'
/usr/lib/ruby/1.8/passenger/railz/request_handler.rb:53:in `perform_action'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/base.rb:529:in `send'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/base.rb:529:in `process_without_filters'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/filters.rb:569:in `process_without_session_management_support'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/session_management.rb:130:in `process'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/base.rb:389:in `process'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/dispatcher.rb:149:in `handle_request'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/dispatcher.rb:107:in `dispatch'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/dispatcher.rb:104:in `synchronize'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/dispatcher.rb:104:in `dispatch'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/dispatcher.rb:120:in `dispatch_cgi'
/usr/lib/ruby/gems/1.8/gems/actionpack-2.1.0/lib/action_controller/dispatcher.rb:35:in `dispatch'
/usr/lib/ruby/1.8/passenger/railz/request_handler.rb:38:in `process_request'
/usr/lib/ruby/1.8/passenger/abstract_request_handler.rb:165:in `main_loop'
/usr/lib/ruby/1.8/passenger/railz/application_spawner.rb:321:in `start_request_handler'
/usr/lib/ruby/1.8/passenger/railz/application_spawner.rb:282:in `handle_spawn_application'
/usr/lib/ruby/1.8/passenger/utils.rb:163:in `safe_fork'
/usr/lib/ruby/1.8/passenger/utils.rb:161:in `fork'
/usr/lib/ruby/1.8/passenger/utils.rb:161:in `safe_fork'
/usr/lib/ruby/1.8/passenger/railz/application_spawner.rb:280:in `handle_spawn_application'
/usr/lib/ruby/1.8/passenger/utils.rb:163:in `safe_fork'
/usr/lib/ruby/1.8/passenger/utils.rb:161:in `fork'
/usr/lib/ruby/1.8/passenger/utils.rb:161:in `safe_fork'
/usr/lib/ruby/1.8/passenger/railz/application_spawner.rb:279:in `handle_spawn_application'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:317:in `__send__'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:317:in `main_loop'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:168:in `start_synchronously'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:135:in `start'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:112:in `fork'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:112:in `start'
/usr/lib/ruby/1.8/passenger/railz/application_spawner.rb:179:in `start'
/usr/lib/ruby/1.8/passenger/railz/framework_spawner.rb:270:in `handle_spawn_application'
/usr/lib/ruby/1.8/passenger/railz/framework_spawner.rb:263:in `synchronize'
/usr/lib/ruby/1.8/passenger/railz/framework_spawner.rb:263:in `handle_spawn_application'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:317:in `__send__'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:317:in `main_loop'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:168:in `start_synchronously'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:135:in `start'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:112:in `fork'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:112:in `start'
/usr/lib/ruby/1.8/passenger/railz/framework_spawner.rb:87:in `start'
/usr/lib/ruby/1.8/passenger/spawn_manager.rb:222:in `spawn_rails_application'
/usr/lib/ruby/1.8/passenger/spawn_manager.rb:217:in `synchronize'
/usr/lib/ruby/1.8/passenger/spawn_manager.rb:217:in `spawn_rails_application'
/usr/lib/ruby/1.8/passenger/spawn_manager.rb:126:in `spawn_application'
/usr/lib/ruby/1.8/passenger/spawn_manager.rb:251:in `handle_spawn_application'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:317:in `__send__'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:317:in `main_loop'
/usr/lib/ruby/1.8/passenger/abstract_server.rb:168:in `start_synchronously'
/usr/lib/passenger/passenger-spawn-server:46


Any help would be appreciated as I have spent too much time on this.  Thanks in advance.

-Mark

---

### Post by mrsteveman1 on 2009-03-08
Shouldn't machine 2 be trying to connect to machine 1's mysql daemon using TCP?

I may be reading what you said wrong :)

---

### Post by mpetro on 2009-03-09
Yes, you are correct.  Machine #2 should be connecting with Machine #1 via TCP.  Why it is not is the confusing part.  Here is my database.yml file:

development:
  adapter: mysql
  encoding: utf8
  database: 'testweb_development'
  username:dataman
  password: xxxxx
  host: Machine1HostName
  port: 3306

As I stated in my original message, I can connect with the db on the command line using the credential in the database.yml file.

I appreciate your looking at the issue.

-mpetro

---

### Post by mrsteveman1 on 2009-03-09
Does machine1s mysql database have permissions set to allow this user access from the IP you are connecting from?

---

### Post by mpetro on 2009-03-09
Yes, the user was given all privileges.  I can connect to machine1 from machine2 on the command line and execute commands with this user.  The user was granted with the username 'user'@'192.168.1.0/255.255.255.0'.

-mpetro

---

### Post by mrsteveman1 on 2009-03-09
So there are no problems connecting a mysql client to the daemon on the other machine.....

That means it has to be a problem with whatever that client you were using is, rails? Perhaps something wrong in the syntax of the file holding database info?

Is there a way to get better debug info out of the thing?

---

### Post by mpetro on 2009-03-10
Steve,

I appreciate you for taking the time to look at my issue.  I have decided to move to a different platform.

-Mark

---

