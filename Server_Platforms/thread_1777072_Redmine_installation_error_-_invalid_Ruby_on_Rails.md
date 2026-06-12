---
title: "Redmine installation error - invalid Ruby on Rails application root"
date: 2011-06-07
forum: Server Platforms
---

### Post by sipickles on 2011-06-07
Hello,

I am trying to install redmine onto 10.04, as detailed [here]("http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_in_Ubuntu")

I used the passenger method, and all seemed to go very smoothly during setup.

Unfortunately when I goto the redmine page I get a Passenger page which says:

```
Cannot start Ruby on Rails application
The directory "/var/www" does not appear to be a valid Ruby on Rails application root.
```

Apache setup isnt my strong point so any help gratefully received.

Heres my /etc/apache2/sites-available/default:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        <Directory /var/www/redmine/>
                RailsBaseURI /redmine
                PassengerResolveSymlinksInDocumentRoot on
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Thanks

Si

---

### Post by Joespower on 2011-08-04
I'm having the same issues using the same website (among others) as reference.  The documentation here doesn't appear to be current/complete.  If someone has gotten this to work, can you help a brotha out?

---

### Post by tomsdongle on 2011-08-04
having the same issue here - receiving exactly the same error.

To confirm,

do you change the permissions of passenger.conf to www-data?

also, is my passenger.conf correct:


[HTML]<IfModule mod_passenger.c>
PassengerDefaultUser www-data
 PassengerRoot /usr
  PassengerRuby /usr/bin/ruby
</IfModule>[/HTML]

---

### Post by maniat1k on 2011-09-30
Hi!
I'm trying to get this working on Ubuntu 11.04. And I'm also having troubles with passenger. But I'm not having the same error as the other..

the error
```
service apache2 restart
Syntax error on line 6 of /etc/apache2/sites-enabled/redmine:
Invalid command 'PassengerDefaultUser', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

the apache log

```
[Fri Sep 30 10:42:16 2011] [error] *** Passenger could not be initialized because of this error: The Passenger spawn server script, '/usr/lib/ruby/gems/1.8/gems/passenger-3.0.9/lib/phusion_passenger/passenger-spawn-server', does not exist. Please check whether the 'PassengerRoot' option is specified correctly.

```

 vi /etc/apache2/mods-available/passenger.conf

```
<IfModule mod_passenger.c>
  PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-3.0.9
  PassengerRuby /usr/bin/ruby1.8
  PassengerDefaultUser www-data

</IfModule>

```


vi /etc/apache2/apache2.conf (at the bottom of the con file)

```
Include /etc/apache2/mods-available/passenger.conf
```


vi /etc/apache2/sites-available/redmine (instead of default)

```
<VirtualHost *:80>
    ServerName redmine

    DocumentRoot /var/www/redmine/public

    PassengerDefaultUser www-data
    RailsEnv production
    RailsBaseURI /redmine
    SetEnv X_DEBIAN_SITEID "default"

    <Directory /var/www/redmine/public>
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>
```

I used this manual [http://www.x2on.de/2011/04/23/tutorial-redmine-with-git-and-gitosis-on-ubuntu-11-04/]("http://www.x2on.de/2011/04/23/tutorial-redmine-with-git-and-gitosis-on-ubuntu-11-04/") It has details but you can follow it.

**Running the test works.**
you go to  cd /var/www/redmine
and by doing 

```
ruby script/server webrick -e production
```

In the browser I put [http://redmine:3000](http://redmine:3000) and works :p
Hopefully someone can lend us a hand.:)

---

### Post by maniat1k on 2011-10-06
@sipickles It's looks like your sites-available is wrong.. look at mine or **look the example I used to create mine**... try that and show us your progress. **Let's try help each other ¿ok?**

---

