---
title: "CPU/Motherboard recommendations"
date: 2008-08-07
forum: The Cafe
---

### Post by ssamoon on 2008-08-07
Hey there,

I'm gettin ready to build a PC but I haven't done so in 5+ years, many new companies on the market these days, and I'm just hoping for a little advice.

I'm looking to use a full size ATX. Quieter is better. I already have a network card, CD-drive, monitor, and soundcard that I'll migrate from an old computer.

Also, any advice about power supply / case would be appreciated. Machine doesn't need to be too 'hardcore', just something respectable for a programmer-nerd to play around with that will hopefully last awhile and not make a ton of racket. I'd like keep the price as low as I can, say < 300 for the case, mobo, processor, power supply.

Was considering [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115052") and [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856167031")

Thanks in advance,

Sean

(PS. I'm planning on ordering everything from newegg.com, bonus points for things that they sell. Thanks!)

---

### Post by Dremora on 2008-08-07
I've had great luck with Nvidia chipsets and AMD CPUs, they may not be quite up to the same pace as Intel in some ways, but they are much better priced, and more reliable, Intel doesn't seem to support Linux as well as AMD does on consumer level stuff.

Nvidia GPU's have the fullest hardware accelerated OpenGL support, and probably will be the best performing cards for quite some time.

Lots of people jump up and down over the free "radeon" driver for ATI's cards, it barely works, it will probably stay that way for a couple years if I was guessing.

Nvidia's binary drivers are also the only ones that consistently survive through suspend/resume, where Intel and ATI's just explode. :P

I write this now on what will probably be the last Intel system I will ever own. :P

---

### Post by ssamoon on 2008-08-07
Another question:

How important is the watts for the power supply? Is 300W enough?

---

### Post by Dremora on 2008-08-07
> **ssamoon said:**
> Another question:

How important is the watts for the power supply? Is 300W enough?

Depends more on the amount of rail voltage.

Some power supplies claim, say 500 watts, but can really only handle 380 under load.

You may see some outfit saying their PSU is 500 Watts and "65% efficient" or something, meaning it can really only handle 325 watts ouput, ok thats a really horrible case, but it gets the point across.

What all will the supply be powering?

How much money do you want to spend?

I use a 500 Watt supply with 80% efficiency, it ran me $40, not the best, not the worst.

---

### Post by ssamoon on 2008-08-07
> **Dremora said:**
> Depends more on the amount of rail voltage.
What all will the supply be powering?

How much money do you want to spend?


Won't be anything exceptional in the computer, 1-2 hard drives, sound and video card, network card, cd burner. Fan or two. Looking to keep the machine quiet, as I may use it for recording music occasionally and loud systems annoy me.

< $200 for case, power supply, motherboard hopefully? Whatever is reasonable.

---

### Post by Erdaron on 2008-08-07
I've just built a cheap machine (RedArmor in my sig). PSU is an Antec EW380. The whole setup was around $250 (including shipping charges), and this included pretty much the whole computer (cpu, mobo, hdd, psu, case, video card).

Celeron 430 is a good CPU. Runs cool, does what you need it to, though a cheap Core 2 Duo can probably get more out of your machine.

My motherboard is built on Intel 945 chipset, and it worked perfectly with Ubuntu on first install - including on-board video and audio.

---

### Post by Dremora on 2008-08-07
> **ssamoon said:**
> Won't be anything exceptional in the computer, 1-2 hard drives, sound and video card, network card, cd burner. Fan or two. Looking to keep the machine quiet, as I may use it for recording music occasionally and loud systems annoy me.

< $200 for case, power supply, motherboard hopefully? Whatever is reasonable.

300 Watt would probably be alright for a standard desktop PC, I'd look for a 350 if you can find one for a few dollars more and want to be on the safe side.

75-80% efficiency at the least.

---

### Post by Dremora on 2008-08-07
> **Erdaron said:**
> I've just built a cheap machine (RedArmor in my sig). PSU is an Antec EW380. The whole setup was around $250 (including shipping charges), and this included pretty much the whole computer (cpu, mobo, hdd, psu, case, video card).

Celeron 430 is a good CPU. Runs cool, does what you need it to, though a cheap Core 2 Duo can probably get more out of your machine.

My motherboard is built on Intel 945 chipset, and it worked perfectly with Ubuntu on first install - including on-board video and audio.

945 chipset maxes at 3.25 GB of RAM, no matter what OS you use, just a warning...

---

### Post by Erdaron on 2008-08-07
> **Dremora said:**
> 945 chipset maxes at 3.25 GB of RAM, no matter what OS you use, just a warning...

If I'm using a bottom-shelf CPU (I know what I buying power-wise), I probably won't care about maxing out RAM. 2 GB does the job just fine. I haven't come even close to pushing this amount yet.

But suggestion duly noted should I upgrade the system in the future!

---

### Post by ssamoon on 2008-08-07
Thanks for the warning, I would like to have the option to go to 4 GB ram, and I'm also planning on getting something without a reduced cache size like a Celeron..

---

### Post by Dremora on 2008-08-07
> **ssamoon said:**
> Thanks for the warning, I would like to have the option to go to 4 GB ram, and I'm also planning on getting something without a reduced cache size like a Celeron..

I've been following something about 965, G33, and G35 chipsets with AMI BIOS malfunctioning quite badly on Linux, it seems the proper patches will land in time for intrepid though, but if you want to stay with Hardy, these wouldn't be a prudent choice.

It's always some damned thing....

I saw that you can get a Via C7D 1.5 Ghz with the motherboard included for $60 the other day...those max out at 2 gigs of RAM and have no PCI-E port, but they are cheap as hell...

---

### Post by zachtib on 2008-08-07
my $0.02

one of the above posters mentioned Intel not supporting Linux as well as AMD... I've never had a problem with Intel, and I've always advised people building Linux computers to go Intel as much as possible: CPU, Mobo, chipset, video, NIC, etc.

They are a little more pricey, but I've always felt they were worth it, the Core 2 line of CPUs are great

---

### Post by Dremora on 2008-08-07
> **zachtib said:**
> my $0.02

one of the above posters mentioned Intel not supporting Linux as well as AMD... I've never had a problem with Intel, and I've always advised people building Linux computers to go Intel as much as possible: CPU, Mobo, chipset, video, NIC, etc.

They are a little more pricey, but I've always felt they were worth it, the Core 2 line of CPUs are great

The Core 2 is good, the chipsets are god awful, in my experience anyway.

Anything branded other than Intel is asking for it, anything actually branded "Intel" motherboard wise is really really asking for it.

About the only people you want anything to do with if you go the Intel route is ASUS or Gigabyte, they don't appear to totally cheap out on the chipsets and ship with particularly buggy firmware.

---

### Post by zachtib on 2008-08-07
really? what chipsets have you used?  I've got a P35, never had an issue with it

---

### Post by Methuselah on 2008-08-07
I have a Gigabyte EP35C-DS3R mobo and a Core2 quad q6600 I bought for the machine I built for ubuntu.

The motherboard is DDR3 ready but has dual channel DDR2 as well and can take up to 8GB DDR2 (4GB DDR3).

It has built in RAID, ethernet and realtek HDA audio all of which were recognized by ubuntu without any work. 
Like you, I already had some of those laying about but it's hard to find a mobo without them and I wanted them to work if present.
It also has a sizeable number of USB, eSata and expansion slots (pcie, and pci) and many tweaking option in the BIOS.
And of course, it works with the processor.

No built in wifi or firewire though if that is important to you.

I thought it was a good buy at the time (several montsh ago) and I'm 100% happy with it.
However, I'm certain there are newer options now.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128082](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128082)

---

### Post by Dremora on 2008-08-07
> **zachtib said:**
> really? what chipsets have you used?  I've got a P35, never had an issue with it

Oh, on some newish Intel chipsets, you get lots of firmware bugs and in some cases Linux won't even boot unless you turn ACPI off.

It eventually gets sorted out by the kernel team, but by then, the board is a year or two old, and there are more out that won't work right.

I've never had Linux fail to work properly on anything from AMD/Nvidia

I've got a G35 right now, the stupid thing has a lot of problems, and if you don't use kernel 2.6.26 it doesn't work well, and lower than 2.6.24 won't even boot.

---

### Post by days_of_ruin on 2008-08-07
I think the asus mobo with splashtop are cool.I don't have one
tho so I don't know what they are like.

---

### Post by pparks1 on 2008-08-07
My last two linux home builds have both been AMD processors.  While I admit that Intel has the performance edge right now, I just find that my Linux machines don't need it like a Windows gaming box.  

I really like my AMD64X2 processor.  The power consumption is very low and the fan is quite quiet and the chip runs very cool.    I also have one of the Antec Sonata II cases.  They come with a 400-500 watt power supply depending upon what model you buy.  it's easy to work with, very quiet and very nice cooling.  I've just added my setup to my sig block.

---

