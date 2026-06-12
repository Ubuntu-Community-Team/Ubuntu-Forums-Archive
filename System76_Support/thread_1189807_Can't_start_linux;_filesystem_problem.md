---
title: "Can't start linux; filesystem problem"
date: 2009-06-17
forum: System76 Support
---

### Post by glacialfury on 2009-06-17
** SOLVED: The problem described in this thread was solved by booting via LiveCD, and running fsck (from within the GUI partition manager) on both partitions.**

Quick: errors after upgrade, particularly with Impress; now system boots to grub prompt and has filesystem errors when trying to mount either / or /home partitions from within LiveCD

Please help. Serp, bought in summer 2008, 

Regards,
glacialfury

ps: as a temporary fix, if I can launch the (functional) Windows partition from that grub prompt, and someone knows how, I'd be much obliged; I have time-critical work on this laptop.

Long:
My dear friends,

I have run into an unfortunate problem, and once again need your expertise.  I have been using my Windows partition primarily for the past few weeks, and started up Ubuntu yesterday.  I recently upgraded to 9.04 (on a serval, I *think* serp3? serp4?  Purchased in summer, 2008) without looking at the System76-specific upgrade instructions.  It seemed to work ok and updates were fine.  I experienced some application errors while doing some work, I don't recall what, but they didn't seem important at the time, and eventually tried logging out and back in, which caused a failure that made the machine switch to manual/safe/repair console and told me to run fsck, because there was a problem with the filesystem (sda3, where /home is mounted).  

I ran fsck, which encountered a number of errors, all of which it offered to fix.  I pressed "y" for each offer; this eventually went over 1200 times, most of which were apparently reassigning things to blocks.  I rebooted, and this time it wanted fsck for the root partition; I did the same thing there, pressing "y" for each proposed fix.

I rebooted, and things seemed to be working alright, although OpenOffice seemed a lot buggier than usual.  I attributed it to the heavyweight powerpoint files I was making it deal with.  At some point, Impress stopped showing the pictures (text displayed), I couldn't see any programs I opened after that point (although I could close them - invisibly - with the "Force Kill Window" applet thingy by randomly clicking in the right spot), and when I tried to log out to "refresh" X, it was blocked by OpenOffice - would I like to end it and log out anyway?  

Sure, I said.  Next reboot landed me at the grub prompt.

At this point, I'm writing from a LiveCD.  I can't access my data on either the root partition or the /home partition.  When I try to mount either from within the Places menu (where the partitions are all correctly listed), I receive the error:

"Cannot mount volume.  Unable to mount the volume.

Details: mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error     In some cases useful info is found in syslog -try dmesg | tail or so"

I *can* mount the windows partition from the LiveCD.

---

### Post by glacialfury on 2009-06-17
update:

I was able to check/repair the root partition from the built-in partition editor on the live cd, and then mount it with "sudo mount -t ext3 /dev/sda1 <dir>".  I did the same with the /home partition, on /dev/sda3.

I haven't tried rebooting, but the files are accessible; the partition editor's feedback was something about the reported size being different than the actual size, which it presumably fixed.

---

### Post by ScottTE on 2009-06-17
A similar thing happened to me last night. My problem started when I was trying to boot the laptop into the BIOS. I couldn't remember which key it was powered off several times prematurely, this led to putting me in to the GRUB menu and I had to run fsck manually. After several hundred fixes I finally got a good boot, but now my keyboard doesn't work so I can't login.. I'm thinking one of the files that was corrupted has something do with the keyboard.. Will work on it later this afternoon.

Ubuntu 9.04

---

### Post by glacialfury on 2009-06-17
Running fsck from the partition manager on the LiveCD seems to have cured both partitions; I am able to boot and so far, it seems to be working normally.

---

### Post by izizzle on 2009-06-17
You could try running fsck.

edit: beat me to it!

---

### Post by thomasaaron on 2009-06-17
This problem may be a Tracker bug. It occurs either when upgrading directly from Intrepid to Jaunty or when doing a fresh install from some older Jaunty disk images.

We have an ongoing forum post going on it. Please see...
[http://ubuntuforums.org/showthread.php?p=7225556#post7225556](http://ubuntuforums.org/showthread.php?p=7225556#post7225556)

Running these commands should fix it...
sudo apt-get install tracker-utils
tracker-processes -r 

After running these commands, try to run fsck on your partitions from a live CD. If that doesn't repair your filesystem, you may need to re-image. 

If fe-imaging becomes necessary, you should download the latest Ubuntu image (i.e. don't use an older disk image, as it may install the problematic software).

---

### Post by glacialfury on 2009-06-17
I'll try that.  However, a new problem cropped up.  I used the system for awhile, and closed all the programs.  I opened firefox, but it didn't display on the screen.  I managed to find its borders, and that gave me the window frame, but nothing inside it (just titlebar and border).  Same thing with all other programs; either they showed up "invisible", or they didn't launch at all.

I logged out, intending to log in again, figuring it was an X error.  I was right, but I don't know what to look for.  This is the error on logout (after switching to a console-drawn screen)
"Could not start the X server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnoses.
In the meantime this display will be
disabled.  Please restart GDM when 
the problem is corrected.

<Ok>"

You can't click the Ok button or trigger it in any of the usual ways (enter, space, mouse); ESC, q also don't work. This can't-restart-x problem is mentioned in the post you linked, so I'll give that a try later when I'm home.

Thanks for the help.

---

### Post by thomasaaron on 2009-06-17
Right, tracker just hoses the filesystem, which can have an effect on everything.

You might want to write those commands down, boot into recovery mode, and run them from there. I wouldn't want to reboot again before fixing tracker and running fsck from a live CD.

This was such a ridiculous bug.

---

### Post by jdb on 2009-06-17
> **thomasaaron said:**
> Right, tracker just hoses the filesystem, which can have an effect on everything.

You might want to write those commands down, boot into recovery mode, and run them from there. I wouldn't want to reboot again before fixing tracker and running fsck from a live CD.

This was such a ridiculous bug.

There might be more going on here than just the tracker bug.
Everything I can find about it just compains of tracker corrupting it's own index file and hogging the CPU.

Check out this bug & it's 8 duplicates:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691")

jdb

---

### Post by thomasaaron on 2009-06-18
Holy mackeral. Definitely a possibility. Funky sata driver controllers would explain a lot. If that's the case, it sounds like about the best work-around at the moment is to go back to the -9 kernel.

---

### Post by serval1 on 2009-06-19
Okay I was lucky. When I upgrade Grub, an invalid UUID always replaces my ROOT in menu.list. I have to manually replace this using the live CD. When I did the last time, the old kernel was made default (2.6.27-14-generic. I made a good mistake). In Grub, my alternate OS is 2.6.28-11-generic. I do not have the problems described here.

Now, I see the 2.6.28-13-generic Linux image is available. Does this fix the problem and is it safe to upgrade? I did not have the time this morning to run through the change record yet. I'm hoping someone has already done that, and can report his/her findings to all.

---

