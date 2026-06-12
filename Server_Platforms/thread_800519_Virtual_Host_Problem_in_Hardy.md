---
title: "Virtual Host Problem in Hardy"
date: 2008-05-19
forum: Server Platforms
---

### Post by madhusudancs on 2008-05-19
I am trying to run multiple websites from different locations on my Hardy machine. I did the same procedure I used to use on Feisty and Gutsy. I have even logged this procedure in my blog [http://madhusudancs.info/virtualserver-setup]("http://madhusudancs.info/virtualserver-setup"). But it doesnot work. 

When I give the address in the browser it says 

```
Forbidden

You don't have permission to access / on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch mod_vhost_hash_alias/1.0 Server at mywiki Port 80
```

This is the procedure I followed, I copied two files from default and named them drupal6 and mediawiki

one of these files looked like this

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName drupal6

	DocumentRoot /home/madhu/mywebdevelopment/drupal6.0/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/madhu/mywebdevelopment/drupal6.0/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

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

and I do this in the terminal
```

sudo a2ensite drupal6
sudo a2ensite mediawiki
sudo /etc/init.d/apache2 restart
```

to the Hosts list I add these details

IP address: 127.0.0.2  Alias: drupal6
IP address: 127.0.0.3  Alias: mywiki

and when I type [http://drupal6](http://drupal6) or [http://mywiki](http://mywiki) in the browser I get the above mentioned error. Please help me

Thanks in advance

---

### Post by windependence on 2008-05-20
Didn't you have another thread on this?

-Tim

---

### Post by madhusudancs on 2008-05-20
Hey thanks for the reply. I dont think I personally have posted a thread on this. If so please link me to that. I still say no to it. The previous post I did was on Bridge Mode settings and I am sad that I haven't got any help on that. If there is a thread on the same issue posted by somebody else please link me.

---

### Post by windependence on 2008-05-20
Let me see if I can find it for you.

-Tim

---

### Post by bennybobw on 2008-05-21
That was my thread, and I still haven't resolved it.
It's here:
[http://ubuntuforums.org/showthread.php?t=797903]("http://ubuntuforums.org/showthread.php?t=797903")

Can you check your error log and post the results over there?

---

### Post by spiderbatdad on 2008-05-21
the above error looks like the result of an .htaccess file with no corresponding .htpasswd file.
Also, possibly edit /etc/hosts to point to your local ip:
<ip> domain.com

---

### Post by bennybobw on 2008-05-22
Check your permissions on mywebdevelopment too...[ that's what screwed me up]("http://ubuntuforums.org/showthread.php?t=797903&page=2").

---

### Post by madhusudancs on 2008-05-25
> **spiderbatdad said:**
> the above error looks like the result of an .htaccess file with no corresponding .htpasswd file.
Also, I have never needed to edit the hosts file for apache use. Instead I specify ServerName localhost in httpd.conf

/etc/hosts contains 127.0.0.1 localhost

Is this what you are try to accomplish?
[http://spiderbatdad.podzone.org](http://spiderbatdad.podzone.org)

I can also make it so the host html page wont display without authorization.

I dont think this is the problem. I never used .htaccess files either in feisty or in gutsy. How this problem arises only in hardy? There is something wrong somewhere else.

---

### Post by madhusudancs on 2008-05-25
> **bennybobw said:**
> Check your permissions on mywebdevelopment too...[ that's what screwed me up]("http://ubuntuforums.org/showthread.php?t=797903&page=2").

Permission is 777 recursively on that direcroty. I had seen your post before posting this.

---

