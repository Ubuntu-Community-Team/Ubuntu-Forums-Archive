---
title: "[SOLVED] I Feel Rather Stupid"
date: 2008-11-24
forum: Server Platforms
---

### Post by brook adams on 2008-11-24
Six months ago I figured out how to set up a virtual host on my computer using apache2 on ubuntu 7.10. This past week I finally upgraded to 8.04 (I know I'm one upgrade behind the rest of the world).

I foolishly neglected to look one last time at my sites-available directory and now after rebuilding everything, I can't get virtual host to work.

The default file in sites-available works fine... 
That is, entering localhost in the browser gets me to /var/www

my other sites-available file (mysite) which is supposed to direct apache to a directory in my home folder doesn't have any effect. It is a copy of the default file with paths changed for DocumentRoot and log files.

Yes, I did 'a2ensite mysite' and reloaded...

I am hoping someone might have the time to look and see if I've made some kind of egregious error.

Here are the last three lines of my apache2.conf:

# Include the virtual host configurations:
ServerName floyd
NameVirtualHost *
Include /etc/apache2/sites-enabled/

here is the beginning of the mysite file:
(there is no .com because I'm just serving to myself)

<VirtualHost *>
	ServerName mysite
	ServerAlias www.mysite
	DocumentRoot /home/brook/mysite/web/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/brook/mysite/web/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from 192.168.
	</Directory>
etc....

---

### Post by Philio on 2008-11-24
Your config looks ok, try disabling the default site:

```
sudo a2dissite default
```

Then restart apache :)

---

### Post by brook adams on 2008-11-25
Thanks for the tip Philio,

Disabling default has some interesting results. Trying to reach localhost gives a permissions error which makes ense I guess. When I try to reach 'mysite', my browser looks out on the internet for the closest match... 
I imagine this means I have to tell apache to look only on the localhost.
Any idea how I do that?

---

### Post by Philio on 2008-11-25
Ah right, if your trying to add this on a local or intranet machine your going to need something that tells your browser that the site mysite is hosted on that particular machine.

If the hostname of the machine is mysite this might do the trick, I would assume Apache would see [http://mysite/](http://mysite/) and use the correct virtual host while any requests to [http://ip_address/](http://ip_address/) would go to the default site.

I can tell you a couple of other ways that you could achieve the same as this is a local/intranet machine which I know will work if this doesnt:

1. Use multiple ports:

- Edit /etc/apache2/ports.conf and add Listen 81, 82 etc for other ports to listen on.
- Setup virtual hosts by port e.g. NameVirtualHost *:80 / *:81 / etc and <VirtualHost *:80> etc.

2. Use multiple interfaces:

- Setup 1 or more virtual network interfaces by editing /etc/network/interfaces and adding eth0:0, eth0:1 etc interfaces with different IPs.
- Setup virtual hosts by IP.

---

### Post by brook adams on 2008-11-25
Hi Philio,

Thanks for the help... Dig this.

I tried disabling mysite virtual host block and replacing the DocumentRoot in default with the path to the mysite directory. Well, apache didn't like that very much so I opened up /etc/group and added www-data to my group.

Maybe that had no effect, I dunno... I read your post and adjusted the last lines of my apache.conf file to read like this:
ServerName 127.0.0.1
NameVirtualHost *
Include /etc/apache2/sites-enabled/

and now it works...

So thanks.

---

