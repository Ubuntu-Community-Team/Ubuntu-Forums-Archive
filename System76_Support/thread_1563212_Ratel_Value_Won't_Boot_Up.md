---
title: "Ratel Value Won't Boot Up"
date: 2010-08-28
forum: System76 Support
---

### Post by Teasdale on 2010-08-28
This can't be good.

I had my computer off for a few weeks; I've been using my Starling. I went to boot the Ratel up today, and I'm getting an error message before it gets to the desktop. Here's what the display/monitor says:

> 
Boot from (hd0.0) ext3 e7728359-15b1-4eb6-a7c9-db1b40e7c807
Starting up ...
[ 6.8866341 ata3.00: revalidation failed (errno=-5)
[ 12.002634] ata3.00: revalidation failed (errno=-5)
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/e7728359-15b1-4eb6-a7c7-db1b40e7c807 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _(blinking cursor)

---

### Post by Teasdale on 2010-08-28
I read someone else who said this was happening to them sometimes when they booted up, so I thought I'd try to boot up again.

It started, had a bunch of errors really quickly before it wanted me to log in. I logged in, it got to the desktop with the toolbars but no wallpaper. Then the wallpaper showed up, but the toolbars disappeared. The display was also vibrating (an issue I've had a couple other times when I booted up, but for which no source or problem could be found to fix).

So I pushed the restart button, and I got the "System 76" screen, but nothing beyond that Normally, it says "Press <F2> for help," but that wasn't there. Just the System 76 logo.

I pushed restart again, and it got past the System 76 screen and then said said "boot failure. Press any key to continue."

The computer is a little over a year old; it's still running the original Ubuntu 9.04 it came with.

I think this is probably really, really bad . . .

---

### Post by isantop on 2010-09-01
Would it be possible to try booting from a LiveCD or LiveUSB? You should be able to make one from your Starling.

If you can, try looking through the hard drive to see if any of the data on it is missing, like your home folder. There may be a few partitions to check.

---

### Post by Teasdale on 2010-09-01
Thanks for responding. I made a Live CD of Puppy Linux, but when I put it in, the computer bypassed the CD and booted up semi-normally. It was slow, and looked like it was going to do this:

> 
It started, had a bunch of errors really quickly before it wanted me to log in. I logged in, it got to the desktop with the toolbars but no wallpaper. Then the wallpaper showed up, but the toolbars disappeared.

but it didn't; after the bunch of errors, it actually did start up and got to the desktop. Then I got a pop-up saying that Dropbox wouldn't work unless I installed DRM files (I do have Dropbox, but never saw that before!), but I got a row of error boxes when it tried to download them. I was able to close all of that out, and now I'm trying frantically to send my pictures to a USB drive - it says it's going to take an hour.

---

### Post by Teasdale on 2010-09-01
I think it sent some of my pictures to the USB, but then started giving me error messages saying "error saving this photo," and "error saving that photo." Then the icons on the desktop disappeared, and now nothing will load.
I have toolbars on the top and bottom of the desktop, but when I try to load anythingg, I get a box saying something like 

> 
Could not launch 'Log File Viewer'
Failed to execute child process 'gnome-system-log' (input/output/error)


---

### Post by Teasdale on 2010-09-02
I shut it off with the power button and restarted -- I went into the bios and allowed booting from the drive, but it still bypassed the Live CD and actually booted up normally. Everything seems normal at the moment, except that my display is bigger than usual.

I'm transferring files via Dropbox, and I was able to get a Log File. It's long - about 600K for July28, and 1.3MB for Aug 28.

---

### Post by isantop on 2010-09-02
Would it be possible to try a liveCD of Ubuntu? Preferably version 10.04.1.

---

### Post by Teasdale on 2010-09-06
I can try a Live CD.

Right now, the computer has been running for days - ever since it started normally, I've just left it running. During the three days it's been on, it seems normal. I've backed up all my files, photos and everything.

In the past, sometimes when it booted up, the display would be all wavy and shaky. I've always been a little leery about turning it off or restarting it because I never knew whether the display would be right when it started up again. I can't help but think this is related.

I'll have a Live CD ready to boot from next time I restart.

---

