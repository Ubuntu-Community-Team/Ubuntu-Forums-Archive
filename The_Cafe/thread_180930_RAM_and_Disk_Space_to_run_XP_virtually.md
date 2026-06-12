---
title: "RAM and Disk Space to run XP virtually?"
date: 2006-05-23
forum: The Cafe
---

### Post by Jucato on 2006-05-23
Here's the deal:
I'm currently dual booting Kubuntu Breezy and Windows XP. I mainly use Kubuntu, but my sister uses nothing but XP. Once in a while, I also pop into my XP install to play some online games and use some apps that either have no Linux ports or can't be run through WINE.

The thing is, I hate to have to reboot every time I need to do something in XP. As much as possible, I want to stay within Linux. So the question is:

How much RAM and disk space do I need in order to run XP smoothly and still play these online games? Will 512MB RAM and a partition of 10GB be enough? 

My current processor speed, btw, is 1.5GHz (AMD Sempron 2200). I also currently have 256MB RAM from two sticks (128 + 128 ). I'm planning to buy a 512MB stick and put it in with a 128MB stick (I only have 2 slots for RAM), making a total of 640MB. The game's minimum memory requirement is just 258MB and 800MHz.

And finally, which virtual emulator (is that what they call it) do you recommend? VMWare? Qemu? something else?

Thanks!!

---

### Post by Engnome on 2006-05-23
I tried qemu, it worked very well but was slow (didnt try the accelerator thing) You can forget about any 3d games. Apps and simple 2d games work ok though.

I installed it onto a 8 gigabyte img file (XP thinks its a harddrive) and with my 1.7 gHz pentium m and 512 ram the speed was acceptable.

---

### Post by Stealth on 2006-05-23
If only PCs had Parallel...:D

---

### Post by Jucato on 2006-05-23
[QUOTE=Engnome]You can forget about any 3d games. Apps and simple 2d games work ok though.[/QUOTE]

I forgot to mention that I also have an NVIDIA GeForce MX 4000 with 128MB DDR-RAM. With it, will it be possible to play the 3D games?

[QUOTE=Stealth]
If only PCs had Parallel... :D[/QUOTE]

Forgive my noobishness, but what do you mean? ](*,)

---

### Post by jnev on 2006-05-23
to emulate windows with something like vmware, you can get by with 512mb of ram, though 1gb would be better. you can forget about any kind of games though; so far I haven't been able to figure out how to get my nvidia drivers installed (running the exe does NOT work). it's good for any applications you need (I use it for dreamweaver and photoshop), but gaming is not going to work.

---

### Post by Jucato on 2006-05-23
Ah too bad... :(
Guess I'll have to stick to the old fashion way: Reboot...

---

### Post by MartinJ on 2006-05-23
I'm using a Windows XP virtual machine on my laptop: 1.7GHz with 768MB ram and a hopeless mobile graphics chip.

Startup, using explorer, general use is very responsive, you wouldn't be able to tell it is running virtually.

However, I installed the latest Football Manager game and any disk operations such as saving, loading are very slow, about 5 times as long as normal.  Also, the graphics are a bit jumpy at times.

---

