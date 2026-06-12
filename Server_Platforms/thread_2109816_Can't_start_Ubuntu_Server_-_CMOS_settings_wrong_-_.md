---
title: "Can't start Ubuntu Server - CMOS settings wrong - fd0 error"
date: 2013-01-28
forum: Server Platforms
---

### Post by Wiking on 2013-01-28
Hi, I can't get my Ubuntu server to run. 

I end up getting this message at boot:
> WAIT....

CMOS settings Wrong


Press F1 to Run Setup

Press F2 to load default values and continue

error: fd0 error

It's Ubuntu 11.10 running on an old Celeron from early 2001.

I believe it must have something to do with the new year. I haven't booted up since December, but today I went to boot it up for the first time this year and it didn't run.

[http://ubuntuforums.org/showthread.php?t=2004472&page=2]("http://ubuntuforums.org/showthread.php?t=2004472&page=2")

In the link above you can see that I modified a few things in BIOS and in Grub in order to get it to boot and shutdown, starting with post #18.

Should I change date in BIOS?

Thanks.

---

### Post by aromo on 2013-01-28
Most likely CMOS values got corrupted (dead battery?).

Try reloading factory values (F2).  If it works, try setting the correct date and see if it boots up again.  If it doesn't work try disabling the floppy drive in the BIOS.

If it's a dead battery, you can get it in the dollar store.

---

### Post by Wiking on 2013-01-28
When I press F2 (default values) I get the** fd0** error.

Like I said in my initial post I edited some values in grub that affected boot.

---

### Post by chrisguk on 2013-01-28
Hey there and welcome.

Have a look at this launchpad bug and see if it helps:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568720]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568720")

---

### Post by SeijiSensei on 2013-01-29
/dev/fd0 is a floppy drive.  Do you have one of those?  If so, either disable it in the BIOS or simply unplug the cables from the back of the drive.  Then try booting again.

---

### Post by furything on 2013-01-29
Hi 

What you are describing is before grub gets a chance to start.

Agree sort off
> /dev/fd0 is a floppy drive.  Do you have one of those?  If so, either  disable it in the BIOS or simply unplug the cables from the back of the  drive.  Then try booting again.     By setting the BIOS to defaults you have told it there is an installed floppy drive and to halt on all errors.

Go into BIOS and if you don't have a floppy change BIOS to not installed, don't just remove cable because the BIOS boot sequence will still require it. IF you do have one still set as uninstalled it may be your floppy drive has failed. 

For Errors you can reduce what it is going to halt on ie all but keyboard.

---

### Post by Wiking on 2013-01-29
I was able to get the server booting after disabling the floppy drive. That's fixed.

However I now have another problem that I can't seem to connect the server to my network. Everything in /etc/network/interfaces is correct, I don't see any errors.

I even did a ping test and no packets were dropped.

It doesn't even show up on my router.

Whenever I try connecting with Putty, I just get message: **Network error: Connection timed out**

---

### Post by chrisguk on 2013-01-29
Ok without knowing the topology of your network it can be difficult to diagnose your problem.  You say that you are connected.  So the first things I would check are this :

Check the router config to make sure it has allocated you an IP Address statically if not then just manually allocate one, you may need to read your router docs for this.


Make sure the ports are open in your firewall by issuing the following commands:


Sudo ufw allow 80 (the same for 443, 22 and 53 if you want DNS)


80 is the web and 443 is https.  22 is for SSH but most experienced users or admins change this number for Security.  You don't need to worry about that at the moment because until you have mastered the basics you can then start making complicated tweaks.


Btw I assume that when you issue ifconfig it displays your IP and MAC address correctly?


If you get any errors then just post them here.

---

### Post by Wiking on 2013-01-30
fixed

---

### Post by Wiking on 2013-01-30
Ok got it fixed. in ufw status port 22/tcp was Denied. Changed that and now can connect. 

thanks all.

---

