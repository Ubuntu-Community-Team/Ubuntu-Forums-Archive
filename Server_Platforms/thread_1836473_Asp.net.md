---
title: "Asp.net"
date: 2011-08-31
forum: Server Platforms
---

### Post by Drenriza on 2011-08-31
What is the best way to install mono 2.4 on 10.04LTS ubuntu server edition?
I want to do this to be able to run a ASP.NET website with apache2.

I found this guide, but is this suited for server edition?
[http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx](http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx)

Kind regards.

---

### Post by Drenriza on 2011-08-31
bump a little bit.

---

### Post by directhex on 2011-08-31
> **Drenriza said:**
> What is the best way to install mono 2.4 on 10.04LTS ubuntu server edition?
I want to do this to be able to run a ASP.NET website with apache2.

I found this guide, but is this suited for server edition?
[http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx](http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx)

Kind regards.

Ubuntu 10.04 shipped with Mono 2.4, so all you need to do is install the requisite packages? Install mono-xsp and run "xsp" in your app folder to check it works, then when confident, install libapache-mod-mono

use the mono-server2-admin/mono-server2-update commands to generate the config stubs you need.

---

### Post by Drenriza on 2011-09-01
> **directhex said:**
> Ubuntu 10.04 shipped with Mono 2.4, so all you need to do is install the requisite packages? Install mono-xsp and run "xsp" in your app folder to check it works, then when confident, install libapache-mod-mono

use the mono-server2-admin/mono-server2-update commands to generate the config stubs you need.

What do you mean with
"use the mono-server2-admin/mono-server2-update commands to generate the config stubs you need."
What is a stub? :p

---

### Post by Drenriza on 2011-09-02
> mono-server2-admin.conf is a perl tool to adminstrate your ASP.NET webapps that will be executed with mod_mono.

When you try to add an application, admin.conf will verify that your path exists, if it is, it will
add a directory inside /etc/xsp/conf.d with the name of your app, and also as a file with the
filename format: 10_appname. This file will have the information (path, app).

So, when mono-xsp-update.conf is executed it will read those dirs and create a debian.webapp in
/etc/xsp that the xsp daemon will read, also with a mono-server2-hosts.conf that will have your
directory settings with apache directives. Apache will read mono-server2-hosts.conf!

> mono-server2-update is a perl tool to update/create a .webapp and a .host file in
/etc/mono-server2.

These two files are needed by mod_mono (apache), they setup the alias, directory permissions,
and ASP.NET applications.

Both files are created with other host configuration files that are in /etc/mono-server2/conf.d

 For more information read the README.Debian of this package (/usr/share/doc/mono-server2/README.Debian).

Well needless to say i don't get it. I simply don't get it. No where does it say how to get to this point. Do i just need to run the two commands and then thats that? Or does i need to run these commands in conjunction with my C# ASP.NET program/website????? And so some linux hokus pokus.

EDIT.
Also what is the default version?
mono-xsp - simple web server to run ASP.NET applications - default version

---

### Post by Drenriza on 2011-09-02
Also as far as i can see mono-xsp or mono-xsp2 does not run the ASP.NET runtime 4.
How can i install the ASP.NET 4 runtime on linux?

---

### Post by directhex on 2011-09-02
> **Drenriza said:**
> Also as far as i can see mono-xsp or mono-xsp2 does not run the ASP.NET runtime 4.
How can i install the ASP.NET 4 runtime on linux?

Upgrade to Ubuntu 11.10.

---

### Post by Drenriza on 2011-09-03
> **directhex said:**
> Upgrade to Ubuntu 11.10.

Will this then automatically use runtime 4 for ASP.NET?
As far as i can see, by default mono is not installed in any shape on the server edition.

---

### Post by directhex on 2011-09-04
> **Drenriza said:**
> Will this then automatically use runtime 4 for ASP.NET?

That's the default configuration, yes.

mono-xsp pulls in mono-xsp4 by default on 11.10, and mono-xsp2 on older versions. mono-xsp4 and associated packages are not available on 11.04 or older, only 11.10.

> As far as i can see, by default mono is not installed in any shape on the server edition.

Not by default, no. Server installs are extremely minimal.

---

### Post by jayster1973 on 2011-10-16
I guess I'm experiencing a unique problem, but I can't seem to get past it.  I have all the LAMP components installed and it works fine, but when I try to add mono to serve asp.net pages, it locks up near the end of the installation and becomes a zombie.  The zombie description is as follows:

root      1246  0.0  0.0      0     0 pts/0    Z+   11:48   0:00 [mono-apache-ser] <defunct>

I'm running Ubuntu Server 10.04 LTS inside VirtualBox.  I also have a low-end box I installed this on, too, and experience exactly same problem.  When I install mono-xsp2 and serve up a page on port 8080 it works fine, but when I try to install mono-apache-server2 it can't finish the installation.  This is really annoying, please help. 

What is also odd, I have installed mono before in the past over a year ago, but never had problems like this.

---

### Post by Drenriza on 2011-10-17
> **jayster1973 said:**
> I guess I'm experiencing a unique problem, but I can't seem to get past it.  I have all the LAMP components installed and it works fine, but when I try to add mono to serve asp.net pages, it locks up near the end of the installation and becomes a zombie.  The zombie description is as follows:

root      1246  0.0  0.0      0     0 pts/0    Z+   11:48   0:00 [mono-apache-ser] <defunct>

I'm running Ubuntu Server 10.04 LTS inside VirtualBox.  I also have a low-end box I installed this on, too, and experience exactly same problem.  When I install mono-xsp2 and serve up a page on port 8080 it works fine, but when I try to install mono-apache-server2 it can't finish the installation.  This is really annoying, please help. 

What is also odd, I have installed mono before in the past over a year ago, but never had problems like this.

Are you going to use mono for the .NET framework 4.0, or what version are you going to use?

---

### Post by cj1982 on 2012-01-30
Exactly the same problem. At end of installation mono-apache-serv becomes <defunct>

Anyone knows what's the problem?

Maybe apache-mpm-worker o apache-mpm-prefork? I have installed the second one.

Thanks

---

