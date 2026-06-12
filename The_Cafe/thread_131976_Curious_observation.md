---
title: "Curious observation"
date: 2006-02-17
forum: The Cafe
---

### Post by Netisan on 2006-02-17
Using monitoring services:
Under windows ram usage reaches closely the limit. HDD runs actively. Processor rate gives low percents. 
Under Ubuntu ram is low, disk doesn't run, processor runs 65-100% (as per the benchmark). Computer itself is faster..

What I early noticed-there is not this typical HDD crrrrrrrrrrrr in Linux.

---

### Post by Stormy Eyes on 2006-02-17
Part of it, I think, is that the Linux kernel itself handles virtual memory differently. Also, if a Linux app loads libFoo.so (a DLL), the next app that needs libFoo.so will use the copy already resident in memory instead of loading its own copy.

---

### Post by chimera on 2006-02-17
Two words:

shared

libraries

---

### Post by mstlyevil on 2006-02-17
[QUOTE=chimera]Two words:

shared

libraries[/QUOTE]

Not to get too technical but there are shared DLL's in Windows. This is one of the reasons for conflicts due to bad code. But I am sure Linux has a lot more shared libraries.

---

### Post by fuscia on 2006-02-17
dude, you should definitely switch to linux.

---

### Post by towsonu2003 on 2006-02-17
I will say this has also something to do with your hardware. Keeping in mind that my windows do not access internet, does not use firefox, and is not updated at all (not even SP1), I have: 

> **Netisan]
Under windows ram usage reaches closely the limit. HDD runs actively. Processor rate gives low percents. [/quote]
this is my linux behavior (hdd not active, unless needed said:**
> 
Under Ubuntu ram is low, disk doesn't run, processor runs 65-100% (as per the benchmark). Computer itself is faster..
typical HDD crrrrrrrrrrrr in Linux.
this is my windows' behavior. processor more around 30-40%, crrrr sound is in my linux during updatedb (scared the HELL out of me the first time) and mounting flash media... 

I don't really care as long as I can open 6-7 openoffice windows + 5-6 tabs of firefox + calculator + connect to internet + liferea.

---

### Post by prizrak on 2006-02-18
[QUOTE=mstlyevil]Not to get too technical but there are shared DLL's in Windows. This is one of the reasons for conflicts due to bad code. But I am sure Linux has a lot more shared libraries.[/QUOTE]
The thing in Windows is that because of DLL hell many applications ship with their own DLL's and load the copy that came with them as opposed to the system wide copy.

---

### Post by mstlyevil on 2006-02-18
[QUOTE=prizrak]The thing in Windows is that because of DLL hell many applications ship with their own DLL's and load the copy that came with them as opposed to the system wide copy.[/QUOTE]

True. Which is why there are more shared libraries in Linux than in Windows. Linux does a better job of using shared libraries.

---

### Post by Netisan on 2006-02-18
[QUOTE=fuscia]dude, you should definitely switch to linux.[/QUOTE]
Yes, of course.. but.. Frankly, I'm now here with windows:-#  Having problems with Gnome. Need support.
The alternative is to have 2 Ubuntus - one for experiments, other for support :D

---

