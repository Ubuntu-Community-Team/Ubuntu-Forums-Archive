---
title: "Strange USB Disk Problem"
date: 2017-11-28
forum: Windows
---

### Post by AlexHudghton on 2017-11-28
Background  - In my last house I used a Ubuntu 16.0.4 desktop as a home theatre - 3 1TB disks to hold lots of films & TV & music. The desktop was in a cupboard to suppress fan noise. New house - no cupboard so I have changed over to a laptop (at the moment Windows 10) and a 3TB USB disk.

Problem:

I copied the films / TV over from the desktop disks onto the USB drive (plugged disk into desktop to do this) and everything works well.

Initially, I was using a Ubuntu 16.0.4 laptop to test out the idea of doing it this way and all went well.

I then swapped to the windows laptop and again the film / TV aspect was all fine

Today I repeated the operation with the music files. There is about 2.5GB of data, over 8000 tracks and they copied over to the USB drive without a problem. 

Plugging the drive into the windows system I cannot see the music file directory. I can see all the film directories / files.

If the disk is connected to an Ubuntu system I can see everything.

The disk is formatted as NTFS

Any ideas welcomed.

---

### Post by howefield on 2017-11-28
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2017-11-28
What type of music files, MP3, OGG, WAV, etc.

Actually, given that you cannot see the files from your proprietary windows operating system using a proprietary windows filesystem (NTFS), I think your question would more logically be posed at a windows forum or the support.microsoft site.  Might get lucky and someone here will have a suggestion.

---

### Post by coffeecat on 2017-11-28
A long shot this, but worth checking. Please post the name of the music file directory and some sample filenames of the music files.

There are certain characters that are forbidden for filenames in Windows and in Windows filesystems: ~ # % & * ' { } \ : < > / ? + | " and maybe some others. However, if you save files with filenames with forbidden characters to NTFS from a Linux system, you can see and open them OK from your Linux system, but Windows gets confused.

---

### Post by SuperFreak on 2017-11-28
> **coffeecat said:**
> A long shot this, but worth checking. Please post the name of the music file directory and some sample filenames of the music files.

There are certain characters that are forbidden for filenames in Windows and in Windows filesystems: ~ # % & * ' { } \ : < > / ? + | " and maybe some others. However, if you save files with filenames with forbidden characters to NTFS from a Linux system, you can see and open them OK from your Linux system, but Windows gets confused.

also if there is a space before or after the filename before the extension

---

### Post by AlexHudghton on 2017-11-28
Thanks for all the replies.

The directory name is "Music Collection" - no forbidden characters there. The directories under the master are similar - "Black Sabbath" "The Chieftains" "Moody Blues" etc.

filenames are track title with  .mp3 .mp4

I just tried a quick experiment.

Connected to a Ubuntu laptop the directory and its files exists and I can see everything. (slight error in the size I gave above - it's actually 33GB)

Move the drive over to the Windows 10 laptop and I can't see the top level "Music Collection" directory.

I can create a directory called "Music"

I move back to the Ubuntu laptop intending to copy some files into this new directory, but "Music" has gone and "Music Collection" is back and [B]it's empty!

[/B]

---

### Post by coffeecat on 2017-11-28
This could be your problem:

> **AlexHudghton said:**
> Windows 10

By default, Windows 10 doesn't shut down, but goes into hibernation or whatever when you think it has shutdown. If a filesystem it has accessed has changed while it has been in hibernation mode - such as being written to from Ubuntu - it will proceed to tidy it up, removing anything it thinks shouldn't be there. 

Sorry - naive explanation. I don't use Windows much at all. Someone else will be able to explain that better. You need to ensure that Windows shuts down properly before you allow it access to a NTFS filesystem you write to from Ubuntu.  

To disable hibernation, you need to disable fast startup:

[https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html](https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html)

---

### Post by AlexHudghton on 2017-12-02
After much wasting of time, i have taken the easy route.

I have brought forward my dual booting of the laptop, install Ubuntu - changed the disk to ext4 and copied over the data.

Dual-booting is another can of worms, haven't got it right yet, but I can now use the system as intended, with no M$ in sight :D

Thanks to everyone who contributed for their help

Regards

Alex

---

