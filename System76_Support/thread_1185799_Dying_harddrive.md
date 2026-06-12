---
title: "Dying harddrive?"
date: 2009-06-12
forum: System76 Support
---

### Post by Derath on 2009-06-12
panp4n

So I upgraded to 9.04 two nights ago, yesterday the laptop went into sleep mode (no idea why, for power management I have no sleep modes when plugged in), and froze when it tried to wake up, the SysReq-REISUB trick didn't work, the three finger salute didn't work, so had to hold the power button.

This is where the fun begins...

Upon reboot, fsck complained about an error and that I had to run fsck manually, which I did, then rebooted, fsck still complained and had to run manually again, this time with a bunch of inode errors, reboot again, now I'm sitting at a grub> prompt... found the post in here about the serp with a similar issue, okay, so now it's live cd time...

Started the live cd, went to the partition editor and checked/fixed both sda1 and sda3, took a while, but it said successful, reboot, still at the grub prompt. Hmm.... booted the cd again, all the files from the root partition are now in lost+found and numbered... oh boy, root's hosed now, home looks fine though, with one exception of character encoding issue (??? looks like wine directory from the files), copied home to a usb drive. Killed the root partition and choose to format as ext4 and just reinstall.

Reinstall went fine, default stuff worked fine, so today I started loading all the apps I had before. When I got most of them it was time to hit the websites for all the other apps (virtualbox, playonlinux, "what were those other libraries I needed for other apps?" type stuff) and firefox wouldn't start. Okay no problem, check logs, nothing in there suspicious, now no apps are working at all, they attempt to start and bail, but at least I have a pretty desktop!

Okay, something else is going on here, so attempt reboot, and I'm stuck at login prompts with ext4 complaining about inode errors now, hard reboot, at the grub prompt again???? Okay, second system: look up information on grub prompt command lines, try to mount hd(0,1), and it won't mount. Uh oh...

Live cd time again, now the partition editor sees the root partition as unknown. This isn't good...

Gave up and emailed support. Tom, I hope you get my email soon.

---

### Post by albinootje on 2009-06-12
> **Derath said:**
> 
So I upgraded to 9.04 two nights ago
--cut--
Killed the root partition and choose to format as ext4 and just reinstall.


1) Check your hard drive with gsmartcontrol/smartmontools and badblocks apps.

[http://gsmartcontrol.berlios.de/home/index.php/en/Screenshots](http://gsmartcontrol.berlios.de/home/index.php/en/Screenshots)

2) Using Jaunty/9.04 + ext4 partitions means that you'll have to use a 2.6.30 kernel to avoid problems afair.

---

### Post by thomasaaron on 2009-06-12
This problem is actually a Tracker bug. It occurs either when upgrading directly from Intrepid to Jaunty or when doing a fresh install from some older Jaunty disk images.

We have an ongoing forum post going on it. Please see...
[http://ubuntuforums.org/showthread.php?p=7225556#post7225556](http://ubuntuforums.org/showthread.php?p=7225556#post7225556)

Running these commands should fix it...
sudo apt-get install tracker-utils
tracker-processes -r 

After running these commands, try to run fsck on your partitions from a live CD. If that doesn't repair your filesystem, you may need to re-image. 

If fe-imaging becomes necessary, you should download the latest Ubuntu image (i.e. don't use an older disk image, as it may install the problematic software).

---

### Post by Derath on 2009-06-12
badblocks and gsmart (short test) reports no errors...

Since I can't even access the root partition now, I guess I will have to reinstall again and then do the tracker fix...

---

### Post by thomasaaron on 2009-06-12
Re-install from a freshly downloaded image. Then you will not have the tracker bug.

---

### Post by Derath on 2009-06-13
Reinstalled from a fresh cd, tracker was still installed by default, so I installed the tools, did tracker-processes-r and then removed tracker completely.

Although my /home partition still registers as having an error, so as soon as I'm done installing stuff and fixing, I'll go back to the live cd and repair /dev/sda3 again.

Also have another issue, but I'll start a new thread for that...

Oh and Tom: From one tech to another, THANKS SO MUCH! From watching this forum, emails, and I believe I even got to talk to you once before; you are doing a GREAT JOB!

---

### Post by robert.rankin.jr on 2009-06-14
I'm having this same problem on a panp5. It was working perfectly until this started happening.

I've formatted like five times in the past five days trying to fix it, each time with ext4. I've downloaded the latest iso and everything. Now I'm trying with ext3, and it seems like it will work, but I'd like to manage to resolve this problem with ext4.

With the latest iso, I tried your tracker suggestion, but that didn't help. I'm thinking about trying it with Karmic later this week to see if that helps.

Any ideas?

Thanks,
Robert

---

### Post by Derath on 2009-06-14
Robert: right after a reinstall (and I mean immediately), install the tracker-utils, run the tracker-processes -r, and then remove tracker, then boot the live cd again and repair both partitions. That seemed to work for me.

Even on a fresh download I still found tracker was still installed.

---

### Post by thomasaaron on 2009-06-15
> I've formatted like five times in the past five days trying to fix it, each time with ext4.

ext4 is unstable. That's probably the issue. If you use a freshly downloaded januty 64-bit cd and ext3, you should be fine.

---

### Post by robert.rankin.jr on 2009-06-15
Doesn't seem to be it. Last night I installed on ext3... woke up, the computer was frozen, restarted and major breakage. When I boot up into normal mode, I get a green screen and when I boot into recovery mode I get a busybox prompt saying that it can't mount /sys, /dev, or /proc... how weird.

Thanks,
Robert

---

### Post by thomasaaron on 2009-06-15
> Even on a fresh download I still found tracker was still installed.

Not to be overly inefficient here, but are you certain you are downloading the latest images from [http://ubuntu.com/downloads](http://ubuntu.com/downloads) ? 

Tracker has been removed from the images (unless they recently re-inserted it). I've not downloaded an image for a while, so I guess that is possible.

---

### Post by robert.rankin.jr on 2009-06-15
Don't know how to check, but it doesn't look like it.

> robert@robert-laptop:~$ tracker-processes -r
Found 132 pids...
Setting database locations
Checking database directories exist
Checking database version
  Could not find database version file:'/home/robert/.cache/tracker/db-version.txt'
  Current databases are either old or no databases are set up yet
  A reindex will be forced
  Creating version file '/home/robert/.cache/tracker/db-version.txt'
Checking database files exist
Removing all database files
  Removing database:'/home/robert/.local/share/tracker/data/common.db'
  Removing database:'/tmp/tracker-robert/cache.db'
  Removing database:'/home/robert/.cache/tracker/file-meta.db'
  Removing database:'/home/robert/.cache/tracker/file-fulltext.db'
  Removing database:'/home/robert/.cache/tracker/file-contents.db'
  Removing database:'/home/robert/.cache/tracker/email-meta.db'
  Removing database:'/home/robert/.cache/tracker/email-fulltext.db'
  Removing database:'/home/robert/.cache/tracker/email-contents.db'
Setting index database locations
Checking index directories exist
Checking index files exist
Could not find index file:'/home/robert/.cache/tracker/file-index.db'
Could not find index file:'/home/robert/.cache/tracker/email-index.db'
Removing all database index files
  Removing database index:'/home/robert/.cache/tracker/file-index.db'
  Removing database index:'/home/robert/.cache/tracker/email-index.db'

and when I did grep -i tracker, it only returned my search.

I checked the partition and am hoping that was just a fluke... though I doubt it, based on the history I've been having with this. If it helps, I was looking through my logs... and it seems that there's not even a trace of any of this happening. Guess that makes sense since it probably didn't access the partition. But I was expecting to find something, I guess...

Thanks,
Robert

---

### Post by Derath on 2009-06-15
Tom: Unfortunately that was a new download from the website (from the Michigan LUG mirror), that why I had asked if there was a date change.

I dunno, maybe I chose the wrong mirror to download from.

---

### Post by thomasaaron on 2009-06-15
Try this...

sudo apt-get install tracker-utils
tracker-processes -r 

...and reboot.

Man, those errors scream "T-R-A-C-K-E-R!"

I'll be surprised if your hard drive is going out, but I suppose it's a possibility.

---

### Post by robert.rankin.jr on 2009-06-15
Didn't work for me. This is what I've tried.

Ext4
Ext3
Changing BIOS operating system to "Other"
Removing Windows XP
Removing tracker
Removing tracker immediately after first boot
Trying Karmic again... which seemed to be okay, but quickly scrapped it after two boots because of grub2 and no dual boot... plus  I need a stable system


And I'm not really sure what else that there is I can try... Any other ideas? I'm trying XFS right now... and if that doesn't work, I'm just thinking it's something wrong with the HD. But the problem with that is that Windows worked fine.


Robert Rankin

---

### Post by thomasaaron on 2009-06-16
We can try a new hard drive if you are still under warranty. Contact me via email if you want to go that route.

---

### Post by robert.rankin.jr on 2009-06-16
Will do. Thanks.

Robert

---

### Post by jbelmonte on 2009-06-16
When you tried to go back to ext3 after trying ext4, did you reformat the partition?

---

### Post by robert.rankin.jr on 2009-06-16
Is there any other way to change to ext3 from ext4? ;) Yes, I did. And if anyone cares, XFS and JFS both died on me. Only thing I haven't tried is ext2.

Thanks,
Robert

---

### Post by robert.rankin.jr on 2009-06-18
If anyone has the same problem that I had, I got it working by installing the 32 bit version. It seems to be related to this bug... Haven't read the whole thing yet, but hopefully there's another option. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)

---

### Post by robert.rankin.jr on 2009-06-18
If anyone else is experiencing the same problem and the tracker fix isn't working, there does seem to be a solution to this bug.

> wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb)
sudo dpkg -i linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb

Yay for Ubuntu systems that run perfectly... or, in my present situation, Kubuntu.

Looks like a few of the devs are brewing up a fix as well. I know Karmic works fine.

---

### Post by phyzome on 2009-06-18
Tom, how can this possibly be a bug in Tracker? Doesn't that run in userspace, far, far away from the filesystem code? How can it be corrupting superblocks?

Derath, check out this thread from a few weeks ago, where I experienced the same troubles with a newly upgraded panp4i:

[http://ubuntuforums.org/showthread.php?t=1142589](http://ubuntuforums.org/showthread.php?t=1142589)

I never could get the tracker fix to work. The only thing that *did* work was not using Jaunty. (Annoying, because that version finally fixes a screen resolution bug.)

---

### Post by thomasaaron on 2009-06-18
Looks like it could be this...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

Faulty SATA controller driver. Evidently, it isn't present in the -9 kernel. I'd suggest reverting. We're testing on this end too.

---

