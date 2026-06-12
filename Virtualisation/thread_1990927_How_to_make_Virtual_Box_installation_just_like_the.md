---
title: "How to make Virtual Box installation just like the real thing"
date: 2012-05-30
forum: Virtualisation
---

### Post by yeehi on 2012-05-30
I use virtual box to try out new distros. It is very convenient, and I like the way it is set up. For instance, I use a bluetooth mouse on the operating system installed on my hard drive. During installation of a new Ubuntu OS on Virtual Box, my mouse works all the time, from the very beginning. Also, during the installation, my virtual OS is online from the moment of starting the installation. That is good.

The problem is, that is not the way things work when I install the OS in real life.

For example, my bluetooth mouse shouldn't work, because bluetooth won't have been set up and paired with my mouse.

Also, I should not be connected to the internet during installation either, as I have a USB key modem that I have to insert into the Laptop and then I need to (I believe, maybe it is possible to do something different in Linux) launch a small MS Windows program to dial up my ISP to get a wireless connection. As it is, after installation, it looks like my Virtual OS has a wired internet connection, instead of a wireless one.

What I want to know is how to set up Virtual Box so that the OS installs just as it would do if I were putting it  onto my real hard disk.

Thank you!

---

### Post by arubislander on 2012-05-30
When you're trying out a new distro in Virtual Box it will never be completely the same as installing it on real hardware (see my signature!) If you want a better feel as to how the distro will run with your hardware without installing it I'd create a liveUSB (with Startup Disk Creator, Unetbootin or MultiSystem), boot into a live session and try it out that way.

---

### Post by yeehi on 2012-05-30
Thank you arubislander.

I see what you are saying: for my purpose, i.e. testing whether my hardware is compatible with an OS, I shouldn't use VirtualBox. I should use a Live CD and boot into a live session.

I would then want to test if the updated versions of the packages worked OK on my system. I can't understand the following. You say don't do a system update in a live session. Wouldn't I, still in the Live session, do an update and check how everything ran. It that was OK, then I would know that I could use CD to do an installation on the hard disk.

What about later on, when I want to check how other packages or applications would run on my updated system? How would I check those things out? Is that when I would use VirtualBox?

Thank you for your help.

---

### Post by arubislander on 2012-05-31
OK, you really want a testing environment to see if you should apply updates and such to your production system. That is really wise, but more trouble than most people care to go through.

I just apply most regular updates. When a new release comes out of the OS then I have a spare partition I install it to and try it out on my hardware. I am assuming you could manage the same for your purposes. That is, reserve some space on your hard disk (around 8GB should be enough) and install or update whatever you want to test before applying it to your main system.

BTW: Performing updates in a live session tends to go wrong because eventually the system runs out of 'virtual' disk space.

---

### Post by yeehi on 2012-05-31
ahh! So that is the way you do it! You have two installations that you keep updated. One is your production system. The other one is the test one, that you update first, to see if things work. It is a good idea.

Thank you!

---

