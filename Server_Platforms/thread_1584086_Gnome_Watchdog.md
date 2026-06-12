---
title: "Gnome Watchdog"
date: 2010-09-28
forum: Server Platforms
---

### Post by keiffee30 on 2010-09-28
I have found this documentation 

[https://help.ubuntu.com/community/UbuntuLTSP/GnomeWatchdog](https://help.ubuntu.com/community/UbuntuLTSP/GnomeWatchdog)

but it stats that its for 8.04LTS would this still be the same for 10.04LTS?

---

### Post by arrrghhh on 2010-09-28
Hrm, you should try and see if it fails for any reason.  A lot of the documentation was written for one version, but other versions work - sometimes with no modifications, sometimes with some tweaking.

Check it out, let us know how it works :D

---

### Post by keiffee30 on 2010-09-28
ok i will give it a go to see. is / would there be any log files i should have a look in or jus tthe out put of the screen do.

---

### Post by keiffee30 on 2010-09-28
i have been looking in the /etc/init.d/..... and found watchdog in there. so i tried a

sudo /etc/init.d/watchdog restart

and its working. so it looks like 10.04 install it by default. all you have to do is to make sure that this is in the startup so it auto runs on boot. you can also make sure that it runs by typing in that command. 

I should learn to trust in myself and 'do it'. i just think that i have been around the other os too dam long to just do it.
many thanks

---

### Post by arrrghhh on 2010-09-28
No worries, never hurts to ask.  FYI, there's a new upstart system in 10.04.  Instead of init.d, you should use ```
sudo service watchdog restart
``` - or start, stop, etc.  Some services will outright not work if you try to use init.d!

Also, use the thread tools drop down menu and mark this thread [SOLVED] if you feel it has been :D

---

