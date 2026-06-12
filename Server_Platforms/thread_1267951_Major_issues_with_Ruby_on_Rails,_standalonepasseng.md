---
title: "Major issues with Ruby on Rails, standalone/passenger"
date: 2009-09-16
forum: Server Platforms
---

### Post by pthanos on 2009-09-16
Hi all,

I am trying to install a ruby on rails app (redmine). I have installed all the necessary things that allow me to launch the application through the webrick standalone server (./script/server).

The firs issue is that this server performs extremely slowly. I really don't care because the final goal is to run apps through Apache, but still I think that this may actually be connected to the problems I will describe next. Any ideas with WEBrick is so slow?

Then I installed passenger. It seems to be running ok and I get no apache errors. When I make requests though, the server takes for ever to reply and in the end nothing happens. Checking the logs, I get a > [ pid=13367 file=Hooks.cpp:625 time=09/16/09 17:17:38.153 ]:
  Cannot initialize Passenger in an Apache child process: Could not connect to the ApplicationPool server: Broken pipe (32) (this warning is harmless if you're currently restarting or shutting down Apache)

[Wed Sep 16 17:17:38 2009] [notice] child pid 13362 exit signal Aborted (6)


My apache sites-available/default (the only definition I have) looks like this:
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/
        ServerName 127.0.0.1

         RailsBaseURI /var/www/redmine
         RailsEnv development
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
...rest is default

```

/var/www/redmine is a sym-link to the /public of the RoR app I want to run. When I do a2enmod passenger, all requests to the webserver hang forever. When I disable it, it serves everything as normal pages.

What should I do?

---

### Post by t3r0 on 2009-09-16
Hi,

remove the RailsBaseUri and point your DocumentRoot to the RAILS_ROOT/public/ 

The RailsBaseUri is ment only to be used when runing rails in subfolder.
see [http://www.modrails.com/documentation/Users%20guide%20Apache.html#deploying_rails_to_sub_uri](http://www.modrails.com/documentation/Users%20guide%20Apache.html#deploying_rails_to_sub_uri) for more details

Also change your RailsEnv to production.. 


- Tero

---

### Post by pthanos on 2009-09-16
Thank you for your reply tero.

I have moved the whole app inside /var/www/ and pointed the DocumentRoot to /var/www/myapp/public. I deleted the RailsBaseUri directive, and set the env to production.

Still I get the same exact error, and http requests never return anything. I googled even more and have a suspition that it could be a permissions deal? Maybe apache can't write where the passenger module is sitting?

---

### Post by pthanos on 2009-09-17
[http://wiki.ousli.org/index.php/RedmineUbuntu](http://wiki.ousli.org/index.php/RedmineUbuntu)

In the end, I had installed the passenger module both with apt and with gem. This by itself was capable of screwing passenger completely. The guide above is the solution to this problem..

---

