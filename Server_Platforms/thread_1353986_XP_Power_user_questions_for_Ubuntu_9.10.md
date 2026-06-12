---
title: "XP Power user questions for Ubuntu 9.10"
date: 2009-12-13
forum: Server Platforms
---

### Post by JAB Creations on 2009-12-13
I'm an XP power user and I've seriously considering switching to Linux for a couple of years now. Before I switch my main OS from XP to Ubuntu I need to have control of the OS.

First and foremost how do I manage what background applications and "services" are starting up with Ubuntu automatically? I presume it's a completely different ballpark.

I've removed Ubuntu's default copy of Apache and replaced it with my own...how can I get my own copy of Apache to start automatically with Ubuntu?

I'm not running a Commodore 64 so how do I disable the swap file? If I run out of 4GB I want an error message letting me know versus my system slowing down over time. Most people seem content to allow junk that shouldn't be in the memory stagnate or migrate to the hard drive as copies of existing files...all a massive waste of resources; so I'm looking for an answer not a debate.

Ubuntu isn't treating Ctrl+[arrow/home/end/pageup/pagedown] to skip through words in textareas like XP does, how do I get this useful behavior to work?

How do I get the scrollwheel to work in Ubuntu?

What file manager closely mimics the usefulness of Windows Explorer in Windows XP? Windows Explorer in Vista/7 sucks hard and the default file manager in Ubuntu isn't customizable, is bulky, and has no tree structure for folders.

How can I get the Windows flag key to work with Ubuntu's application menu?

I've found most other things by exploring or on search engines though those are the things I haven't figured out yet.

---

### Post by JAB Creations on 2009-12-13
I figured out how to get XAMPP to start/stop...

> sudo /opt/lampp/lampp -start

So what/how/where should I do to make this happen when Ubuntu starts?

---

### Post by Cheesemill on 2009-12-13
> **JAB Creations said:**
> What file manager closely mimics the usefulness of Windows Explorer in Windows XP? Windows Explorer in Vista/7 sucks hard and the default file manager in Ubuntu isn't customizable, is bulky, and has no tree structure for folders.


Nautilus (the file browser) does have a tree view, just click on the Places button and switch it to tree.

---

### Post by craigp84 on 2009-12-13
What would you gain from switching? Are you sure it's worth it?

1) Background system processes are told to start by having symlinks in /etc/rcX.d to scripts in /etc/init.d. See [http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit) for the gory details, but more often than not, the preferred method is to identify whatever service you wish to disable, then move it's /etc/rc2.d/S76serviceName to /etc/rc2.d/K76serviceName.

2) Install the ubuntu apache package (you can have the package installed at the same time as your own, i'm assuming you installed your version to /usr/local (the default) so they wont clash. Take a look at how the ubuntu supplied version hangs together, specifically the /etc/init.d/apache2 script. If you're wanting to run it as an unpriveleged user (it wont be able to listen on ports <1024) you can just start it from the user's crontab, have a google for the @reboot timing specifier in (vixie) cron.

3) As root, "swapoff -a" will disable all swap files / partitions immediately. Comment out the swap line in /etc/fstab to stop it being used again at the next reboot. Have a google for what the /proc/sys/vm/swappiness interface allows you to do if you ever want a more pragmatic approach.

4) Haven't a clue unfortunately.

5) You configure it in /etc/X11/xorg.conf but to be honest i'd be dumbfounded if ubuntu didn't pick up your mouse and just make it work. If scrolls not working i'd take a guess at it being something in the desktop mucking you about. "sudo dpkg-reconfigure xserver-xorg" will let you double check the /etc/X11/xorg.conf settings without having to learn X11 config file language.

6) I don't know, but it definitely has tree structure views, it's been in GNOME for years, i used to use it all the time.

7) One of configuration dialogues, think it's called Keyboard, it's just off the Settings -> prefs menu or whatever it's called i can't remember (the settings menu that sits up next to the applications menu -- it's in there somewhere, have a root around you'll find it) It's labelled the "super" key.

8) Yeah there's a ton of help out there.

---

### Post by BkkBonanza on 2009-12-13
To disable swap file,

swapoff -a
(read more details, man swapoff or man swapon)

I've always left it alone because it rarely ever gets touched even on my 2GB system. But you could reclaim the disk space.

On Linux any unused RAM is automatically used as disk cache to speed file access anyway.

On Linux background services are called daemons. Some can be controlled in the GUI on the menu System, Preferences, Startup Applications. Others are more typically managed at the command line. Links placed to files in the /etc/init.d directory control when daemons start at boot. 

I believe the LAMP installer will config relevant apps to auto start at boot by default. But if you wanted to check them out then look in /etc/init.d. There would be symbolic links for each runlevel in /etc/rc?.d (? being runlevel) that point to the init script in /etc/init.d.

My mouse wheel always worked. Not sure how to fix that.

---

### Post by noelvh on 2009-12-13
My fist thought is your are an XP power user, but Ubuntu or Linux is not XP. If you bring your XP thoughts over to Linux you will drop it fast.
> I'm not running a Commodore 64 so how do I disable the swap file? If I run out of 4GB I want an error message letting me know versus my system slowing down over time. Most people seem content to allow junk that shouldn't be in the memory stagnate or migrate to the hard drive as copies of existing files...all a massive waste of resources; so I'm looking for an answer not a debate.

Why would you run out of 4gb of ram? I have 2gb of ram and have never come close, and I am a power user of both XP Ubuntu. Oh and this is more of a windows issue than a *nix issue. And I must say a bit nasty way of asking for help would you not say.

Noel

---

### Post by BkkBonanza on 2009-12-14
I don't recall the Commodore 64 having a swap file. :)

---

