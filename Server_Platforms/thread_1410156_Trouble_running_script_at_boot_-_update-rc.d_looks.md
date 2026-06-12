---
title: "Trouble running script at boot - update-rc.d looks fine but doesn't work."
date: 2010-02-18
forum: Server Platforms
---

### Post by jptech on 2010-02-18
Hi,


Edit: My script is executing.  There must be something wrong with the script I'm trying to run.  Ignore this question.



I'm having trouble getting a script to start on boot.  I'm using JeOS (Ubuntu 8.04.3 LTS).  I have a script that I can start / stop by hand, but I can't get it to start on boot.  Here's a quick description of what I think is relative info:

I'm using LVM and have two logical volumes:
- rootvol --> /
- datavol --> /apps

My script is on the datavol volume and is linked in init.d:
- /etc/init.d/myscript --> /apps/myprog/bin/myscript

All of the rd*.d symlinks are correct.  If I had to make a guess, I'd say the 'datavol' volume isn't available when the system is booting up, so it doesn't even try to execute my startup script.  I've tried:

update-rc.d myscript defaults 90

...but it doesn't help.  I think I need a way of making sure my 'datavol' volume is available / mounted before the script tries to execute, but have no idea how to do it.  Any suggestions?

Edit: Now that I look more closely, I see the message:

* Mounting local filesystems...          [OK]

...quite a while before my script should be running, so I have no idea what's wrong.  I've tried looking through logs, but can't find anything.


Thanks in advance,
Ryan

---

