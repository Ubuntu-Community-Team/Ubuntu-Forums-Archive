---
title: "RAM Requirements"
date: 2008-10-24
forum: Windows
---

### Post by geekgod90 on 2008-10-24
Hi Geeks 


    I use Windows XP SP2 with 256Mb ram and 128Mb ATI Radeon Express 200 series graphic Card. I installed NFS underground 2 which needs a minimum of 256 mb ram . 



    When i tried to open the game , the game does not start and i receive an error saying that Speed.exe has encountered an error , but then i realised that the software called EAsy Info bundled with d game shows my **ram as 223mb instead of 256mb ram** 


  Please HElp . Thanks in advance :(

---

### Post by Bucky Ball on 2008-10-24
Have you noticed this is a Linux/Ubuntu forum? There are other forums for Windoze gamers to ask questions, but you never know ... someone might pop up to give you a hand.

---

### Post by ch_123 on 2008-10-24
Isn't the Express 200 an integrated chipset? If so, it wouldn't be unusual for it to steal some RAM. Are you sure the problem is RAM related though?

---

### Post by Bucky Ball on 2008-10-24
> **geekgod90 said:**
> **ram as 223mb instead of 256mb ram** 

This is completely normal. The filesystem needs to go somewhere else the drive/partition wouldn't know what it was or have any role in life! This could be more accurate than the OS reading, especially if it is telling you 256mb.

---

### Post by geekgod90 on 2008-10-24
> **ch_123 said:**
> Isn't the Express 200 an integrated chipset? If so, it wouldn't be unusual for it to steal some RAM. Are you sure the problem is RAM related though?


ya i m sure it is a ram related problem coz d software indicates that the game requires 256 mb ram whereas i have 223 :( and all other criterias like video memory are met with and its ram that is causing a prblm

---

### Post by Bucky Ball on 2008-10-24
RAM is cheap right now. That is one thing. :)

---

### Post by geekgod90 on 2008-10-24
> **Bucky Ball said:**
> This is completely normal. The filesystem needs to go somewhere else the drive/partition wouldn't know what it was or have any role in life! This could be more accurate than the OS reading, especially if it is telling you 256mb.
ya i know this is compltely know this is true  but the game requires 256 ram and i am stuck up with 223 . i had installed this game earlier and it ran fine 

please help

---

### Post by smoker on 2008-10-24
what does the bios setup say your ram is? check it hasn't put aside 32mb ram for onboard graphics use, if you are using a plugin graphics card this shouldn't be necessary.

if you have a ubuntu live cd, use the memtest option to test your memory, or download and make a bootable version of memtest from here and check your ram:
[http://www.memtest.org/](http://www.memtest.org/)

---

### Post by geekgod90 on 2008-10-25
> **smoker said:**
> what does the bios setup say your ram is? check it hasn't put aside 32mb ram for onboard graphics use, if you are using a plugin graphics card this shouldn't be necessary.

if you have a ubuntu live cd, use the memtest option to test your memory, or download and make a bootable version of memtest from here and check your ram:
[http://www.memtest.org/](http://www.memtest.org/)



yep u r right d bios has really alocated 32 mb for sumthing called as UMA buffer 

i saw 4 options there 32 mb 64 mb and 128 mb and 256 mb but did not see 0 mb :lolflag: 

Please what to do next

---

### Post by fiddledd on 2008-10-25
> **geekgod90 said:**
> yep u r right d bios has really alocated 32 mb for sumthing called as UMA buffer 

i saw 4 options there 32 mb 64 mb and 128 mb and 256 mb but did not see 0 mb :lolflag: 

Please what to do next

If that is "UMA frame buffer" it's shared memory dedicated to your GFX.

There's no "0" option because you'd have no display. I think the only option is to get more memory.

---

### Post by smoker on 2008-10-25
looks like, as fiddledd stated, you'll have to buy more ram, especially if it is a laptop you have. if you have a desktop you could try fitting a decent graphics card with it's own memory, then the bios should give up that 32mb. but a ram upgrade is probably your easiest and cheapest option.

---

