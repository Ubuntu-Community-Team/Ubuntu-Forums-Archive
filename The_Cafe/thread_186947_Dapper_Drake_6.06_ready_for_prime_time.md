---
title: "Dapper Drake 6.06 ready for prime time?"
date: 2006-06-02
forum: The Cafe
---

### Post by Syirrus on 2006-06-02
How many users out there think that Dapper is ready for use?

---

### Post by meng on 2006-06-02
Yes it is.
Perhaps not for everyone though, but IMHO no less so than Breezy.

---

### Post by ubuntu_demon on 2006-06-02
Yeah it is ready. IMHO it is better than breezy (faster,more stable and more polished). Dapper isn't suitable for everyone though.

**who should use Ubuntu**
[quote=ubuntu_demon]
IMHO this falls down into five groups :

ex-debian users. Possible reasons : newer software,nice community,polish.

other linux users who formerly used another distro. Possible reasons : easy,nice community,polish.

People who feel windows is not secure enough and they don't have enough control over windows.

people who feel windows is not secure enough and who only need to do simple tasks like browsing,chatting and using e-mail.

people who want an easy installable secure,stable server with recent software. (debian is also very good here)
[/quote]

**who shouldn't use ubuntu**
[quote=ubuntu_demon]
IMHO four groups of people :

Users who play a lot of recent commercial games. (unless you only want to play ID games such as quake 4)

Users who run commercial software which isn't possible to run in Ubuntu and there's no alternative software solution.

Users without patience unless they only want to use e-mail, webbrowser and gaim. If they want to do more things they need a bit of patience sometimes. Users who think windows is easy but don't realise it's quite hard to install and configure windows to run secure and stable.

Users who don't have a broadband internet connection.
[/quote]

**in which category do you fall ?**

[quote=ubuntu_demon]
I fall into a combination of these groups :

ex-debian users. Possible reasons : newer software,nice community,polish.

People who feel windows is not secure enough and they don't have enough control over windows.

I didn't use debian as my primary desktop (I used windows XP) but I have used it.
[/quote]

These quotes are from my answer in this thread : [http://ubuntuforums.org/showthread.php?t=185005](http://ubuntuforums.org/showthread.php?t=185005)

---

### Post by Klaidas on 2006-06-02
I'm sure it's ready ;)
I'm dual booting with Windows XP, but since dapper has been officially released as stable, I havent' booted into Windows. :-k

---

### Post by therunnyman on 2006-06-02
"No," said therunnyman, "no, it's not ready.  It doesn't support SATA raids consisting of more than two drives, it still uses that convoluted mess called 'udev' - which, I hear, the creators of udev don't really understand - it cannot burn a CD (and on this issue I speak from a position of authority), and compiz still gets the whoopdee-fookin'-doo from me.  It's worse than the beta; How can that be?"

"Breezy, however, " continued therunnyman, "rides on rails.  A near perfect DE/OS combo."

therunnyman

---

### Post by John.Michael.Kane on 2006-06-02
Dapper is ready for prime time **On The Hardware I Use. **

---

### Post by therunnyman on 2006-06-02
Should I call you "Snake" or "Plissken"?

Yes, I concede your point, Snake.  Udev's still there though, and compiz isn't interesting enough yet (I stress "yet").

---

### Post by sha_man on 2006-06-02
compared to breezy, yes definately!

---

### Post by aysiu on 2006-06-02
Same as it ever was:
[http://www.psychocats.net/essays/linuxdesktop](http://www.psychocats.net/essays/linuxdesktop)

---

### Post by John.Michael.Kane on 2006-06-02
therunnyman I'm sure the issues you stress in reguards to sata-raid are valid, however i always thought that issues like this where based on the sata chip being used.being that i don't sata that is just a guess. as for compiz/xgl i guess time will tell how that plays out on the hardware that will run it, and if it can made to run with out alot of CL work arounds. as it stands it does look very interesting. udev i will just leave that those with more knowledge of it . The best anyone could do when looking at any distro is pick one based on support of your hardware or build your machine around the distro you want to use. now i know thats not the best answer or the only answer however for some it is what works for some.


Just my thoughts..

---

### Post by Randomskk on 2006-06-02
I installed Kubuntu Dapper on my laptop, and **everything** "just worked" - the screen, touchpad, sound, wireless, wired, CPU scaling, ACPI stuff, etc.
A single, incredibly easy change to xorg.conf and my widescreen is working perfectly as well.

Overall, I'd say it's certainly ready for prime time, everything is better than ever before.

---

### Post by Randomskk on 2006-06-02
bleh, double post, sorry

---

### Post by eMuNiX on 2006-06-02
I still find that CUPS is half broken, works with my Epson C64 but not my Brother BJC4550.  These both worked well until about Flight 7 when it failed, but everything else is fine.

---

### Post by carlosqueso on 2006-06-02
new XFCE so.......pretty............:shock:

---

### Post by YourSurrogateGod on 2006-06-02
Ok, the last option in that poll and the fact that someone voted for it is hilarious :D .

---

### Post by therunnyman on 2006-06-02
[QUOTE=SD-Plissken]therunnyman I'm sure the issues you stress in reguards to sata-raid are valid, however i always thought that issues like this where based on the sata chip being used.being that i don't sata that is just a guess. as for compiz/xgl i guess time will tell how that plays out on the hardware that will run it, and if it can made to run with out alot of CL work arounds. as it stands it does look very interesting. udev i will just leave that those with more knowledge of it . The best anyone could do when looking at any distro is pick one based on support of your hardware or build your machine around the distro you want to use. now i know thats not the best answer or the only answer however for some it is what works for some.


Just my thoughts..[/QUOTE]

Just to clarify, I ran Dapper on a three-disk RAID, and all my hardware is fully supported.  What happened was, RAID-wise, I had to physically rewire the disks in order to get this thing to work.  The SATA controller (fully supported Promise PCI card) was mounting before the mobo controller, so sda would be the drive connected to the Promise card, then sdb and c would be the mobo drives.  Drove me nuts trying to remember what was going to mount as what.

I know the problem, filed the bug, refiled the bug, confirmed the bug about, I dunno, 700 times, but nothing changed.

And therunnyman asked the swine, "What is thy name?"  The swine said unto him "Udev, for we are many."  I know the exact file that needs fixin', but damned if I can understand udev.  Until that's fixed, I've posted a workaround for SATA RAIDs in the Beginner forum.

Just pissed at the devs is all.  RAIDs are kind of important, especially when dealing with Linux, you know?

therunnyman

---

### Post by John.Michael.Kane on 2006-06-02
therunnyman I understand. Atleast those with this issue have the workaround you posted. all we as endusers who are not versed in programing can do is file bugs, and hope they are fixed.

---

### Post by TrailerTrash on 2006-06-02
I just loaded with fresh installs on 3 laptops....2 ubuntus and one Xubuntu. eVERYTHING works including hibernate ,3D acc., and other things. On one old dell lappy with a ATI card, it even works with 3D out of the box! :-k :confused: I have no idea how that happen. LOL....I would recomend everyone to do a fresh install..I noticed things just work better. 

I have not installed Kubuntu yet and not sure i will.

---

### Post by adamb10 on 2006-06-02
IMHO I dont think Ubuntu is ready for primetime.  I think included with Ubuntu should be a Linux beginners guide that tells the difference between Windows and Linux(eg, tell what a package is, and all that).

---

### Post by polo_step on 2006-06-02
[FONT="Courier New"]I think it's a little soon to say, if you just installed it.  Initially, I'm very impressed running in "Live" mode, but I haven't been able to do a clean install until I can get a bunch of stuff salvaged and archived off the HD of an exiting 5.10 installation before reformatting it to start fresh.  Hating this sort of tedious task and being a slug in hot weather, I may not even get around to it before October, unless I do my usual stunt of buying yet another HD because I'm too lazy to pick stuff off the previous one.:rolleyes: 

I think glowing honeymoon reports are premature; until you've run the system hard for a month or two, you really won't know what strange little problems will turn up.  

All that said, I really do like the looks of 6.06 so far, and it's definitely the only Linux I've seen yet that I'd recommend to any relatively typical user.
[/FONT]

---

### Post by scojo on 2006-06-02
I did an upgrade from Breezy and everything that I need worked for me.  I'm using Dapper on a Gateway laptop.  No complaints at all.

---

