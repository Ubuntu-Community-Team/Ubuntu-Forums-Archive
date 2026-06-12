---
title: "Ubuntu Server?"
date: 2014-11-27
forum: Ubuntu, Linux and OS Chat
---

### Post by flaymond on 2014-11-27
Hey, I'm curious about Ubuntu Server. What is the purpose of Ubuntu Server? Does it give you free-server hosting? or what?

---

### Post by BlinkinCat on 2014-11-27
Hi,

Some general reading for a start - [https://help.ubuntu.com/14.04/serverguide/index.html](https://help.ubuntu.com/14.04/serverguide/index.html)

---

### Post by Elfy on 2014-11-27
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by mastablasta on 2014-11-27
Here is [What is server?]("http://en.wikipedia.org/wiki/Server_(computing)")

Ubutnu server comes preinstalled with applicaitons needed to run such a server.

---

### Post by ibjsb4 on 2014-11-27
I wouldn't call it preinstalled.  You do come to a screen that allows you to select configured packages.
[ATTACH=CONFIG]258236[/ATTACH]
From there I choose 'Manual package selection' since I use the server edition to install desktop environments and do not want server packages to be installed.

---

### Post by mastablasta on 2014-11-28
ok it has groups of packages. I forgot that. but you can setup let's say web server by selecting one group during install. or for example email server group and similar.

---

### Post by flaymond on 2014-11-28
Oh? Is it really? So, if you got Ubuntu Server, what you gonna do with it? Example? (If you willingly to give some :D)

---

### Post by coffeecat on 2014-11-28
> **InterProg said:**
> Oh? Is it really? So, if you got Ubuntu Server, what you gonna do with it? 

You run a server. Not really much more to be said.

> **InterProg said:**
> Example? (If you willingly to give some 

The servers that run this forum and all the ubuntu.com and Canonical owned sites, for starters. They'd hardly be running Windows server.

Wikipedia. A few years ago, the wikipedia people standardised on Ubuntu server for all their servers.

---

### Post by mastablasta on 2014-12-01
> **InterProg said:**
> Oh? Is it really? So, if you got Ubuntu Server, what you gonna do with it? Example? (If you willingly to give some :D)

let's see... not ubuntu bu ti think it has debian under it - OpenELEC is serving the media files.
then the file server is doing automatic backups of other computers in the net.

then it will be making virtual private network (when I have the time) and probably some virtual hosting of maybe games...

my host (I think centos) is hosting the website.

you can do other things - print serve, proxy server, gateway...

---

### Post by newbie-user on 2014-12-01
> **InterProg said:**
> Oh? Is it really? So, if you got Ubuntu Server, what you gonna do with it? Example? (If you willingly to give some :D)

Here's what I do with my Ubuntu servers:

[LIST]
[*]Ubuntu mirror
[*]Company websites
[*]User directory for computer and wifi logins
[*]File storage
[*]Virtual machine hosts
[*]Network routers
[*]Mail servers
[*]Internet gateways
[*]Proxy servers
[*]VPN servers
[/LIST]

---

### Post by coldraven on 2014-12-01
If you want to play around with an Ubuntu server on your own machine then do this:
Install VirtualBox 
You can then either download the Ubuntu Server iso and install it into VirtualBox or:           [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
Download a ready-made VB image of US and run it instantly:                                        [http://virtualboxes.org/images/](http://virtualboxes.org/images/)

Then you can login to the server, install the LAMP* package and fool around with HTML etc. (other options are available)
If you mess it up then you can roll back to a previous snapshot or just load the image and start again.
Keep a text file of all the changes you make to the server config files so that you do not repeat your mistakes. (too many times!) 

* [http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)

---

### Post by Hansiman on 2014-12-02
I think part of the question here is; what do YOU want to do with a server?

My Ubuntu Server currently runs a Minecraft world for me and my friends.

---

### Post by /ADM on 2014-12-02
Isn't the answer in the name?  Ubuntu 'SERVER'..  No you don't get free hosting, it's simply a minimal install with server packages at a command line to run and maintain a server for some website or application on the web.

If you don't know what it is for, probably best not to use it until you have gotten some knowlege.

---

