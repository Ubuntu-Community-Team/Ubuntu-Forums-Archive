---
title: "[SOLVED] Why does everybody hate the windows registary?"
date: 2008-11-10
forum: Windows
---

### Post by CJ Master on 2008-11-10
Just wondering, I don't see anything wrong with it.

...I remember when it first came out microsoft called it an innovation :P

---

### Post by Newuser1111 on 2008-11-10
> **CJ Master said:**
> Just wondering, I don't see anything wrong with it.

...I remember when it first came out micro**s**oft called it an innovation :PI also don't see anything wrong with it.

---

### Post by kernelhaxor on 2008-11-10
I don't hate it ..

---

### Post by Shwefty on 2008-11-10
I asked a friend of mine this question the other day!  We both don't know why everybody hates it.  Fine by me.

---

### Post by handy on 2008-11-11
It is the epitome of bad design.

The unreliability of windows primarily stems from the existence of the registry.

I consider the existence of the overly complicated & huge registry to have been designed & implemented in an effort to severely limit the possibility of users being able to copy the directory holding an application from one computer to another, as can be done on Linux, Apple & Amiga OS's, just to name a few.

The MS policy introduced with win95, was for 3rd party application to be designed to be spread throughout the windows system & the ever growing monster  which is the registry.

Viruses & mal-ware use the registry, combine that with the ease of corruption of the registry & you may understand what makes anyone who has spent time maintaining windows systems loath the registry & the whole design of the windows OS's.

Due to the nature of the registry, it is very often easier to reinstall the system than spend the time diagnosing & repairing the registry.

The only good thing about windows Me, was System restore, which basically takes you back to a backup of a previous registry.  Smartest thing MS ever released, in so doing MS did not make the system more reliable, they just made it cheaper & easier to maintain.

---

### Post by Archmage on 2008-11-11
"This program can't be installed, because it is already installed." This program can't be uninstalled..." means that you have to search the registry by hand and remove it. This can take only hours.

After than you than can install the program again. :KS

---

### Post by insane_alien on 2008-11-11
the biggest problem with the registry is that is a fragile single point of failure. it doesn't take much to screw it up and when it screws up unless you have a backup available then your borked.

---

### Post by ichi@YUKI on 2008-11-11
some viruses and malware hide and/or alter the registry. of course they were designed to do that just to get windows users pissed, since like already mentioned, it's easier to re-install the OS than to fix the registry problem.

> The only good thing about windows Me, was System restore, which basically takes you back to a backup of a previous registry. Smartest thing MS ever released, in so doing MS did not make the system more reliable, they just made it cheaper & easier to maintain.

I heard even the viruses get restored with system restore.. though i'm not quite sure.. lol..

---

### Post by nlinecomputers on 2008-11-11
> **handy said:**
> It is the epitome of bad design.

The unreliability of windows primarily stems from the existence of the registry.

I consider the existence of the overly complicated & huge registry to have been designed & implemented in an effort to severely limit the possibility of users being able to copy the directory holding an application from one computer to another, as can be done on Linux, Apple & Amiga OS's, just to name a few.

The MS policy introduced with win95, was for 3rd party application to be designed to be spread throughout the windows system & the ever growing monster  which is the registry.

Viruses & mal-ware use the registry, combine that with the ease of corruption of the registry & you may understand what makes anyone who has spent time maintaining windows systems loath the registry & the whole design of the windows OS's.

Due to the nature of the registry, it is very often easier to reinstall the system than spend the time diagnosing & repairing the registry.

The only good thing about windows Me, was System restore, which basically takes you back to a backup of a previous registry.  Smartest thing MS ever released, in so doing MS did not make the system more reliable, they just made it cheaper & easier to maintain.


I agree.  Many registry entries are cryptic code names.  Unless you know what the 20 digit UID for your program is you can't easily find and repair or remove the program.   If an INI file is corrupted only one program is affected.  If the registry is corrupted your system is bricked.   Items can be hidden with ease in the registry making uninstalling a program a problem as few programs properly clean up after themselves.   

The DS engine running the registry is slow.  Wonder why Windows take so long to boot?  This is why.  In *nix ini files are only accessed as needed so memory is freed when they shut down.  Not so with the registry.

---

### Post by smoker on 2008-11-11
> **ichi@YUKI said:**
> some viruses and malware hide and/or alter the registry. of course they were designed to do that just to get windows users pissed, since like already mentioned, it's easier to re-install the OS than to fix the registry problem.

I heard even the viruses get restored with system restore.. though i'm not quite sure.. lol..

this is true, if the malware has entries in the registry, they will be back, bad as ever, with a system restore. first thing to do when cleaning a system is turn off system restore.

Erunt is a freeware app i use at times to back up a windows registry:
[http://www.larshederer.homepage.t-online.de/erunt/](http://www.larshederer.homepage.t-online.de/erunt/)

of course, only back up a 'clean working' registry

---

### Post by handy on 2008-11-11
> **ichi@YUKI said:**
> 
I heard even the viruses get restored with system restore.. though i'm not quite sure.. lol..

Not if you go back in time to a clean registry & restore.

Well, that is how it was on XP a few years ago.  I've been completely out of touch with viruses & other mal-ware since I closed shop & jumped ship. :)

---

### Post by zombiepig on 2008-11-11
> **handy said:**
> Not if you go back in time to a clean registry & restore.

Well, that is how it was on XP a few years ago.  I've been completely out of touch with viruses & other mal-ware since I closed shop & jumped ship. :)

Not necessarily - using system restore won't remove the virus infected files from the hard drive. So while it's possible that going back to a restore point from before the infection will remove any registry entries the virus has modified, your system is still infected! It's easier to wipe the system and reinstall, IMO.

---

### Post by SunnyRabbiera on 2008-11-11
yeh it makes things harder then they should be, the registry helps aid malware out in more ways then one.

---

### Post by crazyness003 on 2008-11-11
As everyone else stated, it was "awesome" when it came out. Yay, a single place to give all programs access to the system. But the design is flawed, very easily tricked and in order to defend the registry, you need a program to constantly watch it for changes...wich slows down your system ([COLOR=Red]**unnecessarily**[/COLOR] might I add).

Uninstalled programs leave traces in there

Its cryptic in a very [COLOR=Red]**unnecessary**[/COLOR] way

It has "you are only borrowing the software OS eventho you paid for it" written all over it. Some of the entries [COLOR=Red]arent[/COLOR] even **necessary**.

Notice how the word **[COLOR=Black]necessary[/COLOR]** sprang up in a [COLOR=Red]negative[/COLOR] sense in almost all of my sentences.

It is a pain, and needs not be.

ps: change one random "0" to a "1" in the registry and you may have yourself an ugly-stick butterfly effect.

---

### Post by bostonaholic on 2008-11-11
Also, that sh*tty registry and file system of M$ is why a full build of our application takes >80 minutes on Windows, when it only takes <20 in Hardy!!  Which is why we're getting sandbox development environments for us developers!!! ...but not for a couple more months :mad:

---

### Post by handy on 2008-11-12
> **zombiepig said:**
> Not necessarily - using system restore won't remove the virus infected files from the hard drive. So while it's possible that going back to a restore point from before the infection will remove any registry entries the virus has modified, your system is still infected! It's easier to wipe the system and reinstall, IMO.

Any software installed after the date of your system restore will still be on the machine, but it will be quarantined as a compressed restore point in the relative future, & would not be able to effect the system that it is no longer installed on.

I would think that the only form of virus or other mal-ware that would be a danger would have to be somehow hiding in the non-executable data which system restore leaves in place.

I guess its possible?  

Thankfully the windows system is no longer familiar to me, I'm too many years away from it.  I never expected that I'd ever make that statement.  ;-)

---

### Post by crazyness003 on 2008-11-12
> **handy said:**
> ....Thankfully the windows system is no longer familiar to me, I'm too many years away from it.  I never expected that I'd ever make that statement.  ;-)

Bravo. Unfortunately, many others cannot speak those words. :(

---

### Post by fatality_uk on 2008-11-12
The registry on my Windows XP box currently weighs in at a whopping 78mb. Now if that gets corrupted and can not be accessed due to one or two rouge entries, im pretty much screwed.

Bad design from the start breeds bad practise from Windows developers

---

### Post by Liviu-Theodor on 2008-11-12
Every Windows administrator is at least worried about the registry. Some programs do not delete keys within at uninstall, and that makes the registry bigger and biggeer over time. And there is also the "confortable" message regarding total system failure if you change something in registry.

---

### Post by Antman on 2008-11-12
> **handy said:**
> it is the epitome of bad design.

The unreliability of windows primarily stems from the existence of the registry.

I consider the existence of the overly complicated & huge registry to have been designed & implemented in an effort to severely limit the possibility of users being able to copy the directory holding an application from one computer to another, as can be done on linux, apple & amiga os's, just to name a few.

The ms policy introduced with win95, was for 3rd party application to be designed to be spread throughout the windows system & the ever growing monster  which is the registry.

Viruses & mal-ware use the registry, combine that with the ease of corruption of the registry & you may understand what makes anyone who has spent time maintaining windows systems loath the registry & the whole design of the windows os's.

Due to the nature of the registry, it is very often easier to reinstall the system than spend the time diagnosing & repairing the registry.

The only good thing about windows me, was system restore, which basically takes you back to a backup of a previous registry.  Smartest thing ms ever released, in so doing ms did not make the system more reliable, they just made it cheaper & easier to maintain.
+1

---

### Post by Viranh on 2008-11-13
The registry is difficult to maintain. It fills with junk over time and it's incredibly cryptic. Most programs don't remove their entries when you uninstall them. The registry gives access to the whole system and all its drivers and you don't need any sort of special permission to write to it. 
System restore is a nice idea, but in practice I've never had it work well. I've had it corrupt my whole system, and I have had viruses reinstall themselves in my new restored system. System restore is now one of the first things I turn off. Getting a virus usually = format the C:\ drive and reinstall windows.

---

### Post by cmat on 2008-11-14
Most of my complaints have been all addressed already in recent posts. To reiterate it's a very fragile part of the system and it's been centric to most of my computing woes when I was using Windows full-time. It's very hard to maintain and uninstalling applications still leaves debris which confound future installations.

---

### Post by Twitch6000 on 2008-11-14
Here is my view on the windows registry and its just my view so yeah don't hate me :[.

I find The windows registry their biggest success yet biggest failure.

Odd thought I know,but let me explain why i think this.

Why a Success ?

1. Well it is part of the reason why handling programs and installing info is so easy(correct me there if I am wrong I am still just starting on programming)

2. It makes setting up things easy and handling major settings simple from installation to uninstall(like the recyle bin name or any program settings at that)

3. I think this has to do with part of the reason why game makers use windows as their choice.

Why a failure ?

1. This also makes it easy for any kind of malware to just creep in and gain access.

2. This can cause alot of junk to come up and causing you to install reg cleaners to get rid of it.

3. Like has been stated if you mess up a single reg file you could run into big errors.

So I really think its like what others have said it was good at the start,but has turned into a failure.

It needs revamped or something cause this is something that has helped windows for a long time.

Anyways that is just my thoughts and I know one or two of them are wrong.

---

