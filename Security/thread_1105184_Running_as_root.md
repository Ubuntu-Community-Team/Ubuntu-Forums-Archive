---
title: "Running as root?"
date: 2009-03-24
forum: Security
---

### Post by Rumbl3 on 2009-03-24
I'm still very new to ubuntu. I see things here and there about running programs as root is not a good idea.

Now i'm a admin on my machine so when i start up a program is that running it as root? I don't get it really so i'm just curious what it is and what do u do then to change that.

---

### Post by Simian Man on 2009-03-24
Running programs as root is often needed for administrative tasks.  Running all your programs as root just because you can is not a good idea though.

---

### Post by Dr Small on 2009-03-24
Please read this sticky:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by bodhi.zazen on 2009-03-24
Running as root is probably not a great idea, but some people do and that is their choice.

The main problem with running as root is it makes it easier to crack into your system. Every modern OS, including windows, separates user space from administration, and Linux is no different. Did you ever ask yourself why there is an administrative account on Windows ? Same reasoning should apply to any OS ;)

The other problem is more educational. All too often I see new users running as root to circumvent learning system administration. People simply use gksu nautilus or sudo chown this or sudo chmod that without teaching or learning the basics such as permissions.

When you do that, run as root rather then learn the basics, you are very likely to break your installation. And when such breakage occurs, people come to these forms looking for assistance. 

So far better, IMO, to teach teach basic system admin rather then basic data recovery ;)

Please see things such as :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

---

