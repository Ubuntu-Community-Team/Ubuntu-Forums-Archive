---
title: "Far Cry Illegal Instruction"
date: 2009-06-05
forum: Wine
---

### Post by kartoffel1337 on 2009-06-05
I have a problem with Far Cry with nocd patch on wine 1.1.22:

The Game it self works perfectly, surprisingly even faster than on Windows.
The only problem is I have to try starting it about 20 times until it works.
> wine FarCry.exe
outputs "Illegal Instruction" and just closes itself, than after trying around 20 times it suddenly starts and runs flawlessly.

any suggestions what's going on? it's really annoying that I can't just start it.

---

### Post by Dark Aspect on 2009-06-05
> **kartoffel1337 said:**
> I have a problem with Far Cry with nocd patch on wine 1.1.22:

The Game it self works perfectly, surprisingly even faster than on Windows.
The only problem is I have to try starting it about 20 times until it works.
> wine FarCry.exe
outputs "Illegal Instruction" and just closes itself, than after trying around 20 times it suddenly starts and runs flawlessly.

any suggestions what's going on? it's really annoying that I can't just start it.

I was unable to get Farcry running on Wine 1.1.22 due to the water drawing in a horrible way; it was completely unplayable imo. Have you tried to modify the system.cfg and all the other [suggestions over at wine hq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13613").

---

### Post by kartoffel1337 on 2009-06-05
I don't know what you mean by "all other suggestions", I only see the OpenGL trick, I did that.

When I use an Intel graphics adapter nothing really works, there are weird graphic bugs everywhere, with ATI everything looks fine, even the water.

But with both cards I have the Illegal Instruction problem.


What card do you have? Intel, Nvidia, Ati?
And what FarCry version are you using? I don't know what I have, but wine crashes when I try update to 1.40

---

### Post by Dark Aspect on 2009-06-05
> **kartoffel1337 said:**
> I don't know what you mean by "all other suggestions", I only see the OpenGL trick, I did that.

When I use an Intel graphics adapter nothing really works, there are weird graphic bugs everywhere, with ATI everything looks fine, even the water.

But with both cards I have the Illegal Instruction problem.


What card do you have? Intel, Nvidia, Ati?
And what FarCry version are you using? I don't know what I have, but wine crashes when I try update to 1.40

I have an Nvidia Geforce 9800 GT with the 180.60 drivers. I used, before I deleted it a few days ago, Far cry 1.3 as I had the same update problem you had. I suppose there aren't many other ideas on wineDB, do you have any direct3d registry hacks enabled?

---

### Post by kartoffel1337 on 2009-06-05
I use some registry hacks for other games, but they should all be off for Far Cry.
They shouldn't do anything anyway using OpenGL.

It's weird that you have trouble with Nvidia, normally Ati cards make a lot more trouble with wine than Nvidia cards do.

---

### Post by Bozzeye on 2010-09-12
I have the same problem in 10.10 32-bit, but Far Cry won't start at all. Wine version is 1.3.2, graphics card is Nvidia GeForce 6800 XT and the driver is 256.53. Any tips?

Edit: Nevermind, I downloaded a no-cd crack and it worked.

---

