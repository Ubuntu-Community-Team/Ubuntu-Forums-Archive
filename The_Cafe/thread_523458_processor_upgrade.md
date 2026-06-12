---
title: "processor upgrade"
date: 2007-08-11
forum: The Cafe
---

### Post by rkrug on 2007-08-11
I just got an old Gateway gp6-400c, and I'm working on upgrading it. I already put in a CD burner and I ordered some RAM for it, and everything is going fine.

The only problem is that it has an Intel Celeron processor. I have another gateway computer and I want to take the Pentium 4 out of that and put it in the GP6-400c. 

How do I find out if the GP6's motherboard is compatible with the processor from the newer Gateway computer?

If it helps, this is what I know about the processor (or mobo, I forget which this is :() currently in the GP6:

Intel 440 chipset
Memory controller: 82443BX/DX/ZX
I/O controller: 82371EB (PIIX4E)

---

### Post by WishingWell on 2007-08-11
> **rkrug said:**
> I just got an old Gateway gp6-400c, and I'm working on upgrading it. I already put in a CD burner and I ordered some RAM for it, and everything is going fine.

The only problem is that it has an Intel Celeron processor. I have another gateway computer and I want to take the Pentium 4 out of that and put it in the GP6-400c. 

How do I find out if the GP6's motherboard is compatible with the processor from the newer Gateway computer?

If it helps, this is what I know about the processor (or mobo, I forget which this is :() currently in the GP6:

Intel 440 chipset
Memory controller: 82443BX/DX/ZX
I/O controller: 82371EB (PIIX4E)

Nope, it won't work, they use two completely different sockets.

The Gateway gp6-400c sports a socket 370 with a Celeron Mendocino CPU running at a whopping 400Mhz at 66Mhz bus speed.

The fastest CPU you can put on that board is a Celeron Mendocino 533 and i believe the max memory to be 384 (but it's possible that it's 512, it's been a while since i dealt with those, it's from 1998 after all).

Is the other computer broken? Because if it's not it's better than the old one in every conceivable way.

---

### Post by SomeBuntu on 2007-08-11
If both motherboards support the same slot (pin configuration like 775) then swapping CPU's shouldn't be a problem. Don't forget to use some good quality thermal paste between the CPU and heat sink when reassembling.

---

### Post by starcraft.man on 2007-08-11
That's prettttty old. I'd salvage/scalp it for parts and build a new PC (rather than upgrade with limited options). A small budget of 5-600 dollars can get you decent parts and an acceptable machine for today. That's just my opinion though, have fun.

---

### Post by a12ctic on 2007-08-12
Even less than that... You can get dual core and diskreet graphics for under 600.

amd 3600+
2gb ddr2 
8600GTS

will probably run you about ~500 depending onthe harddrive/mobo you use.

---

### Post by rkrug on 2007-08-12
I'm getting a new computer next month, but right now I have three computers. The one that I am on now, which is good, an old gateway tower thats video card is broken, and the GP6.

This is more of a little project for me than an attempt to make a computer for daily use. I want to see how fast I can get it to run.

---

### Post by WishingWell on 2007-08-12
> **rkrug said:**
> I'm getting a new computer next month, but right now I have three computers. The one that I am on now, which is good, an old gateway tower thats video card is broken, and the GP6.

This is more of a little project for me than an attempt to make a computer for daily use. I want to see how fast I can get it to run.

Well, as i said before, the best you can put in that motherboard is a Celoron Mendocino 533, not much of an upgrade and probably hard to find.

Don't try to use the newer Coppermines in that motherboard, they will fit but they are not pin compatible, either it just won't work or it will destroy the CPU/motherboard or both.

If i were you i'd overclock the current CPU as much as possible and fill the three slots with 128MB each for 384MB of memory total.

Using PC-100 memory you can overclock the CPU by raising the bus speed, probably not all the way up to 100Mhz but at least quite a bit, i don't know if you'll need to change the divider for PCI and AGP for them to work, i've seen some corruption when the PCI-IDE interface has been overclocked to far.

It's not a bad way to learn about hardware but i'm afraid the hardware is so old that most of what you'll learn won't even be applicable on modern hardware.

---

### Post by jgrabham on 2007-08-12
> **a12ctic said:**
> Even less than that... You can get dual core and diskreet graphics for under 600.

amd 3600+
2gb ddr2 
8600GTS

will probably run you about ~500 depending onthe harddrive/mobo you use.

Have a look at my sig - cost about £175 - $350!!!

---

