---
title: "MP3 playlists not in order"
date: 2013-01-04
forum: The Cafe
---

### Post by Swagman on 2013-01-04
I have been having trouble with MP3’s not in order on my Pioneer head unit.

 I've  had to copy the files one at a time if I wanted them in to play in turn on my playlist

Turns out this isn’t limited to just Pioneer. Here’s an explanation I found...

> 
Problem: Many MP3 players that are based on USB flash drives don't allow you to sort the MP3 files in the order you want to listen to them. 

Instead they play the MP3 files in the order they find them; usually the order you copied them to the flash drive. How do we re-order the files?


Background: In the old DOS days Norton Utilities provided a tool called DS (Directory Sort) that would re-arrange the order of files in the FAT (File Allocation Table) directory structure. This was useful because many programs would only display or process files in the order they found them; they wouldn't allow you to sort the files. With the advent of Windows the need for DS was reduced as Windows usually sorts filenames before displaying them (i.e. in Explorer or the Windows file selector dialog box).

Many modern MP3 players are based on USB flash drives (i.e. Creative's MuVo range of MP3 players). These devices don't allow you to sort the MP3 files in the order you want to listen to them. 

Instead they play the MP3 files in the order they find them; usually the order you copied them to the flash drive. Unfortunately if you select a bunch of files in Windows' Explorer and copy them to your MP3 player, they don't always copy in alphabetical order (even if you have told Explorer to display the files alphabetically). And of course you may want to add new MP3 files at a latter date, which will result in them being added to the end of the directory.

Norton's old DS utilities was designed for FAT16 drives and so won't work with newer drives that are FAT32. The addition of long file names (VFAT) further complicates matters. Duncan Murdoch wrote a utility called LFNSORT which went some way to addressing the problems with Norton's DS not working with newer file systems, but unfortunately LFNSORT doesn't work with newer versions of Windows (i.e. Windows 2000 and later).
Early versions of the Windows Defrag tool would also re-sort the directory, but this ability seems to have been removed from newer versions.


Ok.. So this wasn't with USB but with SD Card but the problem still exists.
I was pointed to **DriveSort** but it is a Windows app.

I have Wine & Crossover installed but sod all happened when I tried to run it !

So I was forced to sully myself and use a Windows machine (I'm now going to have to go round proclaiming "Unclean, Unclean" for a month of Sundays) to use this program.

It works !!

So, in future, Rather than contaminate my delicate little Pysch Is there a linux equivalent ?

I wish I could code coz I'd have a crack at it myself.


[http://www.anerty.net/software/file/DriveSort/](http://www.anerty.net/software/file/DriveSort/)

---

### Post by CharlesA on 2013-01-04
Interesting.

I haven't tried playlists on my car stereo (not even sure if the one I have supports it), but I have noticed it doesn't pick up on the Artist/Song tags inside the MP3 files. Sometimes it will find it and sometimes it will just play it based off the name of the MP3.

---

### Post by odiseo77 on 2013-01-04
I don't use playlists, but I have noticed the behavior described in the OP  using a cheap mp3 device when I copied the files manually (through a file manager). When doing so, the files were played not alphabetically (by tag or by filename), but in the order they were copied to the device. I later found that if I used Rhythmbox, the files were played by album order, which was better. So, maybe if Rhythmbox has a playlist option, it could work?

@ CharlesA: I had a similar issue when copying mp3's to my Sansa Fuze. Whilst Amarok displayed the tags properly, the Fuze would only display "Unknown artist" for some albums, which was tedious. So, someone in another forum suggested it could be due to a tag version issue: Apparently, Amarok uses tag version 2.4 and the Sansa Fuze, as well as Windows Media Player use tag version 2.3, so, some tags wouldn't display properly on these if they were saved using tag V. 2.4. The solution was to use a program named EasyTag (it's Linux-based), changing the preferences to use tag version 2.3 and rewrite the tags to my collection.

Regards.

---

### Post by CharlesA on 2013-01-04
> **odiseo77 said:**
> 
@ CharlesA: I had a similar issue when copying mp3's to my Sansa Fuze. Whilst Amarok displayed the tags properly, the Fuze would only display "Unknown artist" for some albums, which was tedious. So, someone in another forum suggested it could be due to a tag version issue: Apparently, Amarok uses tag version 2.4 and the Sansa Fuze, as well as Windows Media Player use tag version 2.3, so, some tags wouldn't display properly on these if they were saved using tag V. 2.4. The solution was to use a program named EasyTag (it's Linux-based), changing the preferences to use tag version 2.3 and rewrite the tags to my collection.

Thanks for that. The player in question is a Pioneer head unit and Winamp displays the tags fine - some of the MP3s are ones I have gotten from Amazon and others are ones I have ripped myself. It is quite odd.

I'll see if that makes any difference.

---

### Post by LADmaticCA on 2013-01-04
I use fatsort in the repos to put my mp3's in order. But I don't deal with playlists, just files on the flash drive.

---

### Post by cariboo on 2013-01-04
I've extensivly tested usb playback on several different head units including:

[LIST=1]
[*]Sony
[*]Pioneer
[*]JVC
[*]Panasonic
[*]Dual
[/LIST]

and I almost always get surprised as to the playback order, I've even gone so far as to rename tracks (try that with over 350 tracks) to see if I could get them to playback in the order I want. The quote from Swagman makes sense, as this is what I'm seeing.

I'm going to give LADmaticCA's suggestion a try in the coming weeks.

---

### Post by CharlesA on 2013-01-04
Thanks for confirming, cariboo!

What a pain!

---

### Post by Swagman on 2013-01-05
> **LADmaticCA said:**
> I use fatsort in the repos to put my mp3's in order. But I don't deal with playlists, just files on the flash drive.

Thanks. Well that looks like it will do the job but is there a GUI front end available ?

The reason for that is that if I'm going to recommend that program on a car forum then the first gripe I'm going to get will be something like

"Stoopid Linux still stuck in the dark ages"

So according to fatsort - h the command I would require would be

```
fatsort /dev/sda* -c -n -d dir
```

To ignore case, sort natural order (the files  are already named 001-Toyah - Jungles of jupiter.mp3 etc and the directory ?

---

### Post by CharlesA on 2013-01-05
I don't see anything about a GUI mentioned on their homepage, and it looks like it only runs on *nix.. soo....

[http://fatsort.sourceforge.net/](http://fatsort.sourceforge.net/)

---

### Post by Swagman on 2013-01-08
I wonder if I chuck £50 at my mate whether he'll code a Gui for it in his spare time ?

---

