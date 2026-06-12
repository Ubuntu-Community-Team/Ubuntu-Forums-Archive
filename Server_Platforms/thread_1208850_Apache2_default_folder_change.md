---
title: "Apache2 default folder change"
date: 2009-07-09
forum: Server Platforms
---

### Post by spongypants23 on 2009-07-09
I've attempted to change the default Apache2 DocumentRoot folder from /var/www to ~/web.

However now whenever I navigate to [http://localhost](http://localhost) I get a FORBIDDEN error, even though permissions are rwxr-xr-x

How do I fix that?

---

### Post by joebeasley on 2009-07-09
Use the full path, /home/web.  Make sure the user running apache has read access to it.

---

### Post by spongypants23 on 2009-07-09
Right. I've changed it to absolute paths.

Here is the current content of:


/etc/apache2/sites-enabled/000-default
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/simon/web
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/simon/web/>
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

Though I'm not sure which user it is that runs apache? The /home/simon/web folder is set to 755, or rwxr-xr-x, so every user should have read access?

---

### Post by JohnLau on 2009-07-10
):P /home/web is different from ~/web, I think you have to take notice of this.
John

---

### Post by spongypants23 on 2009-07-10
> **JohnLau said:**
> ):P /home/web is different from ~/web, I think you have to take notice of this.
John

So it's impossible to have Apache use a folder in my own home directory?

---

### Post by credobyte on 2009-07-10
Why not to use mod_userdir ( [http://httpd.apache.org/docs/1.3/mod/mod_userdir.html](http://httpd.apache.org/docs/1.3/mod/mod_userdir.html) ) instead of changing default configuration ?

---

### Post by JohnLau on 2009-07-10
> **spongypants23 said:**
> So it's impossible to have Apache use a folder in my own home directory?
Yes it is possible. I meant to tell you that joebeasley made a little mistake... ~/web is /home/username/web, but not /home/web ;)

> **joebeasley said:**
> Use the full path, /home/web.  Make sure the user running apache has read access to it.

---

### Post by JohnLau on 2009-07-10
> **credobyte said:**
> Why not to use mod_userdir ( [http://httpd.apache.org/docs/1.3/mod/mod_userdir.html](http://httpd.apache.org/docs/1.3/mod/mod_userdir.html) ) instead of changing default configuration ?

Can write a little guide about this 8-[ It seems a bit hard to understand .....


Have you tried changing the owner of the directory?
```
sudo chown www-data ~/web -R
```

John

---

### Post by wojox on 2009-07-10
So take your /web directory and put it inside /simon directory.

---

### Post by philtrim on 2009-07-10
Try it after removing the trailing backslash  ".../web[COLOR="Red"]/[/COLOR]" the path in the directive.

---

### Post by bear24rw on 2009-07-10
is the folder owned by the apache user? or is the folder viewable by the group the apache user is in, you can try changin apache to run as you i dont remember what file its in but one of the config files tells apache what user to run as and by default it is its own user

---

### Post by spongypants23 on 2009-07-10
> **JohnLau said:**
> Can write a little guide about this 8-[ It seems a bit hard to understand .....


Have you tried changing the owner of the directory?
```
sudo chown www-data ~/web -R
```

John
Did that, no change. Still a Forbidden error.

> **wojox said:**
> So take your /web directory and put it inside /simon directory.
That's where it is. The path is /home/simon/web


> **philtrim said:**
> Try it after removing the trailing backslash  ".../web[COLOR="Red"]/[/COLOR]" the path in the directive.
Nope.. No change.

---

### Post by JohnLau on 2009-07-10
> **spongypants23 said:**
> Did that, no change. Still a Forbidden error.


That's where it is. The path is /home/simon/web



Nope.. No change.

I think there is an ultimate way... try it at your own risk :lolflag:
You can try changing the user that apache is running from www-data to your own account.
You can do this by opening
```
/etc/apache2/httpd.conf
```
for edit
and paste the following lines onto it
```
<IfModule !mpm_netware_module>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User ###PUT_YOUR_USERNAME_HERE###
Group ###PUT_YOUR_GROUPNAME_HERE###
</IfModule>
```

Please tell me if this works :D

John

---

### Post by spongypants23 on 2009-07-10
> **JohnLau said:**
> I think there is an ultimate way... try it at your own risk :lolflag:
You can try changing the user that apache is running from www-data to your own account.
You can do this by opening
```
/etc/apache2/httpd.conf
```
for edit
and paste the following lines onto it
```
<IfModule !mpm_netware_module>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User ###PUT_YOUR_USERNAME_HERE###
Group ###PUT_YOUR_GROUPNAME_HERE###
</IfModule>
```

Please tell me if this works :D

John

**It works!!!**

Here, have a cookie.

---

### Post by itsyashhere on 2012-09-08
> **JohnLau said:**
> I think there is an ultimate way... try it at your own risk :lolflag:
You can try changing the user that apache is running from www-data to your own account.
You can do this by opening
```
/etc/apache2/httpd.conf
```for edit
and paste the following lines onto it
```
<IfModule !mpm_netware_module>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User ###PUT_YOUR_USERNAME_HERE###
Group ###PUT_YOUR_GROUPNAME_HERE###
</IfModule>
```Please tell me if this works :D

John

IT works man !!!!
thanks a lot :D :D

---

