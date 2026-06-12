---
title: "Ruby on rails - redmine - FATAL: password authentication failed"
date: 2011-06-30
forum: Server Platforms
---

### Post by gypsumwolf on 2011-06-30
When I try and access redmine from the webbrowser i get an error:

```
FATAL: password authentication failed for user "redmine" FATAL: password authentication failed for user "redmine" (PGError)
```

Any advice?

I used these instructions to install redmine
[http://foxfoo.com/howto-install-redmine-on-ubuntu-11-04/](http://foxfoo.com/howto-install-redmine-on-ubuntu-11-04/)

---

### Post by rubylaser on 2011-06-30
This is sounds an authentication error from Rails have you looked in your app directory and what's in the log/production.log file to see what's causing the error?  Did you setup a username and password for redmine?  What does your /etc/apache2/sites-available/redmine file look like?  I'm really not a huge fan of this setup.  I like to get the newest version of ruby, gems, rails, and passenger phusion, so I can't be a huge help get this working from the repos.

---

### Post by rubylaser on 2011-06-30
I'll set this up in a VBox VM later, and see if I can't figure out what's going wrong for you.

---

### Post by gypsumwolf on 2011-07-01
> **rubylaser said:**
> This is sounds an authentication error from Rails have you looked in your app directory and what's in the log/production.log file to see what's causing the error?  Did you setup a username and password for redmine?  What does your /etc/apache2/sites-available/redmine file look like?  I'm really not a huge fan of this setup.  I like to get the newest version of ruby, gems, rails, and passenger phusion, so I can't be a huge help get this working from the repos.


I did not set up a user name or password.

Where is log/production.log?

sites-available/redmine:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName redmine.test
	ServerAlias *.redmine.test
	DocumentRoot /usr/share/redmine/public
	<Directory />
    PassengerResolveSymlinksInDocumentRoot on
    Options Indexes ExecCGI FollowSymLinks
	</Directory>
	<Directory /usr/share/redmine/public>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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

Do you recommend I start from scratch and use a different method for installation?

---

### Post by rubylaser on 2011-07-01
Your production log based on the document root you have in your Apache redmine file would be here...
```
tail -n 200 /usr/share/redmine/log/production.log
```^ that will give you the last 200 lines.

Does redmine.test resolve to this host from the box that you're trying to set it up on, or even your your /etc/hosts file on the local machine?  Otherwise, Apache isn't going to route the request to your Rails app.  Also, your redmine sites-available has WAY more in it than you need for Passenger Phusion to work. This will work for you too (with nothing else in it).

```

<VirtualHost *:80>
    ServerName redmine.test
    DocumentRoot /usr/share/redmine/public/
    PassengerResolveSymlinksInDocumentRoot on     
    Options Indexes ExecCGI FollowSymLinks
</VirtualHost>

```

Also, have you enabled the redmine file (does in show up in /etc/apache2/sites-enabled ?)

---

### Post by gypsumwolf on 2011-07-01
> **rubylaser said:**
> Your production log based on the document root you have in your Apache redmine file would be here...
```
tail -n 200 /usr/share/redmine/log/production.log
```^ that will give you the last 200 lines.

Does redmine.test resolve to this host from the box that you're trying to set it up on, or even your your /etc/hosts file on the local machine?  Otherwise, Apache isn't going to route the request to your Rails app.  Also, your redmine sites-available has WAY more in it than you need for Passenger Phusion to work. This will work for you too (with nothing else in it).

```

<VirtualHost *:80>
    ServerName redmine.test
    DocumentRoot /usr/share/redmine/public/
    PassengerResolveSymlinksInDocumentRoot on     
    Options Indexes ExecCGI FollowSymLinks
</VirtualHost>

```

Also, have you enabled the redmine file (does in show up in /etc/apache2/sites-enabled ?)

```

root@bluebox:~# tail -n 200 /usr/share/redmine/log/production.log
tail: cannot open `/usr/share/redmine/log/production.log' for reading: No such file or directory

```

redmine.test does not resolve, because I changed it. is now bluebox and it does resolve.

I updated according to your suggestions. Still have the error.

Yes, I do access the "bluebox" site for redmine. It shows a website displaying the error message.

---

### Post by gypsumwolf on 2011-07-01
> **rubylaser said:**
> Your production log based on the document root you have in your Apache redmine file would be here...
```
tail -n 200 /usr/share/redmine/log/production.log
```^ that will give you the last 200 lines.

Does redmine.test resolve to this host from the box that you're trying to set it up on, or even your your /etc/hosts file on the local machine?  Otherwise, Apache isn't going to route the request to your Rails app.  Also, your redmine sites-available has WAY more in it than you need for Passenger Phusion to work. This will work for you too (with nothing else in it).

```

<VirtualHost *:80>
    ServerName redmine.test
    DocumentRoot /usr/share/redmine/public/
    PassengerResolveSymlinksInDocumentRoot on     
    Options Indexes ExecCGI FollowSymLinks
</VirtualHost>

```

Also, have you enabled the redmine file (does in show up in /etc/apache2/sites-enabled ?)

```

root@bluebox:~# tail -n 200 /usr/share/redmine/log/production.log
tail: cannot open `/usr/share/redmine/log/production.log' for reading: No such file or directory

```

redmine.test does not resolve, because I changed it. is now bluebox and it does resolve.

I updated according to your suggestions. Still have the error.

Yes, I do access the "bluebox" site for redmine. It shows a website displaying the error message.

```

Ruby on Rails application could not be started
These are the possible causes:

    There may be a syntax error in the application's code. Please check for such errors and fix them.
    A required library may not installed. Please install all libraries that this application requires.
    The application may not be properly configured. Please check whether all configuration files are written correctly, fix any incorrect configurations, and restart this application.
    A service that the application relies on (such as the database server or the Ferret search engine server) may not have been started. Please start that service.

Further information about the error may have been written to the application's log file. Please check it in order to analyse the problem.

Error message:
    FATAL: password authentication failed for user "redmine" FATAL: password authentication failed for user "redmine" (PGError)
Exception class:
    PhusionPassenger::UnknownError
Application root:
    /usr/share/redmine 

```
it continues with a backtrace.

---

### Post by gypsumwolf on 2011-07-01
I did a fresh install of lubuntu 11.04.

I used these instructions: [http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_in_Ubuntu]("http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_in_Ubuntu")

It works!

---

