---
title: "Web Server"
date: 2009-11-06
forum: Server Platforms
---

### Post by lupeatx on 2009-11-06
So I've decided to work on a little project at home. I'm wanting to set up a web server at home and host at least 2 web sites. What would be my first steps to get this party started? My system right now is running on Win XP. I know Ubuntu has a server edition but after downloading and installing what's next?:popcorn:

---

### Post by BQAggie2006 on 2009-11-06
You need to start by installing Apache and possibly the entire LAMP (Linux Apache MySQL PHP) stack:

Official Server Guide - [https://help.ubuntu.com/9.10/serverguide/C/web-servers.html](https://help.ubuntu.com/9.10/serverguide/C/web-servers.html)
Community Contributed Documentation - [https://help.ubuntu.com/community/Servers#Web%20servers](https://help.ubuntu.com/community/Servers#Web%20servers)

---

### Post by gordintoronto on 2009-11-06
If you want to dual-boot, your first step is to make a partition into which you can install Ubuntu.

You might find it easier to install regular Ubuntu rather than the server version -- which has no GUI.  Apache will run just fine under Ubuntu desktop.

Does your ISP provide a static IP address?  Most do not, so that means you need to set up something such as no-ip to deal with IP address changes.

---

### Post by PadawanGeek on 2009-11-06
I found this tutorial to be very helpful and informative: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

---

### Post by SGAZ on 2009-11-06
In addition to dealing with changing IP addresses you should be aware that many ISPs do not allow servers to be hosted on their residential services so there is a chance that incoming traffic on port 80, among others, will be blocked by your ISP.  

You may want to be aware of that while configuring Apache (and your router) so you can make any necessary adjustments.  If you are only serving things up for your home network then it won't matter.

Good luck!

---

### Post by linux_lover69 on 2009-11-06
I found this tutorial to work very well. I used it to set up my crudely crapy looking website.

[http://www.gauntface.co.uk/blog/2009/10/15/karmic-koala-web-development-set-up-guide/]("http://www.gauntface.co.uk/blog/2009/10/15/karmic-koala-web-development-set-up-guide/")

---

### Post by GCoffee on 2009-11-06
Also, if you are used to a nice GUI with little buttons and menus, you may want to try:

sudo apt-get install gnome

or:

sudo apt-get install xfce4

XFCE4 is definately lighter, with gnome being the more common (I think..)

I have heard setting up a GUI on a server can be a security risk?

---

### Post by lupeatx on 2010-01-19
So everything has been updated. 

Now will be going to set a domain name. After that I do I start hosting it?

---

