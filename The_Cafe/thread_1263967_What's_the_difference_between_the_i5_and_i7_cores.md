---
title: "What's the difference between the i5 and i7 cores?"
date: 2009-09-11
forum: The Cafe
---

### Post by Blacklightbulb on 2009-09-11
So I getting confused. 

Are the i5 cores similar to i7 cores but with hyper threading and other functions disabled? 

Which is really faster, the i7 I suppose?

The i5 are cheaper right?

Are they compatible with Ubuntu and Arch?

---

### Post by mcduck on 2009-09-11
Depends on the actual core. i7 and i5 are marketing names, and thus more related to the processor's price than it's actual features.

i7 is the marketing name for high-end CPU's, i5 is below that and i3 below i5.

The first i5 cores (Lynnfiled) are indeed nerfed versions of Bloomfield cores (sold as i7), with some features like Hyperthreading disabled. Clarkdale core supports Hyperthreading, and is used for both i3 and i5.

All of these are supported by Ubuntu (and pretty much every Lnux distribution), just like any other x86-compatible processors.

---

### Post by Blacklightbulb on 2009-09-11
> **mcduck said:**
> Depends on the actual core. i7 and i5 are marketing names, and thus more related to the processor's price than it's actual features.

i7 is the marketing name for high-end CPU's, i5 is below that and i3 below i5.

The first i5 cores (Lynnfiled) are indeed nerfed versions of Bloomfield cores (sold as i7), with some features like Hyperthreading disabled. Clarkdale core supports Hyperthreading, and is used for both i3 and i5.

All of these are supported by Ubuntu (and pretty much every Lnux distribution), just like any other x86-compatible processors.

Thanks for clearing that out.

---

### Post by markbuntu on 2009-09-11
i3 and i5 chips are i7 chips that have semi-serious problems but can be reconfigured to still work. 
It costs a lot of money to fab these chips so they need to sell everything they can.
The rest are tossed on the trash heap.

It is a common thing in the chip fab world.

---

### Post by Skripka on 2009-09-11
The BIG difference is that i5 memory controller is now like AMD-on the CPU die, so the memory talks directly to the CPU, and no through a middle-man.  Also, i5 has the PCie slot controller directly on the CPU die, again less middle-men-so the GPU and the attached memory can talk directly to the CPU-fewer middlemen.

Theoretically these should make BIG performance differences...practically, the performance of i5 over Core2: well you're better off buying a Core2Duo than an i5 according to benchmarks with Win7.

[http://arstechnica.com/hardware/news/2009/09/intel-launches-all-new-pc-architecture-with-core-i5i7-cpus.ars](http://arstechnica.com/hardware/news/2009/09/intel-launches-all-new-pc-architecture-with-core-i5i7-cpus.ars)


They are VERY different in architecture from (the 1st gen) i7-or anything else out there and are not "nerfed".  Intel has ALWAYS blocked off features/protocols as a way of subtley differentiating products.

---

### Post by Orographic on 2010-01-11
I'm thinking of getting this i3 setup later this year. Might wait a little while to ensure support, as the motherboard is still quite new.

So, 10.04 should support the i3 no probs? 


My possible new system: 

Gigabyte GA-H55M-UD2H MB

Corsair VS2GB1333D3 2GB (1333MHz) DDR3 RAM (x2)

LG Duallayer DVD Burner Sata Black

Seagate SATA2 500GB Harddisk 7200rpm (2) - one just as a spare with Windows on it (no Raid)

Microsoft Windows 7 Home Premium 64bit oem (for spare drive)

Intel CORE i3 530 or better? (graphics on chip)

Logitech 350 USB DESKTOP mouse/keyboard

Coolermaster RC-690 Black with 460W PSU

---

### Post by iskarion on 2010-01-15
> **Orographic said:**
> I'm thinking of getting this i3 setup later this year. Might wait a little while to ensure support, as the motherboard is still quite new.

So, 10.04 should support the i3 no probs? 
I don't think that 10.04 will fully support the Clarkdale i3/i5 CPUs. At least not the integrated graphics. Support for these has been recently added to kernel 2.6.33. ( [http://www.phoronix.com/scan.php?page=news_item&px=Nzc4OQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzc4OQ) )
But Ubuntu 10.04 is based on kernel 2.6.32.

I hope that Canonical will backport this, as I'm also planning to buy a Clarkdale based system this year. Alas, so far I found no indication, that backporting the Clarkdale IGP support is planed.

---

### Post by LowSky on 2010-01-15
Integrated graphics are the worst... be a real geek and get an Nvidia Graphics card. A cheap decent  one will be under $50

---

### Post by Skripka on 2010-01-15
> **LowSky said:**
> Integrated graphics are the worst... be a real geek and get an Nvidia Graphics card. A cheap decent  one will be under $50

This.  What is the point of getting a $200 CPU, and a $300 motherboard, and $150+ worth of DDR3 only to use integrated crap-hics?

---

### Post by Marlonsm on 2010-01-15
> **Skripka said:**
> This.  What is the point of getting a $200 CPU, and a $300 motherboard, and $150+ worth of DDR3 only to use integrated crap-hics?

Those graphics are (much) better than previous ones from Intel, for (cheaper) laptops they are great.
But for desktops there is no excuse.

---

### Post by Skripka on 2010-01-15
> **Marlonsm said:**
> Those graphics are (much) better than previous ones from Intel, for (cheaper) laptops they are great.

I would not describe IGPs as "great", especially if you have an Atom CPU and are not plugged into a wall.  "Adequate" for most uses aside from HD YouTube vids, sometimes.

---

### Post by Marlonsm on 2010-01-15
> **Skripka said:**
> I would not describe IGPs as "great", especially if you have an Atom CPU and are not plugged into a wall.  "Adequate" for most uses aside from HD YouTube vids, sometimes.

Actually most reviews say it is very capable of HD vids, including ones from Youtube. For most users it should be more than enough, specially when it's along with a not-bad CPU like the i3 and the i5.
And also, in laptops, battery life is important, and IGP is better for it.

---

### Post by HunkirDowne on 2010-03-28
I realize this thread is a little stale...  Were these comments relevant to the Arrandale i5 and Clarkfield i7?  The i5 has two cores and the i7 has four.  I'm specifically looking at the processors for laptops.

i5-520M
i5-540M
i7-620M
i7-720QM
i7-820QM


Thanks

---

### Post by tgalati4 on 2010-03-28
According to Intel, the difference is one star.

---

### Post by teh603 on 2010-03-29
> **LowSky said:**
> Integrated graphics are the worst... be a real geek and get an Nvidia Graphics card. A cheap decent  one will be under $50nVidia isn't going to be the best choice until Nouveau finally gets ready for release. As it is, it doesn't support 3d accelleration, and Plymouth doesn't work with the binary blob. So you have the choice of proper 3d accelleration and an ugly bootsplash, or no 3d and a decent bootsplash.

---

### Post by MaxIBoy on 2010-03-30
My (brand new) i5 has hyperthreading, so I suppose it's a Clarkdale.

Anyway, it's the same basic core and variations thereon (with/without features like hyperthreading, virtualization acceleration, on-CPU graphics, clock speed, and number of cores.) There are i3s, i5, i7s and i9s. I suppose even numbers are uncool.

It's much the same story with the variations on basically every other processor series ever made. For example, Celerons were actually nerfed Pentiums (and could easily be overclocked back to Pentium levels.)

---

### Post by spoons on 2010-03-30
> **Skripka said:**
> I would not describe IGPs as "great", especially if you have an Atom CPU and are not plugged into a wall.  "Adequate" for most uses aside from HD YouTube vids, sometimes.

The Atom GPU is based off of the GMA 950 - an old DirectX 9.0 part without transform & lighting, vertex shaders, or GLSL. It has no HD decoding capabilites.

The Core i5/i3 GPU is a 12-pipeline DirectX10/OpenGL2.1 part with a core clock up to 900mhz. It also has full HD decoding capabilities.

---

### Post by Glucklich on 2010-03-30
> **tgalati4 said:**
> According to Intel, the difference is one star.

I lol'ed :P

---

### Post by teh603 on 2010-04-02
> **spoons said:**
> The Atom GPU is based off of the GMA 950 - an old DirectX 9.0 part without transform & lighting, vertex shaders, or GLSL. It has no HD decoding capabilites.

The Core i5/i3 GPU is a 12-pipeline DirectX10/OpenGL2.1 part with a core clock up to 900mhz. It also has full HD decoding capabilities.To be honest, if you're using the Atom GPU, you're probably using it on a netbook and who uses netbooks for high-end gaming and HD youtube videos anyway? They're designed for a student or business traveller. You don't need much of a GPU for OpenOffice.

---

