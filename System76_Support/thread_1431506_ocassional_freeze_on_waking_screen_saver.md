---
title: "ocassional freeze on waking screen saver"
date: 2010-03-16
forum: System76 Support
---

### Post by Pitt Stains on 2010-03-16
Hello,

I'm running Ubuntu 9.04 on my Gazelle Ultra (gazu1).  9.04 is the originally installed OS, so there shouldn't be any cruft from messy OS upgrades.

I'm kind of a paranoid user, so I lock my screen (using Brightside, aka Screen Actions -- if that matters) every time I step away from my machine.

Oftentimes, I come back and the screen saver is still running -- in other words, my computer hasn't gone to sleep or hibernated yet.  I usually press the down arrow to stop the screen saver and get the prompt for my password.  80% or more of the time, this works as it should.

When it doesn't work, the screen saver stops animating and just stays frozen on the screen.  The login dialogue never shows up, and sometimes (but not always) the fan starts going as if the machine were suddenly doing a lot of work.  At this point, I have no choice but to manually power down the machine and start over.

Any ideas?
-Pitt

---

### Post by Silvertones on 2010-03-17
Same issue here as well.

---

### Post by thomasaaron on 2010-03-17
I'm not sure about brightside. That could be causing some sort of segfault. If you un-install brightside, do you get the same symptoms?

Also, locking the screen isn't the same thing as suspending.

---

### Post by Flyers2391 on 2010-03-17
I had this problem in 9.04 as well on my z61m thinkpad.  I wouldn't manually turn on the screen saver but after it would start, about half the time my system would lock.  After playing for a month I turned off the screen saver ... I don't have this problem in 9.10 anymore

---

### Post by Pitt Stains on 2010-03-18
It seems unlikely to me that the cause would be brightside.  As far as I know, brightside's job is done when the screen saver is activated.  It works like this:
[LIST=1]
[*]brightside is configured to activate the screen saver when I move my mouse to the top right corner of the screen
[*]screen saver is configured to lock the screen when activated
[/LIST]
... so it doesn't appear to me that brightside is directly involved in locking the screen.

I'm happy to uninstall brightside and use the "lock screen" option in the user switcher to eliminate the possibility, but I think we're barking up the wrong tree.

To be clear on the question of suspend/hibernate, I'm not doing either.  I guess there's a setting somewhere that suspends the machine if it's been inactive for X minutes, but I'm talking about periods of less than X minutes, where the screen is simply locked and the screen saver is active.

I put off upgrading to 9.10 because I heard folks were having problems with it at first.  Maybe I'll upgrade in the near future, but not before I take an image of my hard drive.

I just experienced the issue again, and I immediately used the System 76 Driver to produce the logs tarball.  I'd post it here, but I'm not sure if there's sensitive stuff in there that it'd be unwise to make public.  Thomas, if it's safe to do so, I'll post it here; otherwise, I'd be glad to email it to you.

Thanks to everyone who responded.
-Pitt

---

### Post by Silvertones on 2010-03-18
I don't have brightside sorry. I disabled the hibernate & suspend and have been fine. The worst time was yesterday. I was doing the weekly update. The screen went into screen saver and locked up. I had to wait for a couple hours or so to make sure the updates had been installed before holding doen the off button.

---

### Post by Pitt Stains on 2010-03-18
@Silvertones, are you also on Ubuntu 9.04?

---

### Post by Silvertones on 2010-03-19
9.1

---

### Post by thomasaaron on 2010-03-19
> I'm happy to uninstall brightside and use the "lock screen" option in the user switcher to eliminate the possibility, but I think we're barking up the wrong tree.

Yes, please try it. It will only take a minute. Since I've never seen this problem before, and I've never heard of brightside, I'd like to eliminate it as a lead. Otherwise, it'll always be in the back of my mind.

> Thomas, if it's safe to do so, I'll post it here; otherwise, I'd be glad to email it to you.

Yes, you can attach the whole tar.gz file here. It's safe.

---

### Post by Pitt Stains on 2010-03-19
OK, here are the logs.

I've made two changes to my system (probably better to do one at a time if we really want to know what's going on, but I guess if the problem goes away I can undo my changes one at a time to see what triggers it).
[LIST=1]
[*]Brightside is uninstalled
[*]In System > Power Management, I've changed "Put display to sleep when inactive for:" from 15 minutes to never.
[/LIST]

Thanks again for your help.
-Pitt

---

### Post by thomasaaron on 2010-03-19
I can't open that archive. It seems to be corrupted.

---

### Post by Pitt Stains on 2010-03-23
> **thomasaaron said:**
> I can't open that archive. It seems to be corrupted.

Somehow I missed your response, Thomas -- sorry about that.

Something about gzipping the tar made it go screwy, but the original tar (attached) is readable.

Also, I just confirmed that the problem persists despite the measures I've taken:

> **Pitt Stains said:**
> 
   1. Brightside is uninstalled
   2. In System > Power Management, I've changed "Put display to sleep when inactive for:" from 15 minutes to never.


Thanks for your continued assistance.

---

### Post by thomasaaron on 2010-03-23
Well, I see two interesting log entries.


```
Mar 18 12:16:44 red5 kernel: [11794.318265] nautilus[9184]: segfault at 7fb555350960 ip
```

```
Mar 18 12:37:45 red5 kernel: [13055.047306] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
```

The first is nautilus crashing. The second is a filesystem problem.

Open System > Admin > System Monitor > Filesystems and see if any of your partitions are full.

If they are, empty your trash can and reboot. If that doesn't fix it, we'll look at expanding the partition in question.

If they are not full, let's run fsck from a live CD on your partitions. Here are instructions...

> -------------------------------------------------------
To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partition layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them. 

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.

It could also mean that you have a faulty hard drive. However, this is pretty rare, and it is better to try re-imaging the machine first.
------------------------------------------------------

---

### Post by Pitt Stains on 2010-03-23
Any idea what would make Nautilus crash?

My partitions are fine.  The fullest one is at 66%.

I don't have a live disk with me, so I'll have to wait until tonight or tomorrow to do the fsck.  It's weird that the warning doesn't specify which partition it's referring to... Also, periodically Ubuntu will perform a regularly scheduled scan on a partition or two on boot up.  Could this warning just be a notice that the internal counter has reached its magic number and that the partition will be scanned during the next boot?

---

### Post by thomasaaron on 2010-03-23
Possibly, but...

Since Nautilus has to browse the filesystem for files, it makes sense that a filesystem error could cause it to segfault. And nautilus segfaulting leads me to belive this has nothing to do with the automatic fsck.

Let's try to get this one cleared up to see if it fixes the original problem. If, after running fsck from a live CD, the problem recurs, please capture another set of logs (and the time of the freeze), and I'll have another look.

Please send another set of logs (along with the exact time of the freeze) the next time the error occurs.

---

### Post by satsujinka on 2010-03-23
If fscking the filesystems doesn't work you could try replacing nautilus with thunar or pcmanfm. If the crash continues, then it may be time to try upgrading. Alternately, you could see if you have the same problem in lxde or xfce.

---

### Post by Pitt Stains on 2010-03-25
Here are the results of fsck from a Live CD.  I've also attached a screenshot of gparted.

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 208632/500960 files, 1276970/2000084 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda2
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda5: clean, 14573/250480 files, 495136/1000038 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I should probably add that sda1 mounts to /, sda2 is my swap partition, and sda5 mounts to /home. sda4 is an unused partition, set aside in case I ever feel like installing another OS on its own partition.  sda6 is a TrueCrypt drive.

---

### Post by thomasaaron on 2010-03-25
OK, I think the problem might be that sda5 is WAY too small. It is only 1.93 GB, and 1.89 of that is used. So it only has about 41 MB of memory left. Doesn't take much to fill that up -- a song, or a couple of pictures.

You probably should start by booting from a live CD, and then going to System > Admin > Partition Editor, and then expanding that home partition by quite a bit.

---

### Post by Pitt Stains on 2010-03-25
> **thomasaaron said:**
> OK, I think the problem might be that sda5 is WAY too small. It is only 1.93 GB, and 1.89 of that is used. So it only has about 41 MB of memory left. Doesn't take much to fill that up -- a song, or a couple of pictures.

You probably should start by booting from a live CD, and then going to System > Admin > Partition Editor, and then expanding that home partition by quite a bit.

Actually, gparted reports sda5 is 3.81 GB, and of that only 1.89 GB is used, so about 1.93 GB is available.  But most of the folders that would eat up space in the home directory -- and anything personal or sensitive -- are actually just symlinked to the TrueCrypt volume (sda6).  For example, Music, Videos, Documents, .ssh and other folders are just symlinks on sda5; the real content is on sda6.

Any other thoughts?

---

### Post by thomasaaron on 2010-03-26
> Actually, gparted reports sda5 is 3.81 GB, and of that only 1.89 GB is used, so about 1.93 GB is available. 

Oops! Right you are. Sorry about that.

Another idea: Do you have screensaver selection set to random, or are you using a particular screensaver. Could you try "antspotlight" and see if you get the same results?

---

### Post by Pitt Stains on 2010-03-26
> **thomasaaron said:**
> Another idea: Do you have screensaver selection set to random, or are you using a particular screensaver.

Yeah, I have it set to random.  I've changed the setting per your recommendation.  I'll give it a few days to see if that makes any difference.  As you can see from this thread, I get the crashes once or twice a week, so it may be a few days before I have anything to report.

---

