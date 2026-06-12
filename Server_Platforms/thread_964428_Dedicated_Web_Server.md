---
title: "Dedicated Web Server"
date: 2008-10-30
forum: Server Platforms
---

### Post by daboroe on 2008-10-30
I am utilizing Ubuntu Server 8.0.4 LTS on a VMware image. I would like to test it out and what not. I have the ability from the host OS to connect to the website that is hosted on Ubuntu that is running on the VMWare Image. Very easy. Currently I am utilizing LAMP. I do not want to do that anymore. I want to convert LAMP to something I could really utilize in the real world as a dedicated server. The one place that I could work for in May has their websites running on a Mac OS 10.5, I believe, server. I would like to change this for them because of Linux being better in my opinion. 

How can I set up Ubuntu to have a dedicated web server. I have a link but I am not sure if this is just the manual way to set up LAMP or not. Please let me know. <http://www.linuxforums.org/servers/setting_up_a_server.html>

Your help is much appreciated and love Ubuntu Desktp 8.1!

Mike

---

### Post by alienprdkt on 2008-10-30
follow this:) 
[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

---

### Post by ad_267 on 2008-10-30
> Currently I am utilizing LAMP. I do not want to do that anymore. I want to convert LAMP to something I could really utilize in the real world as a dedicated server.

I'm not quite sure what you mean there. Real world web servers do just use LAMP (Linux, Apache, MySQL and PHP/Python/Perl). That link you posted explains how to set these all up. You say you have a LAMP installation already though, how is that any different to what you want?

---

### Post by cariboo on 2008-10-31
I would like to know what the Mac server can't do that you can do with Ubuntu. After all OS X is based on BSD. You know what they say if it ain't broke don't fix it.

Jim

---

### Post by daboroe on 2008-10-31
@cariboo907: I know what they say. We are having major problems with Joomla and the Mac Server and what not. Currently I do not have the time to learn how things are set up since I already have hte knowledge of having a server in place with that. 

@ ad_267: People say like WAMP, LAMP, XAMPP should not be used for a real world website. What I mean by this you should set up everything manually I know that is really just setting up the LAMP stuff manually as well

Thanks for your help

---

### Post by lykwydchykyn on 2008-10-31
You are confusing several things. 
 - LAMP is a generic term for Linux, Apache, MySQL, and PHP/Python/Perl.  It most definitely is used for real world websites, including some of the biggest ones out there.  Whether you set it up manually or through some sort of virtual package, it's still the same software.
 - XAMPP is a prepackaged LAMP setup that makes it easy for beginners to set up the LAMP environment without having to install a lot of discrete packages or configure everything.  I wouldn't personally recommend it for a "real world" server, just because I prefer to have the components integrated into the package management of the system.
 - WAMP is LAMP running on Windows, not Linux.  I guess people do this, though I don't know why.

I think where you are getting confused is that XAMPP is probably not recommended by a lot of pros for running on real websites.  Not the same thing as LAMP.  

I suggest you take the time to have a very thorough understanding of this before you go in and replace the existing servers on the basis of some vague notion of Linux being better.  Otherwise you're likely to come out looking very foolish.

---

### Post by alienprdkt on 2008-10-31
> **lykwydchykyn said:**
> 
I suggest you take the time to have a very thorough understanding of this before you go in and replace the existing servers on the basis of some vague notion of Linux being better.  Otherwise you're likely to come out looking very foolish.

very true,
I have apache, mysql, php, python runnig great on mac osX as well as on 2 Ubuntu machines, (I have it set up this way for testing enviroment puposes, plus its backed up if I happen to crash a LAMP) all run just as well and perform rather nicely together. :D

---

