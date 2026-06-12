---
title: "Failed to start apache : no listening sockets available, shutting down"
date: 2010-03-17
forum: Server Platforms
---

### Post by webbdawg on 2010-03-17
Here is the error I am getting

Failed to start apache :

* Starting web server apache2
[Wed Mar 10 19:31:24 2010] [warn] NameVirtualHost *:0 has no VirtualHosts
no listening sockets available, shutting down
Unable to open logs
...fail!


I know there are not virtual hosts because I have not created one. But what does no sockets available mean??


Is there a way to return apache to it's default settings. I may have changed something and I have no Idea what.

Thanks

---

### Post by KB1JWQ on 2010-03-17
If I recall correctly, something else is listening on the port that Apache is trying to listen on.  netstat -pant, look for the same port that your Listen directive is set to in httpd.conf.  From there, you can figure out what's bound there.

---

### Post by webbdawg on 2010-03-18
> **KB1JWQ said:**
> If I recall correctly, something else is listening on the port that Apache is trying to listen on.  netstat -pant, look for the same port that your Listen directive is set to in httpd.conf.  From there, you can figure out what's bound there.

There is absolutely nothing in my httpd.conf file. Which seems odd.

I know it cannot be that hard to get things running............so why is it turning in to an excessive in frustration. No matter what I try Apache will not start and I keep getting  the listening error.

---

### Post by jrssystemsnet on 2010-03-18
> **webbdawg said:**
> Is there a way to return apache to it's default settings. I may have changed something and I have no Idea what.That sounds highly likely.

**WARNING WARNING WARNING** the below code snippet will remove Apache2, ALL repeat ALL configurations you may have created, and ALL repeat ALL data you may have placed in the location for the default site.  Back up /etc/apache2 and /var/www before running this code if you think there is **anything** in there you may need later.

```
you@box:~$ sudo apt-get purge apache2
you@box:~$ sudo rm -rf /etc/apache2
you@box:~$ sudo rm -rf /var/www/*
you@box:~$ sudo tasksel remove lamp-server
you@box:~$ sudo tasksel install lamp-server
```

Now you should be able to start Apache, and browsing to it should get the default "**It Works!**" page.

Note: I edited this to use tasksel instead of just installing Apache2 by itself, because although it installs a good bit more than "just Apache", it sounds like you're more interested in getting to "something that works" rather than "exactly what I asked for and nothing more." :)

---

### Post by webbdawg on 2010-03-18
It all worked except I get the error

**tasksel: aptitude failed (100)**

when trying to run the last sudo tasksel install lamp-server

---

### Post by jrssystemsnet on 2010-03-18
> **webbdawg said:**
> It all worked except I get the error

**tasksel: aptitude failed (100)**

when trying to run the last sudo tasksel install lamp-server

```
you@box:~$ sudo dpkg --configure -a
you@box:~$ sudo apt-get update
you@box:~$ sudo apt-get upgrade
you@box:~$ sudo tasksel install lamp-server
```

If it still won't work, try **sudo dpkg --configure -a** AGAIN after the apt-get update and apt-get upgrade, then report back here.

---

### Post by webbdawg on 2010-03-18
I finally got apache2 to appear. I had to manually create the file /etc/apache2/apache2.config

Then I re ran all the suggested commands.

I tried to get apache started but still get the error:

Failed to start apache :

 * Starting web server apache2
no listening sockets available, shutting down
Unable to open logs
   ...fail!

At this point I am ready to just wipe the drive and start over, which seems to be a bit drastic.

Jeez, I know I'm not an idiot but this seems to be pretty odd.

---

### Post by KB1JWQ on 2010-03-18
You need a valid httpd.conf (or other configuration file) with the proper command strings included.  Not sure why you don't have this.

---

### Post by jrssystemsnet on 2010-03-18
Try **sudo tasksel remove lamp-server && sudo tasksel install lamp-server**, see if you get the standard config files then.

---

