---
title: "smallest live cd that supports mp3s?"
date: 2006-03-24
forum: The Cafe
---

### Post by magomago on 2006-03-24
I need one...on all the machines at my lab except for the one i use (which i can't play music on...no sound) are all password locked in windows.  I need to play some music to help pass some time (long story...just imagine 10 hours a day in front of a pc doing imaging work alone, i'll die if i don't get some other kind of stimulation) and I figure to bypass it by using a live CD (bios is accessible to switch to boot on cdrom if i need to)

I just need to know if there is a live CD, that is as small as possible that comes with mp3 support :)  my first shit if a 6pm-3am so if anyone knows anything i'd apprecaite it :D

---

### Post by Zimmer on 2006-03-24
[http://damnsmalllinux.org/applications.html](http://damnsmalllinux.org/applications.html)
DSL, would appear to come ready with mp3 support.

---

### Post by Randomskk on 2006-03-24
Yeah, Damn Small Linux has MP3 support built in, and can read from USB keys or network - but note that a live CD can't play an audio CD unless you have two CD drives :P
I just installed DSL to the hard disk of one of the school computers for MP3 and parallel port control in fact :D

---

### Post by magomago on 2006-03-24
i can't take the cdrom out? ><

is there a way to load music onto it then?  I only have 1 cd drive...and i don't have a thumbdrive

perhaps build a bootable drive?  or what about a small distro that loads everything into memory so i CAN take out the cdrom?  if DSL was only 50 they might as well give an option to load it into memory

---

### Post by Zimmer on 2006-03-24
It appears you can load it to RAM, if you have 128mb, with the toram option, but I have not tried that.
[http://damnsmalllinux.org/wiki/index.php/Cheat_Codes](http://damnsmalllinux.org/wiki/index.php/Cheat_Codes)

---

### Post by aysiu on 2006-03-24
You can install DSL to a pen drive or USB key.

---

### Post by zachtib on 2006-03-24
[QUOTE=magomago]i can't take the cdrom out? ><

is there a way to load music onto it then?  I only have 1 cd drive...and i don't have a thumbdrive

perhaps build a bootable drive?  or what about a small distro that loads everything into memory so i CAN take out the cdrom?  if DSL was only 50 they might as well give an option to load it into memory[/QUOTE]

DSL is ony like ~50mb.
you should be able to extract the iso, fill up the folder with music, bringing the total size of the folder you extracted to under 700mb, then burn the contents of that folder.

---

### Post by magomago on 2006-03-24
how can i ensure it is still bootable though?

---

### Post by Antoine.L on 2006-03-24
You could try building a custom amaroK live CD with your mp3s on it: [linky](http://amaroklive.com/index.php?page_id=110&language=en)

If the default live cd doesn't contain mp3 support, it may be tricky to add it, but it can be done: [painfull remastering process](http://amarok.kde.org/amarokwiki/index.php/AmaroK_Live#How_To_Remaster)

---

### Post by zachtib on 2006-03-24
[QUOTE=magomago]how can i ensure it is still bootable though?[/QUOTE]

I'm honestly not quite sure.  I would think so, but I can't guarantee anything.

---

### Post by ferebee on 2006-03-25
[QUOTE=Randomskk]Yeah, Damn Small Linux has MP3 support built in, and can read from USB keys or network - but note that a live CD can't play an audio CD unless you have two CD drives :P
I just installed DSL to the hard disk of one of the school computers for MP3 and parallel port control in fact :D[/QUOTE]

If you've got more than 128mb ram, Puppy Linux will load entirely to
RAM and then let you take the liveCD out of the drive. I supports mp3s
out of the box too.

---

### Post by zachtib on 2006-03-25
[QUOTE=ferebee]If you've got more than 128mb ram, Puppy Linux will load entirely to
RAM and then let you take the liveCD out of the drive. I supports mp3s
out of the box too.[/QUOTE]

actually, if burnt to a cd-rw, puppy linux can save its state to the disk, so you could add mp3s after burning it

---

### Post by mcduck on 2006-03-25
If all you need is mp3-support, the Geexbox is your thing. And it's only 6,3MB :D

It's a Linux/mplayer-based distro for media center use, supporting video, photos and audio playing from hard disk, CD's, DVD's, network streams or even DVB. It also supports IR control, joystic control and TV output, and if you need more, it's easy to customize.. You can add codecs, music, movies, custom art or photos as much as you want to fill your disk. (and it loads itself to RAM so you can swap the disk if you want.)

Take a look: [http://geexbox.org/en/index.html]("http://geexbox.org/en/index.html")

(I love it, I always carry it on a small CD in my wallet so I can play music on any computer anywhere)

---

