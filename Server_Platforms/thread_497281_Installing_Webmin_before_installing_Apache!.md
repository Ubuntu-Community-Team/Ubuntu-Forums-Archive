---
title: "Installing Webmin before installing Apache!"
date: 2007-07-10
forum: Server Platforms
---

### Post by titanevn on 2007-07-10
hi Ubuntu men,

I install Webmin on Ubuntu 7.10 (beta) by following these steps:

[B]# wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.350_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.350_all.deb)

# dpkg --install webmin_1.350_all.deb

# apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
[/B]
The process seem to be completed successfully but when I tried to connect to [http://ubuntu710:10000](http://ubuntu710:10000) it doesn't work; :confused:

I also try with IP Address and receive the error report:

"Firefox can't establish a connection to the server"

After that, I install Apache2 and It 's still do NOT work.

how do I solve the problem???

sorry for my poor English.:mad:

---

### Post by titanevn on 2007-07-10
I've solved the problem;

First, I Update Ubuntu with:

**apt-get update**
and
**apt-get upgrade**

and then, try to find open port with

**netstat -tap**

I found out that no Process listen on webmin port; :(

the last command is:
**/etc/webmin start**

hope my post can help other people facing the same problem :)

---

### Post by hebetude on 2008-01-20
weak sauce, the package should have started it on its own.  Their debian packager isn't very good, I had to do a fix because it broke dependencies with my ubuntu packaged version.

---

