---
title: "ReactOS won't have MIDI Support, sadly."
date: 2009-10-18
forum: The Cafe
---

### Post by coldReactive on 2009-10-18
Just a little sad that ReactOS won't have MIDI Support, janderwald isn't going to do it.

> (6:25:55 AM) janderwald: 
coldReactive42: i will never implement midi
(6:25:56 AM) dreimer: 
thx for the +1 smiley1_ ;-)
(6:26:04 AM) coldReactive42: 
k
(6:26:17 AM) Colin_Finck: 
coldReactive42: amd64 branch doesn't replace i386 compatibility, that would be nonsense
(6:26:18 AM) coldReactive42: 
A lot of vgmusic.com people will be angry at you janderwald
> (6:26:36 AM) coldReactive42: 
amd64 can't build without kernel32
(6:26:46 AM) smiley1_: 
dreimer: I allways beleived that this is the best way to go. to me alpha releases don't have a point
(6:26:47 AM) dreimer: 
cant we just use the included midi engine in the sb drivers?
(6:26:58 AM) dreimer: 
smiley1_ 2nded
(6:28:24 AM) dreimer: 
ouuuh 1024 posts :-D
(6:28:36 AM) Colin_Finck: 
coldReactive42: and? That's the kernel32 interface for Win64 apps then
(6:28:39 AM) dreimer: 
1337!!!111
(6:29:07 AM) coldReactive42: 
How am I, or a buildbot, supposed to build amd64 without kernel32?
(6:29:57 AM) janderwald: 
coldReactive42: to implement such a driver brings very little benefit and takes a lot of time to implement

---

### Post by Sand &amp; Mercury on 2009-10-18
He didn't explain why. :|

---

### Post by coldReactive on 2009-10-18
> **Sand & Mercury said:**
> He didn't explain why. :|

Sorry, forgot the rest:

> (6:26:36 AM) coldReactive42: 
amd64 can't build without kernel32
(6:26:46 AM) smiley1_: 
dreimer: I allways beleived that this is the best way to go. to me alpha releases don't have a point
(6:26:47 AM) dreimer: 
cant we just use the included midi engine in the sb drivers?
(6:26:58 AM) dreimer: 
smiley1_ 2nded
(6:28:24 AM) dreimer: 
ouuuh 1024 posts :-D
(6:28:36 AM) Colin_Finck: 
coldReactive42: and? That's the kernel32 interface for Win64 apps then
(6:28:39 AM) dreimer: 
1337!!!111
(6:29:07 AM) coldReactive42: 
How am I, or a buildbot, supposed to build amd64 without kernel32?
(6:29:57 AM) janderwald: 
coldReactive42: to implement such a driver brings very little benefit and takes a lot of time to implement

---

### Post by Slug71 on 2009-10-18
I think it may still happen in the future. I think at the moment their focus is getting USB to work and fixing the Bootloader and Installer.

Hopefully their update manager will be fixed for the next release.

---

### Post by coldReactive on 2009-10-18
> **Slug71 said:**
> I think it may still happen in the future. I think at the moment their focus is getting USB to work and fixing the Bootloader and Installer.

Hopefully their update manager will be fixed for the next release.

No, janderwald specifically also stated that if they want MIDI support, they have to do it themselves. (Though, I don't have the log to back that up -_-)

---

### Post by Slug71 on 2009-10-18
> **coldReactive said:**
> No, janderwald specifically also stated that if they want MIDI support, they have to do it themselves. (Though, I don't have the log to back that up -_-)

Oh well, dont think i'll really use it anyways but im sure that sucks for the people that  would. Give it a while. Soon when more pieces come together and it becomes more usable and the user base increases i think its possible something will happen.

---

### Post by Eisenwinter on 2009-10-18
...okay.

First lets see ReactOS become stable enough for anyone to even **mildly consider** to produce music in any way on it.

---

### Post by RiceMonster on 2009-10-18
Wait, people care about this?

---

### Post by Slug71 on 2009-10-18
> **RiceMonster said:**
> Wait, people care about this?

I actually like ReactOS. I like the concept behind it and like that i may be able to play my games on a non M$ system or having a Windows like system for software that doesnt work on Linux like the software to update my Garmin.

Then i can finally get rid of all traces of M$ :)

---

### Post by CharmyBee on 2009-10-18
The "submit a patch" mentality, huh. ReactOS will be done and complete to the Windows 2000 level by 2074 at this rate.

It's still pretty shameless how downright similar the setup routines are to Windows, and even the typefaces, color schemes and autorun program on the disc. It's definitely not 'inspired', it's more knock-offy than I thought.

---

