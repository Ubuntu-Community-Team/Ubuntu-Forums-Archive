---
title: "[SOLVED] Shaken Confidence"
date: 2008-11-05
forum: Testimonials &amp; Experiences
---

### Post by ericesque on 2008-11-05
Boy, what a frustrating evening.  Let me preface by saying that this is not a hate on Ubuntu thread. Just one of those experiences that you have to share.

My wife decided on a whim to hibernate my desktop install of 8.04.  This is a solid install that I was planning on hanging onto instead of upgrading to 8.10.  

Well when I went to turn the PC back on I was greeted with a Grub error 17.  Completely locked out of my system.

I've read about messing with BIOS settings - didn't work. Spent a couple hours between 1am and 3am trying to get anywhere with a live distro (Ubuntu 8.04 live never reaches GUI, DSL doesn't seem to like fdisk, puppy finally informed me that Grub can't tell what filesystem my linux partitions are using).

You know, I don't mind having to work in order to maintain a stable system. But this...?  This is downright disheartening.  Something as simple as hibernate can cost me hours... makes me wonder if I'll be stuck with XP forever if I want a stable OS :(

I'll be trying an 8.10 disk to reinstall grub tomorrow but I have a feeling it'll turn into a system reinstall.  

Suggestions are welcome.  
Commiseration is appreciated.

---

### Post by hyper_ch on 2008-11-05
a simple hibernate shouldn't end up like that :( don't give up :)

---

### Post by BigSilly on 2008-11-05
[This wee disc]("http://www.supergrubdisk.org/"), has gotten me out of a load of GRUB problems in my short Linux time. It's well worth a download, and is very easy to use. I used it just the other day in fact when my Mandriva install decide to reinstall it's GRUB and erased the main Ubuntu entry.

Give it a try. I used the 0977 .iso and burnt it to disk. As a Linux user your BIOS will be set to boot from disc first I would imagine. Good luck.

---

### Post by ericesque on 2008-11-05
I remembered this morning (having gotten a couple hours of sleep) that
I did an update yesterday in which I received a promt about whether I
wanted to update my menu.lst.  Gave me the option to use the package
maintainer's version or keep my current version.  Thinking- hey, don't
fix what ain't broke, I selected to keep mine.

I'm HOPING that this was the cause of my headache and that reinstalling 
GRUB will fix things. Fingers crossed here...

---

### Post by ericesque on 2008-11-05
> **BigSilly said:**
> [This wee disc]("http://www.supergrubdisk.org/"), has gotten me out of a load of GRUB problems in my short Linux time. It's well worth a download, and is very easy to use. I used it just the other day in fact when my Mandriva install decide to reinstall it's GRUB and erased the main Ubuntu entry.

Give it a try. I used the 0977 .iso and burnt it to disk. As a Linux user your BIOS will be set to boot from disc first I would imagine. Good luck.

I messed with super grub last time I managed to screw it up.  It didn't
seem to offer much help. It did get me into the system, but I was unable
to get a functional boot loader to stick. 

Maybe my next project will be to make GRUB more accessible to end users in a clear and safe manner.

---

### Post by ericesque on 2008-11-06
Well I got past the GRUB 17 error just to run into the following error during boot:

init-run : sbin/init no such file or directory found.

Looked around for a solution, tried some things - no dice.  Finally resolved to do a full reinstall of 8.10 -- but oh wait, the live cd dumps me to Busybox.  

Ubuntu, you have let me down severely the past few days. At this point, Windows 7 can't get here fast enough!

---

### Post by WaeV on 2008-11-06
From a live CD, enter the following in a terminal:

**grub** You may need sudo for this one.  A prompt will appear.
**find /boot/grub/stage1**
**setup (hd0)** (If hd0 is where grub was found)
**quit**

Reboot and you're done.

---

### Post by ericesque on 2008-11-07
> **WaeV said:**
> From a live CD, enter the following in a terminal:

**grub** You may need sudo for this one.  A prompt will appear.
**find /boot/grub/stage1**
**setup (hd0)** (If hd0 is where grub was found)
**quit**

Reboot and you're done.

Thanks for the reply WaeV.  I had already tried that but it didn't work.  Running fsck to repair the file system allowed GRUB to recognize the partition as ext3 (cleared up the GRUB 17 error) and like you, I thought reinstalling GRUB would allow me to boot.  But since the boot was getting hung up on init it didn't really have anything to do with GRUB.

Glad to report that I did finally get it working.  I ended up installing over top of the previous install without formatting any of the partitions.  Ubuntu handled it a lot more elegantly than XP ever did too! My desktop was 100% the way I left it.  My theme was still applied and all my settings, bookmarks, and preferences for default packages were still intact -- gotta love separate home partitions!  I obviously had to catch up on some updates and install any non-default packages, but all in all, I was impressed!

---

### Post by ranch hand on 2008-11-08
Glad you got it working.  I have been watching this thread.

The reason for watching was that I was born at Sparow hospital at 10:15 on 2-8-52.  Always like to see things go right for folks in the Lansing area.

---

### Post by ericesque on 2008-11-09
> **ranch hand said:**
> Always like to see things go right for folks in the Lansing area.

As a matter of fact, so do I :D

---

