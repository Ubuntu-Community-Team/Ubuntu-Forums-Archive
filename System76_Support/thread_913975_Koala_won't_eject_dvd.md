---
title: "Koala won't eject dvd"
date: 2008-09-08
forum: System76 Support
---

### Post by MikeNick42 on 2008-09-08
My newly purchased Koala system ejects the dvd partway (just barely enough to grab and pull the disk out if you're fast) and then reloads it.
Has anyone else run into this or can anyone offer a solution?

---

### Post by thomasaaron on 2008-09-08
Hi, Mike.

I saw your email this morning, but I've not quite dug down to it yet. If you don't mind, I'll respond via the email, as this is a hardware-related anomaly that is unlikely to be helpful to a lot of customers.

---

### Post by giantclam on 2009-11-07
I am having the same problem.  Since upgrading from Jaunty to Karmic, I can not always eject the DVD with the button on the drive.  For example, after using K9 Copy, it asks you to insert a new DVD after copying the old one.  I can not eject the original.  I can only open the drive door with a paper clip and then the program will not continue.

---

### Post by BuchuBaron on 2009-11-08
I am having the same problem after upgrading.  It seems to be a well-documented but poorly solved bug in jaunty as well.  The eject succeeds, but then some automount feature immediately reloads the CD/DVD.

Does anybody have a solution that does not involve restarting the machine and changing CDs during bootup?

---

### Post by riseringseeker on 2009-11-08
Does this happen if you type "eject" (without the quotes) in a terminal as well?

---

### Post by tedmasterweb on 2009-11-30
I've been having a very similar problem. My DVD drive only worked with the original configuration coming from System76. As soon as I upgraded my system, or moved to a new distro, the DVD started failing. Specifically, it started to function only as a CD-RW, DVD read-only and now, after installing CentOS to see if that might fix it, it swallowed an unformatted DVD and refuses to eject it (because the OS doesn't even know it's in there).

I'm wondering if there is any way to fix this. I live outside the U.S. / Canada and I'm probably out of warranty so I may be looking at a new self-installed drive, but I'd appreciate any help on what drive to buy, detailed installation instructions (this tiny desktop machines can be a real pain to take apart) and whether or not this will actually fix the problem.

I must say I chose the Koala because it appeared to be a higher-end machine (and theoretically came with higher quality components). Was I mistaken?

There is a similar thread here: [http://ubuntuforums.org/showthread.php?t=771313]("http://ubuntuforums.org/showthread.php?t=771313")

Thanks to all who've posted similar problems.

Ted Stresen-Reuter

---

### Post by jdb on 2009-11-30
> **tedmasterweb said:**
> I've been having a very similar problem. My DVD drive only worked with the original configuration coming from System76. As soon as I upgraded my system, or moved to a new distro, the DVD started failing. Specifically, it started to function only as a CD-RW, DVD read-only and now, after installing CentOS to see if that might fix it, it swallowed an unformatted DVD and refuses to eject it (because the OS doesn't even know it's in there).

I'm wondering if there is any way to fix this. I live outside the U.S. / Canada and I'm probably out of warranty so I may be looking at a new self-installed drive, but I'd appreciate any help on what drive to buy, detailed installation instructions (this tiny desktop machines can be a real pain to take apart) and whether or not this will actually fix the problem.

I must say I chose the Koala because it appeared to be a higher-end machine (and theoretically came with higher quality components). Was I mistaken?

There is a similar thread here: [http://ubuntuforums.org/showthread.php?t=771313]("http://ubuntuforums.org/showthread.php?t=771313")

Thanks to all who've posted similar problems.

Ted Stresen-Reuter

If there is not an obvious way to manually eject the DVD, most players
have a small hole you can poke a straightened paper clip in to make it eject.

jdb

---

### Post by tedmasterweb on 2009-12-01
> **jdb said:**
> If there is not an obvious way to manually eject the DVD, most players
have a small hole you can poke a straightened paper clip in to make it eject.

jdb

Got it, but on these tiny Koala computers there does not appear to be any hole in the casing. I'm in the middle of restoring from a backup (been 24 hours so far, another 24 to go) but when that's done, I'll try restarting it holding down the eject button (that's worked in the past).

Thanks for the tip, though.

Ted

---

### Post by jdb on 2009-12-01
> **tedmasterweb said:**
> Got it, but on these tiny Koala computers there does not appear to be any hole in the casing. I'm in the middle of restoring from a backup (been 24 hours so far, another 24 to go) but when that's done, I'll try restarting it holding down the eject button (that's worked in the past).

Thanks for the tip, though.

Ted

You might look around for a different backup app.
I just use tar files & it only takes 5 or 10 minutes.

to backup
```
1) boot to a different partition or a liveCD
2) mount the device to backup to, ie., plug in a USB drive
3) mount the partition to back up, ie., sudo mount /dev/sda1 /mnt
4) cd to the newly mounted partition, ie., cd /mnt
5) sudo tar czf /pathToBackupDevice/someFileName.tgz .

```
to restore
```
1) boot to a different partition or a liveCD
2) mount the device to restore from, ie., plug in a USB drive
3) mount the partition to restore, ie., sudo mount /dev/sda1 /mnt
4) cd to the newly mounted partition, ie., cd /mnt
5) sudo tar xf /pathToBackupDevice/someFileName.tgz
```

to learn about tar
```
man tar
```

If you re-format before you restore, the partition will be completely defragmented.
NOTE: If you use UUIDs in grub or fstab, a re-format will assign a new UUID to the partition.

This can be automated with a script.

jdb

---

### Post by thomasaaron on 2009-12-01
Yeah, the old koalas didn't have an eject hole. They have the Mac-style power ejectors.

---

### Post by tedmasterweb on 2009-12-01
Hey there. I really appreciate the tips but in this particular case, the backup was a 60 gig file being copied over a 802.11b wireless connection :-(

I tarred and gzipped up all my files and copied them to another computer (a Mac) so that I could do a fresh, headless install of CentOS (since I don't have a monitor, keyboard, or mouse hooked up to the Koala Mini).

I have several internal hard drives I've boxed up to use as external drives, but there all from old computers and none are more than 20 gigs and that's where my Linux knowledge ends: how to mount several drives as one and how to format them to a file system usable on both Linux and Mac).

Thanks again for the suggestions, though. Nice to see people willing to try and help around here!

Ted

---

### Post by tedmasterweb on 2009-12-01
Well, the copy finally finished and I restarted the machine holding down the eject button. The DVD popped out and when everything booted back up, I popped in a new Sony DVD+R disc and tried burning a DVD:

```
growisofs -dvd-compat -Z /dev/dvd=/home/gustave/Desktop/vncCentOS.iso 
Executing 'builtin_dd if=/home/gustave/Desktop/vncCentOS.iso of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 8.2x1352KBps.
    1572864/4002465792 ( 0.0%) @0.0x, remaining 254:22 RBU 100.0% UBU   2.1%
    1572864/4002465792 ( 0.0%) @0.0x, remaining 423:56 RBU 100.0% UBU 100.0%
    1572864/4002465792 ( 0.0%) @0.0x, remaining 551:08 RBU 100.0% UBU 100.0%
    1572864/4002465792 ( 0.0%) @0.0x, remaining 678:19 RBU 100.0% UBU 100.0%
    1572864/4002465792 ( 0.0%) @0.0x, remaining 847:53 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=300h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/dvd: flushing cache
/dev/dvd: closing track
:-[ CLOSE TRACK failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
/dev/dvd: closing disc
:-[ CLOSE DISC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
/dev/dvd: reloading tray

```

So I tried just burning a single file to the same DVD via k3b and although the blank DVD spins up and appears on my desktop as "Blank DVD+R Disc" I got the following error message from K3b: "K3b did not find a suitable writer. You will only be able to create an image."

So, not being one to give up easily (obviously) I dragged a document onto the DVD icon, opened it, and clicked the "Write to Disc" button. Not surprisingly, I got the following error: "There was an error writing to the disc: The recorder could not be accessed."

And so... I popped the DVD-R disc I had been testing with prior to installing CentOS just to see if it was a disc-type error and indeed, the disc failed to spin up (mount) or appear on my desktop and the only way to eject it was pressing the little eject button on the case.

I popped the DVD+R disc back in to do some more testing and it failed to spin up, or appear on the desktop, or even eject (using the hardware eject button).

Are we having fun yet? Does anyone have any idea what is going on here?

I'm guessing this is either a lose cable or a defective drive, but that's totally a guess...

Thanks in advance.

Ted S-R
[http://tedmasterweb.com](http://tedmasterweb.com)


At least now I know that I should be using DVD+R.

---

### Post by thomasaaron on 2009-12-02
> Does anyone have any idea what is going on here?

Bad drive. Email support for instructions, quote, etc...
support...at...system76...dot...com

---

