---
title: "Please help, weird boot issue"
date: 2008-03-18
forum: Server Platforms
---

### Post by Myen on 2008-03-18
I am running 6.06 server and am having a weird issue, today I rebooted it and somehow the MBR got messed up, which I was able to fix, but now it's not booting right.

It will make it to the login prompt, but alot of things arent loading now, including my network adapter. It looks like its loading some scripts and not others, and/or not loading the modules properly, I can not tell, and none of the log files are helping out, and as far as I can tell all the files are there. Any help would be greatly appreciated, cause I do not want to have to rebuild this server.

further details:
If I do /etc/init.d/networking restart it won't bring up my eth0, but if I do ifconfig eth0 up it brings it up with no complaints, but I cant get an IP cause Im not exactly sure how to do dhcp manually in ubuntu.

---

### Post by penguinpi.com on 2008-03-18
See if when you boot up you can change your runlevel.

sudo init 4 (the default is probably 3 or 2)

if you get all your services then, something got messed up somewhere and change your default runlevel to 4.

edit /etc/inittab
# The default runlevel.

id:2:initdefault:

just change the 2 to 4 just don't set it to 0 or 6

hope this helps

---

### Post by penguinpi.com on 2008-03-18
also to set a static ip all you have to do is

ifconfig eth0 192.168.1.100(or whatever)

also you can play with the settings in

/etc/network/interfaces

I have gutsy server though, but i'm sure it's the same

---

