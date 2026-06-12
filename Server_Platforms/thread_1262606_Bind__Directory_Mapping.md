---
title: "Bind / Directory Mapping"
date: 2009-09-10
forum: Server Platforms
---

### Post by expatCM on 2009-09-10
On the server I have set up a number of directories under /var/www/ and want to access them directly from a client but only on the local network. 

So I have /var/www/joomlasite/ which is accessed without problem at [http://serverip/joomlasite/](http://serverip/joomlasite/)

What I want to do is simply type joomlasite and then get the site directory.

What I did to fix this was open up Bind with Webmin and create a master zone called joomlasite and then gave it an IP address.   When I enter joomlasite on a client I get a message “It Works” and not the pages in the joomlasite directory.

If I enter the IP I allocated in the browser address bar I get a time out.

I feel I am missing a step somewhere, something to point the IP address to the directory but I am not sure what that step should be.  Can somebody please tell me?

At some stage I may want to open access up and use dyndns for a fixed IP.  What changes to the setup will I need to make in order to expand  access at that time?

---

### Post by cariboo on 2009-09-10
A bump for the move.

---

### Post by expatCM on 2009-09-11
interesting this thread should be moved ....  I always thought the server forum was for people who know what they are doing and my question really is from an absolute beginner .... :)

---

### Post by terazen on 2009-09-11
I think you have 2 things to set up.  On your client pc you need to setup joomlasite to point to your server's ip address in /etc/hosts.  Then in the file /etc/apache2/sites-available/default, change where you see "/var/www" to "/var/www/joomlasite" and restart apache with: ```
sudo /etc/init.d/apache2 restart
```

After that you may have to configure joomla to the name "http://joomlasite" intead of "http://x.x.x.x/joomlasite".  I never set up joomla, but I would assume it's similar to drupal/moodle in this way.

---

### Post by expatCM on 2009-09-12
Thanks for your guidance.  The hosts file is easy but the apache2 file is a bit more of a challenge.

You say "in the file /etc/apache2/sites-available/default, change where you see "/var/www" to "/var/www/joomlasite"".  

Now this is where I get confused.  This is my default file.

```
<VirtualHost *:80>

DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
<Directory /var/www//>
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

It covers port 80.  There is another similar file for port 443.

I think what you want me to do is to change 

<Directory /var/www//>
to 
<Directory /var/www/joomlasite/>

BUT should I be doing this and not copying the section, making a new section for each different directory under /var/www/ and leave the original alone ?

Sorry to be so basic but learning about servers is not exactly like falling off a log ....

---

### Post by terazen on 2009-09-14
If you want to are running multiple virtual servers then yes, just copy the default file for the new site.```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/newsite

```

Then you would edit the newsite file, enable it in apache, and restart apache:```
sudo nano /etc/apache2/sites-available/newsite
sudo a2ensite newsite
sudo /etc/init.d/apache2 restart
```

I just assumed you only had the 1 site with my previous post, in which case editing the default file is a little quicker.  Also, if you have a seperate file for https/443 then you'd want to edit both files for the new path.

---

### Post by expatCM on 2009-09-15
Thank you for your suggestions.  I will look at this in a day or two and let you know ....

---

### Post by expatCM on 2009-11-24
Summary = this is about multiple virtual servers.

Well I simply cannot figure this out.   I think it is either due to the fact that I have torrentflux or squid installed but I really do not know how to play in order to get what I want.  Deleting the existing virtual server took out squid and that took time to resolve .........

So I have decided that next week I will set the server up again.  Fresh install of 9.10.  What could go wrong ....   well many things I guess....  which is why I have refreshed this thread.

I am going to follow this guide
[http://linuxgazette.net/141/lazar.html](http://linuxgazette.net/141/lazar.html)
A few minor changes will be needed since it is a little dated but not really too much.

I think it will be a happy life until the bit about installing Torrentflux. That is easy enough but I want to do it in a manner so that I can also run Joomla which is why I opened this thread in the first place.  It is clear that I will need to change a few things.  The guide suggests Address = Any for the Apache virtual server.  Would that remain the same?   and the path Path = /home/public, should that not be more specific and point to the TF directory?

I really want to avoid a mess and so any suggestions or articles to read would be appreciated.

Yes, I know about the Howtoforge article on setting up a server but it does not reflect my need.

---

