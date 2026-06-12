---
title: "Starling Filesystem Errors on Boot"
date: 2009-11-06
forum: System76 Support
---

### Post by JeffV on 2009-11-06
I got the Starling netbook a couple months ago and started seeing this problem a few weeks ago.  

Almost every time I boot the system, it starts the Ubuntu splash screen and the bar starts filling, then it suddenly goes to a screen reporting file system errors on sda1 and does a bunch of automated things to try and fix the problem.  It usually ends up fixing it and I'm able to eventually reboot and everything is fine (no loss of data from what I can tell).  

A couple times, it would try to fix things, then give a graphic screen saying "Could not start the X server due to some internal error".  Then I would log into a basic console, do reboot, and on the splash screen get a "Unclean shutdown, checking drivers".

At this point, it then says /dev/sda1 contains a file system with errors...
"/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY..."

It then starts a maintenance shell, and I follow the instructions on the screen to run fsck.  I get occasional message of "Error reading block xxx...while getting next inode from scan.  Ignore error<y>?" and "Force rewrite<y>?" I just say yes to all of these.  it finishes and I do a Ctrl-D to restart.  Then everything seems to be working fine again.

Is this a sign of a bad hard drive?  It's done this several times now, this most recent being the worst since it took longer to go through and fix all the errors.

---

### Post by samalex on 2009-11-06
The 2.6.28-11-generic kernel on 64-bit Ubuntu is known to cause file system corruptions, but it was fixed with the kernel update from the Ubuntu repositories.  My PanP5 shipped with this kernel, which was about three months ago, but the night I received my laptop I updated this from the repositories and never saw any problems.

Could this be the problem on your end?

If you're running Karmic with ext4 there is also a bug that causes filesystem corruption there as well.  [See here]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579") for more info.

I'm not sure if this helps, but maybe it'll give you more info to tackle this problem.  I'm still alittle gunshy to upgrade to Karmic, and until the FS problems are resolved with ext4 even if I do upgrade I'll stick with ext3.

Take care,

Sam

---

### Post by JeffV on 2009-11-06
Well, it probably isn't one of those.  I'm running 32-bit Jaunty, as originally set up on the machine.  Kernel version 2.6.28-15-generic.

---

### Post by thomasaaron on 2009-11-06
I'm not aware of any bugs in 32-bit Jaunty that caused corruption. It was 64-bit Jaunty that was having the issues.

Try running fsck from a live CD. Maybe that will nip it in the bud.

```
To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partiton layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them. 

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.


```

If the problem continues, it could be either software or hardware releated.

---

### Post by JeffV on 2009-11-06
Well, I'm not sure how to do this since I don't have a CD-drive for the netbook.  :)

Edit:  Well I tried fsck from Knoppix booted off a USB stick.  It didn't seem to do anything.  I found a guide for transferring the Live CD to a USB stick.  I'll give it a try.  If it still doesn't work, I'll just do a reinstall of the OS.  I backed up all my data, so I don't have to worry about losing anything.

---

### Post by thomasaaron on 2009-11-06
Oops. Yep, sorry about that. It's been a long week.

---

### Post by JeffV on 2009-11-07
So I reinstalled Jaunty from the USB img.  Everything was working perfectly after reinstalling.  I reformatted the hard drive, but kept the same exact partitions that were initially set up on the netbook (with / on sda1, /home on sda3, swap on sda2).  

Then I installed all the updates that were available.  All the updates installed, I rebooted, and I immediately got the filesystem errors again.  

So I'm guessing one of the updates messed everything up.  I only tried restarting twice before installing updates to make sure everything was ok.  I downloaded tons of updates all at once, so I have no idea which update may have done this.  Any ideas?

---

### Post by thomasaaron on 2009-11-09
Well, I'm not hearing anything about updates hosing filesystems on Starlings (or anything else for that matter) across the board. So, my guess is that your hard drive has some sort of problem. Please contact me by email and we'll work on getting you a new drive. support...at...system76...dot...com.

---

