---
title: "Difference between Server and Desktop versions"
date: 2006-07-27
forum: Server Platforms
---

### Post by steve_waters on 2006-07-27
Hello

Just a quick question therefore a quick answer will suffice.

What are the major differences between the Server and Desktop additions, especially if I install Ubuntu Desktop on the server addtion?

If there is another thread or wiki or web page on this please point to it rather reapet information, save you guys some time to help people with real problems.

Many thanks
Steve

---

### Post by apjone on 2006-07-27
major differance is the lack of a gui (graphical user interface), the server installs text only, no gnome or kde. thus is a lot smaller and quicker. The 6.06 server also comes with no ports open by default !! SECURE !!.

AJ

---

### Post by az on 2006-07-27
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

You can install ubuntu-desktop on a server.  The desktop packages do not conflict with the server packages.  You may want to install the desktop kernel, too, though.  Install the linux-386 package.

The server is just a base system, so the desktop already has that.  If you want the LAMP stack, you can also install apache2 php5-mysql libapache2-mod-php5 mysql-server.

---

### Post by lamego on 2006-07-27
The desktop also comes with "NO PORTS OPEN" as default.
The major diference is the "server" kernel version which gets installed by default and provides better support and optimization for server services.

---

### Post by steve_waters on 2006-07-28
Ok

So we have no GUI and optimised kernel and no gui. 

So if I install the gui, I will retain the optimised kernel and thus it is still a more server based system than the desktop version. 

That is a very good feature the no ports open on the desktop as well.

Thanks for the answers guys:KS :KS

---

### Post by az on 2006-07-28
> **steve_waters said:**
> So if I install the gui, I will retain the optimised kernel and thus it is still a more server based system than the desktop version. 

Yes, but you may run into snags with some hardware.  For example, some have wondered why their funky twenty-seven-button optical mouse doesn't work.

> **steve_waters said:**
> 
That is a very good feature the no ports open on the desktop as well.


"No ports open" only means that there is nothing listening by default.  If you install SSH or apache, you will then have something listening on those ports for example.

So the "no ports open" only refers to the default packages set up in the desktop.  It is probably against security best-practices to install a GUI on a server that will be on the internet.

---

### Post by llbbl on 2006-07-28
Having a windows manager, like Gnome, is nice sometimes because you some distros like Fedora include GUI's to make the editing of conf files easier or whatever. I like the httpd conf editor in Fedora for instance. 

What I don't like about Ubuntu is it installs apache conf file into different files like:

/etc/apache2/sites-available/
/etc/apache2/mods-available/

I would rather it all be in one big file. 

I also do not like the fact that apache start page returns an directory listing with a folder [http://localhost/apache2-default/](http://localhost/apache2-default/). By default if the /var/www/html folder is emtpy it should default to ubuntu customized apache default page.

---

### Post by joshchernoff on 2006-07-28
> **llbbl said:**
> 
I also do not like the fact that apache start page returns an directory listing with a folder [http://localhost/apache2-default/](http://localhost/apache2-default/). By default if the /var/www/html folder is emtpy it should default to ubuntu customized apache default page.

why is it that they do that?

---

### Post by llbbl on 2006-07-28
> **joshchernoff said:**
> why is it that they do that?

I dunno I guess they have been worrying about more important things. This seems like a minor detail that could have very well slipped by. 

Also Ubuntu default web folder is /var/www not /var/www/html like I am used too, which is fine, just different. I changed the apache config and created a folder called html since I liked it this way. :)

With Fedora there is a bunch of crap in www that you dont want the public to see, but with Ubuntu it is empty. One reason I liked having a html folder because I could have a /var/www/include folder outside the root web server path for most important info like database connections.

---

### Post by az on 2006-07-28
> **llbbl said:**
> 
What I don't like about Ubuntu is it installs apache conf file into different files like:

/etc/apache2/sites-available/
/etc/apache2/mods-available/

I would rather it all be in one big file. 

The point of apache2 was to eliminate the monolythic configuration file.  You have apache control tools to enable site and modules.

> **llbbl said:**
> 
I also do not like the fact that apache start page returns an directory listing with a folder [http://localhost/apache2-default/](http://localhost/apache2-default/). By default if the /var/www/html folder is emtpy it should default to ubuntu customized apache default page.

You just have to edit the redirect match to the subdirectory of your choice in /var/www.  Your going to remove the default page anyway.  The way it is set up, you don't have a lot of junk in your root folder.

---

