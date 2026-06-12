---
title: "I can't believe..."
date: 2008-03-14
forum: Testimonials &amp; Experiences
---

### Post by sparkerjc on 2008-03-14
There have been several posts regarding this general topic, but I want to give my opinion.

I am new to Ubuntu from Vista. I have a Dell Inspiron 1520 with two hard drives that I swap out to switch between Ubuntu and vista so I don't wreck my data... like I have before...

Anyway I switch the drives out often right now, but it is becoming less frequent as I become accustomed to Ubuntu. A few days ago I turned on my computer and it just sits there with a black screen and one of these "_" flashing in the top left corner and the HD light is Solid. First thought: Great, hard drive is crashed... (I was rebooting because I was playing around with all settings and generally messing the system) After about 30-45 seconds of "_" flashing in the corner I hold down the power button to kill the machine and try it again, same thing. I go into the "Recovery mode" and it says something to the effect of "This partition has been mounted 21 times and a disk check has been forced" I realized that it was checking the disk the first two times and left me clueless as to what was going on. Annoying.

I went on my way for the next 21 "mounts" and forgot about it. It happened again yesterday and I killed again right before I realized that was probably what it was again, even so I went to recovery mode so I could watch the status.

As a new user I cannot believe this is how it is set up.

No warning
No cancel
No progress bar
"_"

If Ubuntu is supposed to win windows users things like this to be more obvious what is going on. We aren't the quickest breed, for sure, but gimme a break!

Anyway like I said this has been mentioned before so don't yell at me... Thanks for listening.

---

### Post by Perpetual on 2008-03-14
My understanding is that 8.04, Hardy Heron, shows a status bar and an 'escape'.  However, on my Gutsy install, there is a message during boot that says checking disk.  Have you changed your usplash settings or set 'quiet' mode when booting?

---

### Post by sumguy231 on 2008-03-14
On my system, the splash screen always quits and displays the progress of that, even on a normal boot. Sounds like something is misconfigured on your system. But the really good news is that in Ubuntu 8.04, the splash screen can display a loading bar for the progress of the disk check, and even let you cancel it.

---

### Post by spiderbatdad on 2008-03-14
You are correct to assume that is not normal behavior. This is the first thread I've seen with this issue. Perhaps an answer will be forthcoming.

---

### Post by mgranet on 2008-03-14
It shows me the fsck progress in Kubuntu. It might be a Gnome thing?

---

### Post by sparkerjc on 2008-03-14
I am using a fresh install of 7.10, which I have installed twice.

I have messed with display settings and my xorg.conf is a huge mess, although everything displays properly and I have sweet desktop effects...

I think, however the first time it did this was on my first install which I ruined by playing with drivers and such leading to a new install, and it has done the same thing this time. Maybe I messed up the same thing twice? I wanted to get used to it and play around with all the stuff to know what not to do so I can have 8.04 run smoothly with a clean install.

At least it is good to know it isn't supposed to be like that, which was my biggest worry.

---

### Post by Flying caveman on 2008-03-14
> To change the number of times a ext2/etx3 partition is mounted, after which a file system check (fsck) is performed use -c option followed by the number.

For example, the following command changes it to 100 (fsck will be triggered after filesystem is mounted for the 100th time):

$ sudo tune2fs -c 100 /dev/hda1

To check the value (called "Maximum mount count"), as well as other parameters:

$ tune2fs -l /dev/hda1

Replace /dev/hda1 with the ext2/ext3 partition your wish to set the value for.

from [http://ubuntuforums.org/showthread.php?t=11203](http://ubuntuforums.org/showthread.php?t=11203)

---

### Post by Tyke91 on 2008-03-14
gnome and kde have not even been started yet at the point where it would be running fsck, so i don't think that's the problem (besides, i use gnome and i get the usual disk check messages)

my guess is that somewhere in your ubuntu dabbling, you changed a config file and now your boot screen doesn't give you verbose output.

---

### Post by SunnyRabbiera on 2008-03-14
> **mgranet said:**
> It shows me the fsck progress in Kubuntu. It might be a Gnome thing?

I doubt it, its probably a ubuntu thing as i know kubuntu modifies some things.

---

### Post by sparkerjc on 2008-03-14
By the way-

Thanks for the overwhelming response. I have used the forum for several issues and am always annoyed by the "OMG it has been 2 hours and no reply u sux im going back to windows! and plz plz plz someone help me dis jus sux u no? fix my crap!"

Also where is there info on all the upgrades in 8.04 (I can never remember the names)?

---

### Post by sparkerjc on 2008-03-14
> **Flying caveman said:**
> from [http://ubuntuforums.org/showthread.php?t=11203](http://ubuntuforums.org/showthread.php?t=11203)

Thanks, but like I said I have already read the other posts about the issue.

---

### Post by ramjet_1953 on 2008-03-15
Follow this link for a solution to your problem:

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

Regards,
Roger 8)

---

### Post by Sef on 2008-03-15
Moved to Ubuntu Testimonials & Experiences

---

