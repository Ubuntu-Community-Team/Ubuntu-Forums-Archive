---
title: "xp security centre"
date: 2010-03-08
forum: The Cafe
---

### Post by Post Monkeh on 2010-03-08
i've recently been feeling quite smug reading about people moving to linux because their windows box was full of malware.
i haven't had a virus on windows in years. 

until today. i've no idea HOW it installed itself. i saw a flash in my system tray that updates were available but i ignored it because i was busy.
basically i have 2 drives on my desktop. 80 gig seperated to 3 partitons (plus 1 linux swap) and a 500 gig seperated into 3 partitons for windows & 2 for linux & linux swap.

it was sort of needed when the pc was downstairs and used by me AND other people but now there are just too many disks, so i was shifting stuff around so i could get rid of some of the partitions, and in the middle of it i started getting this xp security centre popping up telling me i was infected. i had just opened firefox, which opened loads of tabs i'd been browsing last time i'd been on windows, i'm guessing something here caused my problem. i was trying to click the windows closed (had about 9 or 10 of them) so maybe i clikced on something else by mistake

luckily i'm not too slow so i thought something was up, but it looked TOTALLY genuine , even so far as having an entry at the bottom of the windows security centre.

i'm now having to go through a whole rigmarole to get rid of the thing, just goes to show you can never be too careful.

---

### Post by Tristam Green on 2010-03-08
Xp Security Center installs through rogue links and false messages via web applets.

It's one of an entire extended family of malware applications :|

It's a pain to get rid of, for sure lol.

---

### Post by Post Monkeh on 2010-03-08
> **Tristam Green said:**
> Xp Security Center installs through rogue links and false messages via web applets.

It's one of an entire extended family of malware applications :|

It's a pain to get rid of, for sure lol.

it's actually called xp internet security on mine but i think it can call itself xp security centre too.

automatic removal tool i downloaded didn't work first time, i may have to do it a few times. such a pain.

---

### Post by Tristam Green on 2010-03-08
[http://www.bleepingcomputer.com/](http://www.bleepingcomputer.com/)

they have a huge compendium of that class of malware, and how to remove it properly.

good luck.

---

### Post by Post Monkeh on 2010-03-08
> **Tristam Green said:**
> [http://www.bleepingcomputer.com/](http://www.bleepingcomputer.com/)

they have a huge compendium of that class of malware, and how to remove it properly.

good luck.

cheers.
saw that but i've never heard of the site before so i was sure if i should trust them. i've been following the guide [here]("http://www.spyware-techie.com/xp-internet-security-removal-guide/").

and before anyone jumps on the "it's just windows" bandwagon, i don't know much about the internal workings of my OS, but since this managed to infect me through firefox, i'm guessing it's a vulnerability in firefox (or a particular website more likely) that could be exploited on any os.

---

### Post by Tristam Green on 2010-03-08
> **Post Monkeh said:**
> cheers.
saw that but i've never heard of the site before so i was sure if i should trust them. i've been following the guide [here]("http://www.spyware-techie.com/xp-internet-security-removal-guide/").

and before anyone jumps on the "it's just windows" bandwagon, i don't know much about the internal workings of my OS, but since this managed to infect me through firefox, i'm guessing it's a vulnerability in firefox (or a particular website more likely) that could be exploited on any os.

it's a javascript exploit.  i've seen the popups for it come up even on legitimate websites.

---

### Post by Post Monkeh on 2010-03-08
ended up reinstalling.

with me deleting partitions i was going to end up having to reinstall a lot of stuff anyway, thought i might as well make sure i'm rid of the virus altogether.

---

### Post by xpod on 2010-03-08
> **Tristam Green said:**
> it's a javascript exploit.  i've seen the popups for it come up even on legitimate websites.

Indeed.
It`s ending up on [more](http://www.nytimes.com/2009/09/15/technology/internet/15adco.html?_r=1) & [more](http://www.computerweekly.com/Articles/2009/10/27/238317/gizmodo-tricked-into-serving-scareware-laced-adverts.htm) popular sites and we even have a good dozen+ threads covering the junk ourselves here at UF.

---

### Post by NightwishFan on 2010-03-08
This happened to my friend.. How now uses Ubuntu by choice. :D

His parents blamed him it turned out it was his dad who did it.

---

### Post by Post Monkeh on 2010-03-08
> **NightwishFan said:**
> This happened to my friend.. How now uses Ubuntu by choice. :D

His parents blamed him it turned out it was his dad who did it.

ubuntu's free of it at the minute.

i don't think anything like this xp internet security could happen on linux without a root password, but someone could still do pretty nasty things with your user directory i'd imagine

---

### Post by Tristam Green on 2010-03-08
> **Post Monkeh said:**
> ended up reinstalling.

with me deleting partitions i was going to end up having to reinstall a lot of stuff anyway, thought i might as well make sure i'm rid of the virus altogether.

Aw man, you gave up too easily.

I've gotten removal of this thing down to an artform at work...20 minutes tops.

Run the rkill script that you find on bleepingcomputer.

Once explorer.exe reloads, check the task manager for anything that doesn't look normal.  Use a second computer to cross-check process names.

Clear your browser cache and clear your temp directories, including 
[indent]c:\temp
c:\documents and settings\username\local settings\temp[/indent]
***make sure you have enabled view on hidden folders/files and system files.***

I always check these areas in the registry for anything that looks funky:

hklm\microsoft\windows\current version\run
[indent]look for anything that exists in c:\documents and settings\username\local settings\temp\*.exe[/indent]

Run Malwarebytes to pick up any residuals.

Restart, and check back through those areas again.

---

### Post by Post Monkeh on 2010-03-08
i normally would have just kept at it, but like i said,  my partitions were a bit of a mess. i had a drive c, d, e, f, g & m, which was too many considering i had programs installed on all of them.

the plan was to just move everything onto 2 partitions (excluding the windows c drive) - one partition for my programs, one for the data and files, and then reinstall, but i could have ended up with registry problems so i just went for the reinstall.

i forgot how horrible it is. boot up to no wireless. luckily i have my laptop to download the driver. video card needs a driver, different bits of hardware need drivers.
took me 3 reboots to get sp3 installed (my xp disk is sp2 anyway), and it took half an hour to download and install the 60mb file (file itself downloaded in around 5 minutes)
started my reinstall nearly 3 hours ago now and i'm still installing updates and have yet to install any programs.
i really have to laugh when people say windows is easier to use than ubuntu. in fact any linux distro i've tried i've had installed and updated (with all the softare i want installed) within an hour.

---

### Post by NightwishFan on 2010-03-08
Users can still be vulnerable. Target the human not the machine. Someone will install a rogue deb if they do not understand why not to.

---

### Post by Tristam Green on 2010-03-09
> **Post Monkeh said:**
> i normally would have just kept at it, but like i said,  my partitions were a bit of a mess. i had a drive c, d, e, f, g & m, which was too many considering i had programs installed on all of them.

What is this I dont even; that is a messed-up partition scheme.

---

### Post by Kazade on 2010-03-09
Loosely related, but I now tend to recommend people run Windows in VM in Virtualbox on Ubuntu. You can even set it up as a session from the GDM which is pretty cool. Obviously not the best idea if you play D3D games.

Then if anything does infect it, it's just a quick roll back to a snapshot :)

---

### Post by Post Monkeh on 2010-03-09
> **Tristam Green said:**
> What is this I dont even; that is a messed-up partition scheme.

the pc used to be used by me and my dad. i had 5 partitions then. 
windows
my programs
my files
dad programs
dad files


i got a new hard drive a couple of years ago and just copied the same partition scheme for the drive i was replacing and copied the files across to save me being forced to reinstall  my programs. i then made ANOTHER partition with the remaining space.
my dad hasn't used the pc in years, the partitions were just a throwback to then.  i knew it was messy and i've been meaning to fix it for ages.

i've now got it down to 3. 2 partitions on my 80gig drive, (& 1 swap partition for linux) and 1 on my 500 gb drive (& 2 linux partitions & a swap partition)

---

