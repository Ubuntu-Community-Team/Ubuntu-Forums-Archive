---
title: "What is difference between Ubuntu Gnome release and one with flashback?"
date: 2014-04-12
forum: Ubuntu Development Version
---

### Post by cwmoser on 2014-04-12
What is the difference between the Trusty Ubuntu Gnome distro release versus
the regular release when you install **gnome-session-flashback**?????

Carl

---

### Post by ibjsb4 on 2014-04-12
In a nutshell:

Ubuntu Gnome Flashback is built on Gnome Shell and Mutter


Gnome Flashback that is built on the ubuntu release using either compiz or metacity.

---

### Post by cwmoser on 2014-04-12
Thanks.  Is there a benefit with **Mutter** vs **Compiz** vs **Metacity** ???

Lot of new technology going on under the hood of Trusty.
I am running 12.04 with Gnome and Compiz.

Carl

---

### Post by ibjsb4 on 2014-04-12
Mutter, never used it.

Compiz, all that eye candy :)

Metacity and fallback is what I run.  Because I just want the basic stuff.

---

### Post by kansasnoob on 2014-04-12
> **ibjsb4 said:**
> In a nutshell:

Ubuntu Gnome Flashback is built on Gnome Shell and Mutter


Gnome Flashback that is built on the ubuntu release using either compiz or metacity.

That's wrong :(

The flashback session is not even installed in Ubuntu GNOME, by default it boots to the GNOME Shell DE but the new GNOME Classic session can be chosen from the login screen.

The flashback session can be installed in either Ubuntu or Ubuntu GNOME. Please see:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

---

### Post by buzzingrobot on 2014-04-12
Ubuntu Gnome used the current Gnome Shell environment.

The "flashback" is an emulation of the old Gnome 2 environmment.

---

### Post by ibjsb4 on 2014-04-12
> **kansasnoob said:**
> That's wrong :(

The flashback session is not even installed in Ubuntu GNOME, by default it boots to the GNOME Shell DE but the new GNOME Classic session can be chosen from the login screen.

The flashback session can be installed in either Ubuntu or Ubuntu GNOME. Please see:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

Must be missing something, it sounds to me that we are basically saying the same thing.  You end up on one of three wm.  Depends on which burn you start with.  Wish it would not of become so confusing.

---

### Post by grahammechanical on 2014-04-12
It is true that I have not tried gnome-session-flashback on Ubuntu Gnome recently. But when I did try it a few weeks ago I found that it was broken. Rightly or wrongly, I have concluded that when running Ubuntu+Unity we may install gnome-session-flashback. And when running Ubuntu Gnome we may install Gnome Classic, which is a Gnome 3 Shell extension. But not the other way around. I would not advise it.

Of course, there is nothing stopping us from installing gnome-session-flashback on Ubuntu Gnome. Or installing Gnome Classic in Ubuntu+Unity. I would not do it. But then again, I think that if a person wants Xfce on Ubuntu, then install Xubuntu. And if we want KDE on Ubuntu then install Kubuntu and likewise with Lubuntu to get LXDE.

It seems more natural to me. Less likely to experience issues.

Regards.

---

### Post by ibjsb4 on 2014-04-12
> Of course, there is nothing stopping us from installing gnome-session-flashback on Ubuntu Gnome. Or installing Gnome Classic in Ubuntu+Unity. I would not do it. But then again, I think that if a person wants Xfce on Ubuntu, then install Xubuntu. And if we want KDE on Ubuntu then install Kubuntu and likewise with Lubuntu to get LXDE.

Yes, there are options +1 to that.

---

### Post by cwmoser on 2014-04-12
Thanks for the comments.  

I'm still confused whether I want to go with Trusty Gnome distro or Trusty Unity with Gnome Flashback.

I'm not even sure which Gnome version I have with my 12.04.  
Like to discern what to go with before April 17.

Carl

---

### Post by monkeybrain20122 on 2014-04-12
I have installed flashback on Unity to test remote desktop but it is apparently broken in 13.10 for that purpose. So ended up installing lxde with a wall paper and theme to look like flashback instead (not sure if it is still broken in 14.04, haven't checked)

---

