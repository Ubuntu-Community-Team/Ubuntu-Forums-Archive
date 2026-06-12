---
title: "DVDfab"
date: 2010-01-20
forum: Wine
---

### Post by handy on 2010-01-20
I spent a good deal of time yesterday trying to backup a DVD onto my HDD.  I tried & failed using both DVDShrink & Handbrake under Arch. So then I booted into OS X, & tried with something that uses VLCs inbuilt abilities & also with MacTheRipper (current build), I used a couple of other Mac utilities for the job & they all failed too.

This sent me researching, & I found that Sony's arccos(2) protection system was what was wasting my day. 

Eventually I downloaded the shareware, windows software called [**_DVDfab_**]("http://www.dvdfab.com/free.htm"), which handles all forms of DVD protection & some of those for Blue-ray too, amongst other things.

It worked in DVD to DVD mode, in 32 min's, compressing DVD-9 format to DVD-5 as it went.  Doing a beautiful job.

After all these years, DVDShrink has finally been toppled from its throne. For me anyway.

DVDfab is probably old news for many of you, but after the day I had yesterday, I had to promote it here, in the hope of saving someone else from wasting their time trying to backup a DVD, when they needn't have. :)

It installed in Wine with no problems, there were some error messages in the Terminal, but they were inconsequential. 
DVDfab is really easy to use, requiring no reading of manuals or the like.

---

### Post by stinger30au on 2010-01-20
went down this route yonks ago...

but i since discovered a much better solution, for free with ubuntu

first off, make sure you can play a dvd with the moive player on your pc first with the app "movie player".
if you cant play movies with this, then oyu need to install the codecs for it or you will never rip a dvd properly.

then to rip the dvd install a program called

k9copy

k9copy will allow you to rip/shrink in one hit. it has copied every disc i have ever thrown at it

---

### Post by hemimaniac on 2010-01-20
+1 for K9Copy, I also have used dvd9 to 5

---

### Post by JohnAStebbins on 2010-01-21
> I found that Sony's arccos(2) protection system was what was wasting my day. 
Handbrake handles Arccos if you are using the latest release (0.9.4) or the development [snapshot]("http://forum.handbrake.fr/viewtopic.php?f=6&t=13969") and you enable dvdnav in the preferences.

---

### Post by handy on 2010-01-24
> **stinger30au said:**
> went down this route yonks ago...

but i since discovered a much better solution, for free with ubuntu

first off, make sure you can play a dvd with the moive player on your pc first with the app "movie player".
if you cant play movies with this, then oyu need to install the codecs for it or you will never rip a dvd properly.

then to rip the dvd install a program called

k9copy

k9copy will allow you to rip/shrink in one hit. it has copied every disc i have ever thrown at it

I have found k9copy to be unreliable when dealing with large numbers of disks.  So I use neroLinux instead, which has never failed me.

> **JohnAStebbins said:**
> Handbrake handles Arccos if you are using the latest release (0.9.4) or the development [snapshot]("http://forum.handbrake.fr/viewtopic.php?f=6&t=13969") and you enable dvdnav in the preferences.

I use HandbrakeCLI, which has not been upgraded to 0.9.4, & so would not handle arcoss2.

***[Edit:]** Though if I'd thought of it I probably would have installed the GUI version of Handbrake 0.9.4 on OS X, which would have solved the problem. *

---

