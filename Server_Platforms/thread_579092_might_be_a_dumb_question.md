---
title: "might be a dumb question"
date: 2007-10-17
forum: Server Platforms
---

### Post by linux-loser on 2007-10-17
this might be a really dumb question but im very new to linux, just installed first time 3 days ago.  so please bare with me.

im running fiesty 7.04 x64 desktop.  is if possible for me to install server options?

and will i be able to use my gnome gui and control the server options?

if so, to what extent... like will i be able to host my own domain, and email?  that sounds really crazy as i have used windows all my life and have never dreamed of such things.

---

### Post by bodhi.zazen on 2007-10-18
yes you can do all this and more ... 

Start here : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

I advise you install Firestarter ...

OK, now on to the good stuff :

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

That should be enough reading for one night :twisted:

---

### Post by Soarer on 2007-10-18
> **linux-loser said:**
> this might be a really dumb question but im very new to linux, just installed first time 3 days ago.  so please bare with me.

im running fiesty 7.04 x64 desktop.  is if possible for me to install server options?

and will i be able to use my gnome gui and control the server options?

if so, to what extent... like will i be able to host my own domain, and email?  that sounds really crazy as i have used windows all my life and have never dreamed of such things.

As bodhi.zazen says.

If you are going to use it mainly as a server, then install the server version first and then ubuntu-desktop for the Gnome GUI afterwards.

Most of the server options can be managed with webmin ([www.webmin.com](www.webmin.com)) even on a server without GUI.

But, if you just want to try running web sites and email servers, than use what you already have. It will work fine, but you will need to install apache web server etc.

---

### Post by linux-loser on 2007-10-18
so i am looking at formatting and installing the server OS instead of the desktop OS?  or is there way that i can install some server capabilities to run a web site and email on top of the OS i already have?  

though, i dont want to come off as lazy im willing to do it all over again, just my roomate has all of her pictures on here already and as she is a photographer she might be mad if she was to lose all that.

---

### Post by linux-loser on 2007-10-18
so i am looking at formatting and installing the server OS instead of the desktop OS?  or is there way that i can install some server capabilities to run a web site and email on top of the OS i already have?  

though, i dont want to come off as lazy im willing to do it all over again, just my roomate has all of her pictures on here already and as she is a photographer she might be mad if she was to lose all that.

ahh crap sorry double post.

---

### Post by Soarer on 2007-10-18
No need - you can install what you need on top of the desktop.

The perfect setup ([http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)) link is a good one to follow, but you may not need all of the software. If you aren't going to be running a database-driven site, for example, you won't need MySql. Probably you won't need an FTP server as you are already working on the box you are using.

You will definitely need Apache though - start there & build up.

---

