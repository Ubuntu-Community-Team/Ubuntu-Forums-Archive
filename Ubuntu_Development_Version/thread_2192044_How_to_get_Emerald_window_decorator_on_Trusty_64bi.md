---
title: "How to get Emerald window decorator on Trusty 64bit"
date: 2013-12-05
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-12-05
If you're like me and like Emerald windows decorator and can't live with out it here's how to get it. ;)

Just enter these commands. It works well. I tried it with **emerald --replace &** in terminal and it worked instantly. 

I'm not sure if adding Emerald caused gtk-window-decorator to break or if it was going to break any way but, after I added it to CCSM gtk-window-decorator was no longer in the equation.

Then I added it to CCSM as shown replacing **/usr/bin/gtk-window-decorator** with **/usr/bin/emerald** rebooted and it works well.

[ATTACH=CONFIG]248374[/ATTACH]

```
sudo apt-get install git autoconf libtool libwnck1.0-cil-dev libwnck-dev intltool libdecoration0-dev gawk compizconfig-settings-manager

wget cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.5.tar.gz

tar -zxvf emerald-0.9.5.tar.gz && cd emerald-0.9.5/

./autogen.sh
make clean
make distclean
./configure --prefix=/usr --libdir=/usr/lib${LIBDIRSUFFIX} LIBS='-ldl -lm'
make
sudo make install
```

Afterwards:

[[IMG]http://en.zimagez.com/miniature/emeraldscreenshot2013-12-05.png[/IMG]]("http://en.zimagez.com/zimage/emeraldscreenshot2013-12-05.php")

Here is the page I got the commands from [_here_]("http://askubuntu.com/questions/287056/how-to-compile-install-emerald-window-manager-in-ubuntu-13-04-64bit").

It says it is for Raring Ringtale 13.04 64 bit but it works fine on Trusty Tahr 14.04 64 bit.

---

### Post by Chanath on 2013-12-06
Would it work with TT Gnome edition?

---

### Post by Cavsfan on 2013-12-06
> **Chanath said:**
> Would it work with TT Gnome edition?

Not sure. I am in Gnome Flashback.

I just made sure all of the files to be installed were in the repositories and seen they were and went for it. 

It's working great here.

---

### Post by Cavsfan on 2014-03-11
Re-installing emerald in Trusty.
This site seems to be a better place to get emerald-0.9.5.tar.gz

[http://cgit.compiz.org/fusion/decorators/emerald](http://cgit.compiz.org/fusion/decorators/emerald)

That wget command no longer works. Or it would not work for me.

---

### Post by fattyz on 2014-04-14
Thanks this worked for me in gnome-fallback.

---

### Post by Cavsfan on 2014-04-15
> **fattyz said:**
> Thanks this worked for me in gnome-fallback.

You're welcome! Don't you mean gnome flashback (with compiz) though as gnome fallback is just a transitional package. 

I couldn't live without Emerald! I'm glad this does work on Trusty. :)

---

### Post by fattyz on 2014-04-15
Yes, I was not being careful as I read during my endless searching and multiple upgrades that the terms were considered almost interchangeable, (in the opinion of the developer I was reading) flashback being a continuation of fallback.  God knows I can't keep 'em straight.  You are correct though, my session is called flashback w/compiz.  [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback).  All that about flashback, fallback and gnome can be so confusing when you first start sorting through the Ubuntu desktop, especially if you don't want to run Unity IMO.

Thanks again.

---

### Post by Cavsfan on 2014-04-16
> **fattyz said:**
> Yes, I was not being careful as I read during my endless searching and multiple upgrades that the terms were considered almost interchangeable, (in the opinion of the developer I was reading) flashback being a continuation of fallback.  God knows I can't keep 'em straight.  You are correct though, my session is called flashback w/compiz.  [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback).  All that about flashback, fallback and gnome can be so confusing when you first start sorting through the Ubuntu desktop, especially if you don't want to run Unity IMO.

Thanks again.

I know what you mean about confusing. Everything has changed. I pretty much live in Gnome Flashback (with Compiz) with Emerald window decorator if I can find it.
On one install I installed Emerald from another site than the one above and it did not work, borked my system and I had to reinstall Ubuntu. 
Then I re-installed Ubuntu and went back to this thread I had started and everything went perfectly.

You're welcome! Glad this works on Trusty as well as it does. :)

---

### Post by akha666-f on 2014-05-07
Thanks for this post
but I can't got it wrorking with Unity decorations plugins 
is there any help

---

### Post by cariboo on 2014-05-07
> **akha666-f said:**
> Thanks for this post
but I can't got it wrorking with Unity decorations plugins 
is there any help

Trusty has been released, so you won't get any help here, as we are now discussing and solving Utopic (14.10) problems. I's suggest you as your question in [Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329")

Thread Closed.

---

