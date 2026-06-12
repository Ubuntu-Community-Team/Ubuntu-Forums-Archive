---
title: "Ubuntu Alias Redirect Behavior"
date: 2010-10-19
forum: Server Platforms
---

### Post by Scottix on 2010-10-19
Hi I am trying to setup an Apache Environment with a Django development platform, and a redmine project management deal.

I want my Django project on the root url:
[http://ip.address/](http://ip.address/)

I want my redmine software /redmine:
[http://ip.address/redmine](http://ip.address/redmine)

Here is my config file:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/ame
	<Directory />
		Options None
		AllowOverride None
		Order Deny,Allow
		Deny from all
	</Directory>

	<Directory /var/www/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride none
		Order allow,deny
		allow from all
	</Directory>

	<Directory /var/www/ame>
		Options -Indexes +ExecCGI +FollowSymLinks +MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

Alias /redmine "/var/www/redmine"
	<Directory /var/www/redmine>
		PassengerAppRoot /usr/share/redmine
		RailsBaseURI /redmine
		Order deny,allow
		Allow from 10.10.0
		Deny from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

</VirtualHost>
```

So my problem is had it working, but I wanted /var/www/ame to be the root. With this change I added the Alias, but it doesn't seem to be doing what I want. When I try to access redmine I get this error in the log.

```
terminate called after throwing an instance of 'Passenger::FileSystemException'
  what():  Cannot resolve possible symlink '/var/www/ame/redmine': No such file or directory (2)
```

I would like to have both on the same platform and I am open to other ideas.

Update: This appears to be a problem with how Passenger works, stated in [Issue 30]("http://code.google.com/p/phusion-passenger/issues/detail?id=30") I guess I could find another way to do this.

---

### Post by brianjolly on 2010-10-19
I haven't used Redmine, but in a typical rails/passenger setup you need to create a symlink to the public folder of the rails application.

[http://www.modrails.com/documentation/Users%20guide%20Apache.html#deploying_rails_to_sub_uri](http://www.modrails.com/documentation/Users%20guide%20Apache.html#deploying_rails_to_sub_uri)

---

### Post by L0neRanger on 2010-10-30
brianjolly's true. I've spent over three days and countless hours trying to get my redmine, which is under /var/www/redmine to work under its proper sub-URI.

But finally had to settle for the symbolic link method as none of the others work perfectly.

Will post complete configuration and method shortly.

---

