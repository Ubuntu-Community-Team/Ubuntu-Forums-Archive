---
title: "Something similar to Sun SGD"
date: 2011-06-01
forum: Server Platforms
---

### Post by bgbfk8x on 2011-06-01
I am currently running Ubuntu Server 10.04. I'm looking for an application similar to Sun's SGD (Secure Global Desktop) in order to be able to run xwindow applications via a web interface. Any suggestions?
 
Thanx

---

### Post by scorp123 on 2011-09-27
> **bgbfk8x said:**
> I am currently running Ubuntu Server 10.04. I'm looking for an application similar to Sun's SGD (Secure Global Desktop) in order to be able to run xwindow applications via a web interface. Any suggestions?
 
Thanx You could try and convert the Oracle SGD *.rpm packages to *.deb. Not sure if this still works with the current 4.6.x.x release. I've done it successfully in the past with the 4.4x and 4.5x releases.

Or: you could run Webmin and install the VNC module? Works too ...

---

### Post by haqking on 2011-09-27
> **scorp123 said:**
> You could try and convert the Oracle SGD *.rpm packages to *.deb. Not sure if this still works with the current 4.6.x.x release. I've done it successfully in the past with the 4.4x and 4.5x releases.

Or: you could run Webmin and install the VNC module? Works too ...

Wasnt webmin support dropped in Ubuntu and debian ?

you can see here some workarounds [http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/](http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/)

[http://www.webmin.com/community.html](http://www.webmin.com/community.html)

---

### Post by scorp123 on 2011-09-27
> **haqking said:**
> Wasnt webmin support dropped in Ubuntu and debian ? That "workaround" looks horribly complicated. Why not use the *.deb package and let the package manager automagically handle the rest?? :D

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.560_all.deb
sudo dpkg -i webmin_1.560_all.deb
sudo apt-get -f install
wget http://www.webmin.com/webmin/download/modules/vnc.wbm
```

The "vnc.wbm" module needs to be installed from within Webmin's "Modules" configuration screen. Voila. Done.

Having a proper SGD package for Debian/Ubuntu would be waaaay cooler though. I'll try if I can convert the current 4.61-915 build (needs to be downloaded from within Oracle's software "eDelivery" portal). If yes, I'll post instructions ...

---

### Post by scorp123 on 2011-09-28
> **bgbfk8x said:**
>  I'm looking for an application similar to Sun's SGD (Secure Global Desktop) BTW, there in fact is an open source alternative: Ulteo.

Their home page:
[http://www.ulteo.com](http://www.ulteo.com)

They have a few screenshots here:
[http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/features](http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/features)

It is similar to Oracle SGD as so far that Ulteo also gives you a "Webtop" in which you can run pre-configured applications inside your web browser session. Just like SGD it also supports both Windows and Linux so far.

What doesn't seem to work are typical SGD features such as "Client Drive Mapping", "Printer Forwarding" and "Seamless Windowing" as far as I can tell (someone please correct me if I am wrong).


Another commercial possibility would be Teamviewer. Yes, it's commercial ... but you're allowed to use it for free for private purposes.

Their website:
[http://www.teamviewer.com](http://www.teamviewer.com)

I once wrote in a posting about them:
[http://ubuntuforums.org/showpost.php?p=9750486&postcount=2](http://ubuntuforums.org/showpost.php?p=9750486&postcount=2)

The advantage of Teamviewer is that you would not need to run your own server infrastructure. If you want to access your desktop via the web you can do that via their online portal. Works tip top.

---

### Post by scorp123 on 2011-09-30
> **bgbfk8x said:**
> I'm looking for an application similar to Sun's SGD (Secure Global Desktop) **_Update:_**

Converting **SGD 4.61** with *alien* works! (again ... it used to fail with the earlier 4.60 release for whatever reason ...)

You can get the **tta-4.61-915.i386.rpm** package from Oracle's eDelivery site and then convert it with ***"alien"*** into a *.deb package, e.g. **tta_4.61-915_i386.deb**. I did it and it works. Make sure you convert the package incl. the scripts too.

When you install SGD the various binaries might throw the same error message again and again (highly annoying ...!):

```
tr: warning: an unescaped backslash at end of string is not portable
```

Whatever that means ... SGD works. So even though above message gets printed out a lot you can safely ignore it.


```
dpkg -I tta_4.61-915_i386.deb

 new debian package, version 2.0.
 size 380064554 bytes: control archive= 416416 bytes.
     331 bytes,    11 lines   control              
 1363796 bytes, 13209 lines   md5sums              
 1324340 bytes, 14072 lines * postinst             #!/bin/bash
     132 bytes,     7 lines * postrm               #!/bin/sh
   33265 bytes,   731 lines * preinst              #!/bin/bash
     846 bytes,    21 lines * prerm                #!/bin/bash
     156 bytes,     9 lines   shlibs               
 Package: tta
 Version: 4.61-915
 Architecture: i386
 Maintainer: scorp123
 Installed-Size: 909032
 Section: admin
 Priority: optional
 Description: Oracle Secure Global Desktop for x86 Linux kernel 2.6+
  Oracle Secure Global Desktop for x86 Linux kernel 2.6+
  .
  (Converted from a rpm package by alien version 8.81.)
```

---

### Post by alexy4chat on 2012-01-01
Thanks, I install the same, its opening the but unable to login and the administrative console not opening. 

kindly tell the solution 

thanks,
s john

---

### Post by alexy4chat on 2012-01-15
Since I install it in (ubuntu 11.10, server edition), my administrative console is not working,
I check the **sgd** folder it has content its opening,
but sgdadmin folder is empty, also axis folder is empty
I cannot login 

Kindly help in this regard
Thanks


Thanks
S John

---

