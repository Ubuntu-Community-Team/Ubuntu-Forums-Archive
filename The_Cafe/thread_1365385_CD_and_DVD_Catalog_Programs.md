---
title: "CD and DVD Catalog Programs"
date: 2009-12-27
forum: The Cafe
---

### Post by bob-linux-user on 2009-12-27
Please can anyone recommend a cd catalog program? I have over 300 CD's and DVD's mostly containing data and software. I dual boot with XP and run Wincatalog Light in XP and also the Windows version of GWhwere. This shares its database with the Linux Version of Gwhwere that I run from Karmic.

What I want is a  catalog program that runs in Ubuntu, Is **FAST** (not like Gwhere) and ideally having a Windows version as well, to share the database with. I don't mind running a Windows program in WINE. (Wincatlog Light did not run in WINE last time I tried it)

?

---

### Post by jonest1 on 2009-12-27
Here are a few to get you started.

GCStar
[http://www.gcstar.org/index.en.php](http://www.gcstar.org/index.en.php)

Tellico
[http://tellico-project.org/](http://tellico-project.org/)

Ant Movie Catalog
[http://www.antp.be/software/moviecatalog/](http://www.antp.be/software/moviecatalog/)

Alexandria
[http://alexandria.rubyforge.org/](http://alexandria.rubyforge.org/)

Griffith
[http://www.griffith.cc/](http://www.griffith.cc/)

I probably forgot a couple, but this will get you on your way. 

I know that gcstar, tellico, alexandria, and griffith are in the Ubuntu software repositories.

---

### Post by ryantriplett on 2009-12-27
I know it seems simple, but have you thought about just using a spreadsheet? Maybe Google Docs so you can access it anywhere?

---

### Post by Jose Catre-Vandis on 2009-12-27
What is slow about Gwhere? I have tried all the others and keep coming back to Gwhere. I have 500 + CDs and DVDs cataloged in one file with ghwere and on my old 1.7 Athlon and with the database file stored on a lan server, its only seconds for a full search.

It is a bit finicky about mounting and unmounting DVDs when cataloging, but apart from that you already seem to have the right solution from my viewpoint, with the benefit of continuity trhough dual-boot.

---

### Post by pwnst*r on 2009-12-27
> **ryantriplett said:**
> I know it seems simple, but have you thought about just using a spreadsheet? Maybe Google Docs so you can access it anywhere?

too simple, but maybe a project if you're unemployed or something. not many people want to input upwards of 400 cd's/dvd's onto a spreadsheet.  trying to include notes and box shots would be an absolute nightmare on top of that. 

also, how often would you need access when you're not at home?  i'm guessing once every 5 years.

---

### Post by ryantriplett on 2009-12-27
> **pwnst*r said:**
> too simple, but maybe a project if you're unemployed or something. not many people want to input upwards of 400 cd's/dvd's onto a spreadsheet.  trying to include notes and box shots would be an absolute nightmare on top of that. 

also, how often would you need access when you're not at home?  i'm guessing once every 5 years.

True @ the absolute nightmare of including notes, boxshots, etc.

As far the the accessing when not at home - he states he has Windows and Linux - it would be easier than keeping up with a file (unless of course you use something like Dropbox, or perhaps a thumb drive).

---

### Post by pwnst*r on 2009-12-27
yeah, the dual OS can be a small issue, i agree - i'd be using virtualbox in seamless mode if that were the case.

Dropbox is a great idea though - i love that app.

---

### Post by bob-linux-user on 2009-12-27
Thanks to all who replied

@Jonest1
Thanks for all your suggestions but I think (correct me If I 'm wrong) that these are programs where you have to put all the data in yourself. On the two progs I mentioned at the start the basic principles are much the same. You put your CD or DVD in the computer, press a button and the PC forms an index of every filename on the disc, usually only taking a few seconds. I should have made this clearer.

@RyanTriplett
I started doing this on spreadsheet a couple of years ago . The sheer magnitude of the task made me look around for easier options.

@ Jose Catre-Vandis
This is why I say Gwhwere is slow. I have just done some speedtests:
For the same CD/DVD collection the sizes in Megabytes of the files are:
Gwhere 102.2 
Wincatalog Light 63.9

Ok, these are filesizes and not speeds. Looking at times to open catalog:
Gwhwere in ubuntu 1:10 minutes (in Windows 1:30 minutes)
Wincatalog Light(In windows of course) 15 SECONDS

Searching for the same term :
Gwhwere 8:00 minutes (In Windows 5:45 minutes)
Wincatalog Light 10 SECONDS

(I am running an Athlon XP2500 with 2 gig of RAM)

Regards to all

Bob

---

### Post by Jose Catre-Vandis on 2009-12-27
> **bob-linux-user said:**
> 
@ Jose Catre-Vandis
This is why I say Gwhwere is slow. I have just done some speedtests:
For the same CD/DVD collection the sizes in Megabytes of the files are:
Gwhere 102.2 
Wincatalog Light 63.9

Ok, these are filesizes and not speeds. Looking at times to open catalog:
Gwhwere in ubuntu 1:10 minutes (in Windows 1:30 minutes)
Wincatalog Light(In windows of course) 15 SECONDS


Odd. My catalog file is just under 10mb?

---

### Post by bob-linux-user on 2009-12-27
Here is the figures from Gwhwere (glad I didn't have to work this out myself)
Version 2 built with GWhere 0.2.3 File Size 102.25 Mb
Disks in catalog 309  Total Storage Space 443.85 Gb
Total Files 1067285 Total Used Space 438.01 Gb
Total Folders 96329  Total Free Space 5.84 Gb

Disk stats:
CD-Rom 234
HD 24
Other 51

---

### Post by fjf on 2009-12-27
I use cdcat for my files.  Fast and simple.  It is in the ubuntu repos, and there is a windows installer as well.

---

### Post by bob-linux-user on 2009-12-28
Thanks FJF. That was exactly what I was looking for. I now have to load 300+optical disks in so I can't comment on the speed yet though!

Regards

Bob

---

