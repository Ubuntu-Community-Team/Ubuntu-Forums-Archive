---
title: "I was told to format hdd to ntfs in windows, not Ubuntu, so how do I?"
date: 2008-08-29
forum: Windows
---

### Post by PsychedelicWonders on 2008-08-29
Alright currently I have a hdd that was formatted to ext3 in ubuntu, mounted and successfully used in Ubuntu.

Now it never registered under my computer in windows first and fore most.

So how do I get windows to recongnize this hdd?

And how do I go about formating it all to ntfs?

---

### Post by karellen on 2008-08-29
to access your ext3 partition in Windows, you may find this useful:
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) and [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)
if you want to format your Linux installation, simply use your XP/Vista install disk and format the ext3 partition to ntfs. acronis disk director suite does a good job too, without needing restart

---

### Post by SunnyRabbiera on 2008-08-29
Right, that usually works from what I understand.

---

### Post by TenPlus1 on 2008-08-29
This is what I use:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It's a free driver that lets you mount Ext2/3 partitions and use them in Windows...

---

### Post by PsychedelicWonders on 2008-08-29
So whats better ext3 of ntfs for windows?

I dont know which way to go as there are both options.

It is already ext3 right now.

---

### Post by fiddledd on 2008-08-29
> **PsychedelicWonders said:**
> So whats better ext3 of ntfs for windows?

I dont know which way to go as there are both options.

It is already ext3 right now.

As as been said by others, you can get a driver for Windows so that it recognises ext3. But if the drive is going to be used mainly in Windows, then I would format it to NTFS. You can use Windows to format it to NTFS, but remember to transfer any files off the drive first.

---

### Post by PsychedelicWonders on 2008-08-29
I plan to use this primarily in Ubuntu.  like 98% of the time.

But I want full access with no problems in both systems.

I will be using an iphone eventually, so I need all media to be easily readable.

What should i do>?

---

### Post by az on 2008-08-29
> **PsychedelicWonders said:**
> I plan to use this primarily in Ubuntu.  like 98% of the time.

But I want full access with no problems in both systems.

I will be using an iphone eventually, so I need all media to be easily readable.

What should i do>?

Format it to NTFS.

---

### Post by tangibleorange on 2008-08-29
there is pretty good ntfs read/write support in ubuntu these days. i'd reccomend NTFS, but you could use fat32. trouble with fat32 is the 4GB max file size and big fragmentation that occurs with frequent writing.

---

### Post by PsychedelicWonders on 2008-08-29
> **az said:**
> Format it to NTFS.

alright and I should format this ntfs in windows then right?

Where do I go in windows to format this?

Well first I have to have windows find it...

---

### Post by tangibleorange on 2008-08-29
> **PsychedelicWonders said:**
> alright and I should format this ntfs in windows then right?

Where do I go in windows to format this?

Well first I have to have windows find it...

if you're using vista, you right click on Computer in the Start Menu, then manage, and then disk editor or something. then just delete the ext3 partition and format it to ntfs.

otherwise you need to use an ubuntu live cd - other versions of windows don't allow disk manipulation from the disk editor.

---

### Post by karellen on 2008-08-29
this should do the trick if you don't have Windows installed
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by PsychedelicWonders on 2008-08-29
I have windows XP Pro installed.

So what/where do I do to format to ntfs?

---

### Post by karellen on 2008-08-29
> **PsychedelicWonders said:**
> I have windows XP Pro installed.

So what/where do I do to format to ntfs?

then use something like Acronis Disk Director Suite or Partition Magic to view and format your ext3 partition to ntfs. or, if you prefer, download GParted Live CD, burn the iso, boot from the cd and again, reformat your ext3 drive to ntfs

---

### Post by PsychedelicWonders on 2008-08-29
is partition magick already on windows?

Or do I have to download it?

I do have a new version of 32 I have to burn, but everyone keeps telling me to format in windows?

---

### Post by karellen on 2008-08-30
> **PsychedelicWonders said:**
> is partition magick already on windows?

Or do I have to download it?

I do have a new version of 32 I have to burn, but everyone keeps telling me to format in windows?

I don't really understand what you exactly want to do. both Partition Magic and Acronis Disk Suite costs money, so if you want something free that does the job, go for the GParted Live CD. just follow the links or search on Google

---

### Post by PsychedelicWonders on 2008-08-30
What I am trying to do is take my ext3 hdd and format it to ntfs so that I am able to easily access files on a dual boot, using Ubuntu 98% of the time and XP Pro for the rest.

But i have 34 differenet peole suggesting 35 different things.

So I'm just really confused right now.

---

### Post by karellen on 2008-08-30
> **PsychedelicWonders said:**
> What I am trying to do is take my ext3 hdd and format it to ntfs so that I am able to easily access files on a dual boot, using Ubuntu 98% of the time and XP Pro for the rest.

But i have 34 differenet peole suggesting 35 different things.

So I'm just really confused right now.

1. if you format your ext3 partition you won't be able to use Ubuntu. Linux doesn't run on ntfs
2. to format your ext3 partition to ntfs, use:
              a) Gparted Live CD;
              b) your XP install disk;
        if you want something free or something you already posses

---

### Post by PsychedelicWonders on 2008-08-30
> **karellen said:**
> 1. if you format your ext3 partition you won't be able to use Ubuntu. Linux doesn't run on ntfs
2. to format your ext3 partition to ntfs, use:
              a) Gparted Live CD;
              b) your XP install disk;
        if you want something free or something you already posses

I am running my dual boot OS on a separate hdd than I am actually trying to format.

So if I format to ntfs, is Ubuntu going to have problems accessing and reading the data stored on it?

I will format using the live cd, but want to make sure ntfs will be readable in ubuntu.

---

### Post by ugm6hr on 2008-08-30
> **PsychedelicWonders said:**
> But i have 34 differenet peole suggesting 35 different things.

Don't want to add to your problems of confusion... but

If you are using Ubuntu 98% of the time, and it is already ext3, why not just use fs-driver in Windows?

As long as you shut down Windows whenever you use it (rather than Suspend or crash etc), it will not cause any problems.  I've been using it ever since I created a /home partition instead of a separate "data" partition to share between OS.  Although I only use MS infrequently too.

---

### Post by karellen on 2008-08-30
> **PsychedelicWonders said:**
> I am running my dual boot OS on a separate hdd than I am actually trying to format.

So if I format to ntfs, is Ubuntu going to have problems accessing and reading the data stored on it?

I will format using the live cd, but want to make sure ntfs will be readable in ubuntu.

Ubuntu read ntfs just fine :), I never had a problem with a Linux distro reading and writing on my ntfs partitions (after mounting them, of course). I dual boot Vista and Mandriva and I have 2 ntfs partitions and 2 ext3 partitions on a single hdd

---

### Post by PsychedelicWonders on 2008-08-30
Alright thats final.

I am going to use the Ubuntu Live CD to reformat this drive to ntfs.

Now what program should I use in Ubuntu to burn an .iso?

Do I need to mount or unmount my hdd before I can format it?

---

