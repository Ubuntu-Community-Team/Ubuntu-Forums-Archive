---
title: "Installation from live CD without reboot"
date: 2008-04-15
forum: The Cafe
---

### Post by michaeljt on 2008-04-15
It would be really nice to use a live CD to install Ubuntu and to switch into the new system without rebooting first.  Any ideas about whether this is technically feasible?

---

### Post by koshari on 2008-04-15
chroot?

---

### Post by michaeljt on 2008-04-15
> **koshari said:**
> chroot?

I meant continuing with the same X session :)

---

### Post by az on 2008-04-15
man pivot_root


You would have to copy the contents of the ramdisk to the hard disk.  There probably are a few other things to clean up as well.

Brainstorm?

[http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

---

### Post by spamzilla on 2008-04-15
How long does a reboot take? 30secs - 1min? Maybe a bit longer?

 I'd much rather devs and others fixing bugs, rolling out updated programs etc rather than creating a feature which isn't really needed.

---

### Post by az on 2008-04-15
I think this would be useful.  So I put it on the brainstorm site:

[http://brainstorm.ubuntu.com/idea/7056/](http://brainstorm.ubuntu.com/idea/7056/)

---

### Post by spamzilla on 2008-04-15
> **az said:**
> I think this would be useful.  So I put it on the brainstorm site:

[http://brainstorm.ubuntu.com/idea/7056/](http://brainstorm.ubuntu.com/idea/7056/)

While I do disagree with this idea, you do bring up a very good point:

> 
There are occasions where a user can run the live cd, install some applications and customize the desktop only to have to repeat these steps after the installation has taken place. This would avoid that; the user would not have to repeat the same steps again. 


This could help further improve the install / setup process *if* the 'skip reboot' was made very easy to do (i.e new user friendly)

---

### Post by original_jamingrit on 2008-04-15
Is there a 'toram' cheatcode for the Ubuntu CD, like in Knoppix?  if there was, then it would be easy to implement for people with enough RAM.

EDIT:  NVM, I see that there is not.

This would be very difficult to implement, to umount your root directory (which would be the livecd) and then mount your newly installed root device.  This would be difficult to juggle while keeping your X session alive.

It kind of sounds like too much work for too little gain, but if there are some bored hackers sitting around... ?

---

### Post by az on 2008-04-15
> **original_jamingrit said:**
> Is there a 'toram' cheatcode for the Ubuntu CD, like in Knoppix?  if there was, then it would be easy to implement for people with enough RAM.

EDIT:  NVM, I see that there is not.

This would be very difficult to implement, to umount your root directory (which would be the livecd) and then mount your newly installed root device.  This would be difficult to juggle while keeping your X session alive.

It kind of sounds like too much work for too little gain, but if there are some bored hackers sitting around... ?

There is a toram boot prompt for Casper.  It is currently broken. but it is there.  Anyway, you wouldn't need it.  Whether your cramfs is in memory on on cd/usb flash you wouldn't use it.  You would use the root filesystem you just istalled.  You would pivot_root into it.

Your X session as well as all your apps are in memory.  If they need to load shared libraries, they would get them from the root directory on the disk and not from the cramfs image on the cd/usb flash.

It's a lot like going into hibernation.  The main problems with suspend/hibernation are hardware - the software works fine.  This is a lot less complicated.  You would basically need to take a snapshot of some portions of your filesystem before transfering over to your root directory on disk.

P.S. Please vote (for or against) the brainstorm idea.  That keeps the discussion going.

---

### Post by az on 2008-04-15
This idea is the least popular today, with double-digit negative votes...

---

