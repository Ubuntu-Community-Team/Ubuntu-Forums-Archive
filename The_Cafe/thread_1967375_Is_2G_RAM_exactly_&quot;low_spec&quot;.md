---
title: "Is 2G RAM exactly &quot;low spec&quot;?"
date: 2012-04-28
forum: The Cafe
---

### Post by OpenSourceRules on 2012-04-28
With Firefox or Chromium running for 200MB (likely), 512MB just won't do much good.
I made the decision to upgrade the RAM from 512MB to 2G (the max it can hold; I tried 4G and it didn't boot.)
Even with these upgrades, the computer is held back with a relatively slow 80G hard drive (but it is usually quite empty).
I just learned that the max I can go is like a 320G Hard drive, but it is largely pointless when I just use about 10% of a 80G Hard Drive.
Don't be surprised: I quit online multimedia years ago.  
Then again, when I tried to use Main Edition of Linux Mint, the keyboard misbehave on Firefox and Chromium (laggy reactions).  This also happens when I installed XFCE DE under the Main Edition or LXDE Edition of Linux Mint.:p

---

### Post by jerome1232 on 2012-04-28
What model and speed of cpu do you have? More than likely it's what's holding you back.

```
cat /proc/cpuinfo
```

---

### Post by F.G. on 2012-04-28
> **jerome1232 said:**
> What model and speed of cpu do you have? More than likely it's what's holding you back.

```
cat /proc/cpuinfo
```

for sure.
2gig is perfectly fine (i've only got 1 in my ladptop) and the size / speed of the hdd is not going to make a significant  difference (i mean the size wont make any different at all). you may want to try reseating the ram (although it sounds like you did that recently). also, if this computer is old your cpu might be overheating (if the thermal past is all used up and the heat sink is full dust, etc). that would make a significant reduction in speed.

anyhow, isn't this is more of a support question?

---

### Post by Paqman on 2012-04-28
Depends on what apps you're running. For most stuff on Linux 2GB should be fine. The only reason I have 4GB is to give VMs a bit of headroom.

---

### Post by lisati on 2012-04-28
As others have said, you should be fine with 2Gb, which is what I have in my laptops. One of my machines has only 64Mb!

---

### Post by Bandit on 2012-04-28
I recommend minimum of 4GB for multimedia users, but 2GB is fine for most users that only listen to music, surf the web and do office releated stuff. I highly suggest not going any lower as there is deffently some performance degredation due to programs having to be swapped in and out of virtual ram. I have two Netbooks one with 1.5GB of RAM and the other with 2GB. While both work, I can tell the one with 1.5GB is slower. Its faster then it was before I found an extra 512MB and put into it, but still slower then the other with 2GB. They both have the same CPU btw. But like I mentioned unless you do a little home video editing or a lot of multitasking, 2 GB should provide you with a good balance of performance.

---

### Post by Linuxratty on 2012-04-28
> **lisati said:**
> As others have said, you should be fine with 2Gb, which is what I have in my laptops!

2g on this machine here..It does fantastic..Quite speedy.

---

### Post by forrestcupp on 2012-04-28
> **lisati said:**
> As others have said, you should be fine with 2Gb, which is what I have in my laptops. One of my machines has only 64Mb!
I remember how proud I was back when I first had 64MB and most computers still only had 16-32MB. :)

Anyway, in the Ubuntu 12.04 LTS - Precise Pangolin thread, the OP said that his computer is running much faster now. So I guess going from 512MB to 2GB must have helped a lot. ;)

---

### Post by Linuxratty on 2012-04-28
> **forrestcupp said:**
> I remember how proud I was back when I first had 64MB and most computers still only had 16-32MB. :)



LOL! me too! I was so excited!

---

### Post by SemiExpert on 2012-04-28
> **OpenSourceRules said:**
> With Firefox or Chromium running for 200MB (likely), 512MB just won't do much good.
I made the decision to upgrade the RAM from 512MB to 2G (the max it can hold; I tried 4G and it didn't boot.)
Even with these upgrades, the computer is held back with a relatively slow 80G hard drive (but it is usually quite empty).
I just learned that the max I can go is like a 320G Hard drive, but it is largely pointless when I just use about 10% of a 80G Hard Drive.
Don't be surprised: I quit online multimedia years ago.  
Then again, when I tried to use Main Edition of Linux Mint, the keyboard misbehave on Firefox and Chromium (laggy reactions).  This also happens when I installed XFCE DE under the Main Edition or LXDE Edition of Linux Mint.:p

 If a mother board only supports 2GB, that's the best you're going to do.  It sounds as if you have an older PC.  As far as the hard drive, if it's IDE, not SATA, I wouldn't recommend upgrading anyway.

---

### Post by sffvba[e0rt on 2012-04-28
> **forrestcupp said:**
> I remember how proud I was back when I first had 64MB and most computers still only had 16-32MB. :)

Anyway, in the Ubuntu 12.04 LTS - Precise Pangolin thread, the OP said that his computer is running much faster now. So I guess going from 512MB to 2GB must have helped a lot. ;)

One of my happiest computing moments was when a friend of my dad (his tech support guy) came to our house and brought with him a CD-ROM (Creative Labs Quad Speed!!), 16-bit Sound Blaster sound card and 4mb of additional ram (good old days when you chose do you want expanded memory or extended memory) :p


OT: My lappy has 2GB... more than enough for what I use it for, gaming rig only has 4GB and needs at least another 4 to make me happy :)


404

---

### Post by Bandit on 2012-04-28
> **Linuxratty said:**
> LOL! me too! I was so excited!

LOL same here.. 

The specs of my systems over the past few years:

Tandy 1000HX 8086 4.77Mhz, 640k
Tandy 1000TL/2 i286 8Mhz, 720k
(big jump here, I loved my Tandys)
AMD 486DX 100 16MB
AMD K6-2 350 128MB
AMD k6-2 400 192MB (previous system, just did a upgrade)
Athlon 500Mhz 384MB
(another jump, was in Navy for a while, had a K62-450 Laptop with 192MB)
AthlonII 2GHz 2GB
Athlon 64 2Ghz 2GB
Athlon 64 3Ghz Dualcore 4GB
Phenom x4 2.5Ghz Quad 4GB

Thats a hand full of systems over the past 20 years for just little ole me. :guitar:

---

### Post by Bandit on 2012-04-28
> **not found said:**
> One of my happiest computing moments was when a friend of my dad (his tech support guy) came to our house and brought with him a CD-ROM (Creative Labs Quad Speed!!)......

I still got a working dual speed I used to keep around just to put into my system and listen to CDs.

---

### Post by OpenSourceRules on 2012-04-28
To be exact, this is an Acer Aspire 1690WLMi.  It has an Intel Pentium(R) M 715 processor(1.5GHz, 400 MHz FSB, 2MB L2 cache).  
I use Xubuntu because I like XFCE better than Gnome, LXDE and KDE.

---

