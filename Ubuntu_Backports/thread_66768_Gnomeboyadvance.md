---
title: "Gnomeboyadvance"
date: 2005-09-18
forum: Ubuntu Backports
---

### Post by mzhang on 2005-09-18
Downloaded gnomeboyadvance from backports.

Now when I got do:
--> Edit
--> Preferences
--> (Roms Directory) --> Browse
I get "*** glibc detected *** free(): invalid pointer: 0xb79f0d80 ***".

---

### Post by mzhang on 2005-09-26
Hello?

---

### Post by kazuya on 2005-11-15
I'm with you on this. Same issue or problem. Has anyone gotten gnomeboyadvance to work or load ROMs successfully? It doesn't work for me either. It has been like months now I have been trying to get thisd thing working.

Xandros and mepis, you could just select ROM and place over visualboy advance executable and it plays, but lacks things like joystick configurator? 

I may have to giveup on gnomeboyadvance. It doesn't even try to work. Can't open or load my ROMs to play. I wonder if it really uses visualboyadvance? Is there a particular revision of Visualboyadvance that works with mike's gnomeboyadv deb?

On Ubuntu, I still cannot simply drag the ROM over executable to play?

I really like the no root user account thing, but nothing seems to get done without being logged on as root or sudo root?

This is anoying for me on Ubuntu.

---

### Post by Technoviking on 2005-11-15
Is this the hoary backport?

If you are using breezy try this:
[http://www.mikesplanet.net/?p=9](http://www.mikesplanet.net/?p=9)
Mike

---

### Post by Jeremiah85 on 2005-11-17
[QUOTE=mzhang]Downloaded gnomeboyadvance from backports.

Now when I got do:
--> Edit
--> Preferences
--> (Roms Directory) --> Browse
I get "*** glibc detected *** free(): invalid pointer: 0xb79f0d80 ***".[/QUOTE]


I managed to work around this by using the Configuration Editor to manually add the path to the ROMs.

Applications---> System Tools

Expand Apps then expand Gnomeboyadvance

Select General and edit the "romDir" key

Put the path to your ROMs as the value.


I tried this a few days ago and it has worked so far.

---

