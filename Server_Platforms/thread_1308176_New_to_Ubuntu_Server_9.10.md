---
title: "New to Ubuntu Server 9.10"
date: 2009-10-31
forum: Server Platforms
---

### Post by Jms10391 on 2009-10-31
Hello Everyone,
 
I've been programming web sites for about two years now and I've decided to get me my own server.  I chose an Ubuntu sever because people told me it was the best for the price of $0.00.  I'm wonder what steps I have to take to set up the server and what I need to do to get my site up and running, such as where do my files go, how to set up mysql, and how to post it on the web.
 
Thanks,
Jms10391

---

### Post by dvlchd3 on 2009-10-31
First of all, I'd suggest using Ubuntu Server 8.04.  This is the long-term support version.  It is supported until 2013.  Typically this is the way you want to go when using a server.  It is just annoying to have to upgrade your system every 6 months...

Good place to start on how to setup your server is here:
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

And here:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by Jms10391 on 2009-10-31
So I installed the server operating system..... And I'm not sure if I set it up right because I went with default values.  I still have no idea how to access where I upload my files for my site or even how to set up my domain name, any help????

---

### Post by ikt on 2009-10-31
> **Jms10391 said:**
> So I installed the server operating system..... And I'm not sure if I set it up right because I went with default values.  I still have no idea how to access where I upload my files for my site or even how to set up my domain name, any help????

There are plenty of guides on the web :)

[http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu)

for example,

as for specifically where to upload your files, if you installed apache the default location is,

/var/www

setting up your domain name usually requires installing and configuring bind.

There should be a guide on that to.

---

### Post by X1R1 on 2009-10-31
maybe you feel overwhelmed by the fact that you have no GUI and have to type all commands and know the paths in which you want your files to go.

Try webmin, its a pretty cool app that will give you a web-based frontend to do all of your configuration needs :D

Website is here [http://www.webmin.com/]("http://www.webmin.com/")

Also, after you install it, there a tutorial on exactly what you need on this page: [http://doxfer.com/Webmin/Tutorials]("http://doxfer.com/Webmin/Tutorials")

Check out the apache section :D

hope it helped

---

### Post by phillw on 2009-10-31
> **Jms10391 said:**
> Hello Everyone,
 
I've been programming web sites for about two years now and I've decided to get me my own server.  I chose an Ubuntu sever because people told me it was the best for the price of $0.00.  I'm wonder what steps I have to take to set up the server and what I need to do to get my site up and running, such as where do my files go, how to set up mysql, and how to post it on the web.
 
Thanks,
Jms10391


security of your server is massively important

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

That's where the server forum lives ... read the stickies

Phill.

---

### Post by Oropher8598 on 2009-10-31
The [official Ubuntu Server documentation](https://help.ubuntu.com/9.04/serverguide/C/index.html) may be the best place to start... it's not been updated to 9.10 yet, but most things won't have changed.

I also found [this article](http://nanotux.com/blog/the-ultimate-server/) useful when I was learning Ubuntu Server - it uses Lighttpd instead of the more common Apache, but the rest of the guide is very thorough and easy to follow.

---

### Post by phillw on 2009-10-31
adding mod-security  is an ermmmm interesting thing - highly recommended to your apache2 server ... just make sure it doesn't ban you !!!

It does take a bit of thinking of

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

There is a profile for apache2 for apparmor

If you are setting your server to have the outside world contact it, please check the stickies, if you just want a 'local' server ..... please read the stickies !!!

Phill.

---

### Post by ikt on 2009-10-31
If you wish to have a gui you can still use apache/bind etc with ubuntu desktop.

---

### Post by Spiritof76 on 2009-10-31
Assuming one has ubuntu desktop and server on the same lan, is it possible to use gui tools on the desktop to administer the server?

---

### Post by ikt on 2009-11-01
> **Spiritof76 said:**
> Assuming one has ubuntu desktop and server on the same lan, is it possible to use gui tools on the desktop to administer the server?

That depends, it's basically up to the program, I'm not aware of any programs that allow for remote administration using a gui besides those which are installed on the web server, ie ssh, webmin etc.

Would be interested if anyone knows any.

A windows-esk way of doing things would be to install ubuntu desktop on the ubuntu server and use VNC to admin things via the servers gui.

---

### Post by Jms10391 on 2009-11-01
> **X1R1 said:**
> maybe you feel overwhelmed by the fact that you have no GUI and have to type all commands and know the paths in which you want your files to go.
 
Try webmin, its a pretty cool app that will give you a web-based frontend to do all of your configuration needs :D
 
Website is here [http://www.webmin.com/](http://www.webmin.com/)
 
Also, after you install it, there a tutorial on exactly what you need on this page: [http://doxfer.com/Webmin/Tutorials](http://doxfer.com/Webmin/Tutorials)
 
Check out the apache section :D
 
hope it helped
 
YES!  I have done numerous projects on Microsoft Windows Server 2003, and I work with the GUI it has.  It was easy for me to just upload to the live sites on those servers, but when I installed Ubuntu I became extremely confused

---

### Post by dvlchd3 on 2009-11-03
> **Jms10391 said:**
> YES!  I have done numerous projects on Microsoft Windows Server 2003, and I work with the GUI it has.  It was easy for me to just upload to the live sites on those servers, but when I installed Ubuntu I became extremely confused

Learning anything new takes time.  READ THE DOCUMENTATION!

Although you're going to end up using the command-line for most server administrator stuff, you can install the gui by typing:

```

sudo apt-get install ubuntu-desktop

```

---

