---
title: "Request or help: xchat-gnome 0.6"
date: 2005-11-18
forum: Ubuntu Backports
---

### Post by Confuse on 2005-11-18
Can anyone tell me how to backport xchat-gnome 0.6 to breezy? its in the dapper repos. I get the following error when I try.

***Entering source tree...
***Editing changelog...
***Resolving build dependencies...
Reading package lists... Done
Building dependency tree... Done
E: Must specify at least one package to check builddeps for
I couldn't resolve build dependencies by myself. I'll drop you to a shell
damian@pompey:~/ubp-compile-temp/xchat-gnome-0.6$

---

### Post by m_gasior on 2005-11-19
Hi,

For me everything is OK. You need 3 files:
1. [http://archive.ubuntu.com/ubuntu/pool/universe/x/xchat-gnome/xchat-gnome_0.6-0ubuntu2.dsc](http://archive.ubuntu.com/ubuntu/pool/universe/x/xchat-gnome/xchat-gnome_0.6-0ubuntu2.dsc)
2. [http://archive.ubuntu.com/ubuntu/pool/universe/x/xchat-gnome/xchat-gnome_0.6.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/universe/x/xchat-gnome/xchat-gnome_0.6.orig.tar.gz)
3. [http://archive.ubuntu.com/ubuntu/pool/universe/x/xchat-gnome/xchat-gnome_0.6-0ubuntu2.diff.gz](http://archive.ubuntu.com/ubuntu/pool/universe/x/xchat-gnome/xchat-gnome_0.6-0ubuntu2.diff.gz)

Then
1. dpkg-source -x chat-gnome_0.6-0ubuntu2.dsc
2. cd xchat-gnome-0.6/ 
3. dpkg-buildpackage -rfakeroot

Probably you will have to install some dev packages.

---

### Post by Confuse on 2005-11-19
Thank you so much!!!! It worked! Is this how I should approach other packages I want to backport too? Thanks again I really appreciate it!

---

### Post by m_gasior on 2005-11-19
This is simple way and you can try it with most packages, but sometimes it isn't so easy. :smile:

---

### Post by m_gasior on 2005-11-21
Here is new xchat-gnome 0.7 deb.

[http://www.paczki-ubuntu.cba.pl/upload/xchat-gnome_0.7-1_i386.deb](http://www.paczki-ubuntu.cba.pl/upload/xchat-gnome_0.7-1_i386.deb)

---

### Post by akurashy on 2005-11-21
my bad but what xchat-gnome does?

---

### Post by Confuse on 2005-11-21
Ooooooooo, thank you! =]

xchat-gnome is basically a frontend to xchat that makes it more HIG friendly. Its really nice, but still a bit incomplete.

---

### Post by m_gasior on 2005-12-21
New xchat-gnome 0.8 is out. 
Changes: translation support (including full fr and en_GB translations) and a new userlist pop-up. 
My packages for Breezy:

[http://ubuntu.host.sk/upload/xchat-gnome_0.8-1_i386.deb](http://ubuntu.host.sk/upload/xchat-gnome_0.8-1_i386.deb)

or 

[http://www.paczki-ubuntu.cba.pl/upload/xchat-gnome_0.8-1_i386.deb](http://www.paczki-ubuntu.cba.pl/upload/xchat-gnome_0.8-1_i386.deb)

---

### Post by Confuse on 2005-12-21
[QUOTE=m_gasior]New xchat-gnome 0.8 is out. 
Changes: translation support (including full fr and en_GB translations) and a new userlist pop-up. 
My packages for Breezy:

[http://ubuntu.host.sk/upload/xchat-gnome_0.8-1_i386.deb](http://ubuntu.host.sk/upload/xchat-gnome_0.8-1_i386.deb)

or 

[http://www.paczki-ubuntu.cba.pl/upload/xchat-gnome_0.8-1_i386.deb](http://www.paczki-ubuntu.cba.pl/upload/xchat-gnome_0.8-1_i386.deb)[/QUOTE]

Is it compiled against libsexy and ssl? Thats why I've been trying to compile my own, some of them omit important features.

---

### Post by m_gasior on 2005-12-22
Libsexy and ssl are not supported. But if you need libsexy you can try to recompile dapper version. There is only one problem. Before building package you have to edit control file from debian directory. Find:

libdbus-glib-1-dev (>= 0.60)

and change to

libdbus-glib-1-dev (>= 0.36).

---

### Post by Confuse on 2005-12-22
[QUOTE=m_gasior]Libsexy and ssl are not supported. But if you need libsexy you can try to recompile dapper version. There is only one problem. Before building package you have to edit control file from debian directory. Find:

libdbus-glib-1-dev (>= 0.60)

and change to

libdbus-glib-1-dev (>= 0.36).[/QUOTE]

Thanks, thats what I was having problems with. I "backported" libsexy to breezy and am linking it to xchat-gnome, but this problem had me stompted.

---

### Post by Confuse on 2005-12-22
I just upgraded to .8 and man I don't like it. There is just too much dead space below the networks and channels, at least before you had some useful room viewing the people in the channel. Ugh, might have to revert back.

---

