---
title: "php on apache and IIs"
date: 2009-04-02
forum: Server Platforms
---

### Post by glenngds2007 on 2009-04-02
I have a couple of different web servers set up in my home one is a windows IIs web server and the other is an Ubuntu Apache2 web server both are running 64 bit OS's.  I downloaded some updates for the Ubuntu last night and I did not check the php web scripting part of the Ubuntu web server I did a few minutes ago and all php scripts on the server has died and what happens is that when a non-server computer connects to the Ubuntu web server it literally tries to download the script instead of executing.  I know for a fact that it worked a few days ago.

The windows webserver I tried to install php 4 IIs and it does not serve up the files at all either. I probably just fowled up the install here because I have yet to see it correctly do anything with php on IIs

I really need some help here, any ideas??

---

### Post by nquinnathome1 on 2009-04-03
See the answers in [this ]("http://ubuntuforums.org/showthread.php?t=995039")thread; sounds like your Apache installation has lost or disabled the PHP Module

---

### Post by tubezninja on 2009-04-04
Regarding the IIS installation: the available php4 binaries are 32-bit, and will not run on IIS in 64-bit mode.  You need to configure IIS to run in 32-bit mode to get php4 to work.

Here's an article I've run into that discusses this:

[http://www.iisadmin.co.uk/?p=14](http://www.iisadmin.co.uk/?p=14)

Couple of suggestions:

1. You probably already know this, but PHP4 is at End of Life and has been for over a year now.  You should really consider upgrading to PHP 5.2 or later if you can.

2. As someone who used to run PHP (and even Apache) on a Windows server, I would say that you really might want to look into just migrating that Windows/IIS server to a LAMP, unless you have a specific app on it that requires IIS (and the case for migrating to a suitable linux app is not compelling or nonexistent). Getting PHP and Windows to behave, particularly when security updates were necessary, always seemed to be problematic.  Saying goodbye to the ease of the Windows interface was very much worth the reduced headaches it when I did the switch.

---

