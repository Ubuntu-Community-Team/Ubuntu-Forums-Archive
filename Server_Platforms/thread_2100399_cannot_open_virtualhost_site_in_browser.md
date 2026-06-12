---
title: "cannot open virtualhost site in browser"
date: 2013-01-01
forum: Server Platforms
---

### Post by raphievila on 2013-01-01
I'm following this thread and with most of your suggestions I have added a virtual host but when enter the ServerAlias to the browser it just doesn't works. I have added everything, I run the a2ensite successfully, also created all the folders to work with the site, plus the DocumentRoot to point to the folder in the /var/www directory, and I still get the error:

[HTML]The server at redinblackcafe.local can't be found, because the DNS lookup failed.[/HTML]

This is the file in the /etc/apache2/sites-available/redinblackcafe:

[PHP]
<VirtualHost *:80>
	ServerName  127.0.0.1
	ServerAdmin rvila@redinblackcafe.com
	ServerAlias redinblackcafe.local

	DocumentRoot /var/www/redinblackcafe.local
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/redinblackcafe.local>
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

	ErrorLog /var/www/redinblackcafe.local/err/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/www/redinblackcafe.local/log/access.log combined
</VirtualHost>
[/PHP]

Can anyone point out what I'm doing wrong?

---

### Post by volkswagner on 2013-01-01
You should have likely created a new thread.

The error is indicating a dns entry.  The serverAlias does not create a dns entry for you machine.  You need to tell your machine and any network machines where redinblackcafe.local is located (what ip address to translate to).

A quick and easy fix would be to add an entry in /etc/hosts for any machine you want to be able to access the site.


For your local machine adding:

```
127.0.0.1 redinblackcafe.local 
```

Should work.  For any other clients on the LAN you would need to enter the network ip address of you webserver.  You can find your servers local ip by running ifconfig.

```
ifconfig
```

---

### Post by raphievila on 2013-01-01
Thank you volkswagner, I added the line in the /etc/hosts and works like a charm.

And about to post a new question, you are right, I should open a new question and post your answer as the right answer. Thanks.

---

### Post by sandyd on 2013-01-01
**Banana Split** (Thread Split)

---

### Post by raphievila on 2013-01-03
> **sandyd said:**
> **Banana Split** (Thread Split)
Thank you Sandy... I didn't know how to split this...

---

