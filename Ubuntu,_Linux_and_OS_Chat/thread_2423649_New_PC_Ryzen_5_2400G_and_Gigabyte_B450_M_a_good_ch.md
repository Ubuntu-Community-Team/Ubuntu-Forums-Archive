---
title: "New PC: Ryzen 5 2400G and Gigabyte B450 M a good choice?"
date: 2019-07-27
forum: Ubuntu, Linux and OS Chat
---

### Post by jhanarato on 2019-07-27
Hello!

I'm looking into getting a PC custom built. I'd like to use an AMD Ryzen 5 2400G APU and a Gigabyte B450 Aorus M. I've done a few web searches and have not found any major issues.

Is this a good choice? I don't mind tinkering if need be.

Cheers,

J.R.

---

### Post by backspin on 2019-07-27
I just put together a Ryzen CPU system with X570 motherboard, and have had only one major issue.  You should be fine with the B450.

---

### Post by jhanarato on 2019-07-27
Good to hear. What was the issue you had?

Cheers,

J.R.

---

### Post by oldos2er on 2019-07-28
I have that same processor, no problems at all.

---

### Post by jhanarato on 2019-07-28
> **oldos2er said:**
> I have that same processor, no problems at all.

Yeah, I think the APU should be fine. Motherboards on the other hand are a bit of a mystery to me. Would I be right in thinking that the chipset (B450) is probably the most important factor?

---

### Post by CatKiller on 2019-07-28
> **jhanarato said:**
> Yeah, I think the APU should be fine. Motherboards on the other hand are a bit of a mystery to me. Would I be right in thinking that the chipset (B450) is probably the most important factor?
Yes and no.

The Zen chipsets are designed by AMD, and they provide the bulk of the UEFI software through their AGESA. That controls things like voltages, speeds, memory access, and so on. To that extent, if any models work, they all should. Bugs in implementation are likely to be shared, too.

Other devices on the motherboard - things like WiFi devices, sensors, LEDs, onboard sound, and so on - can vary significantly from model to model. There are some of those elements that could be poorly supported under Linux. It might boot & run fine, but be lit up like a Christmas tree with no sound, for example.

Really cheap stuff might cut corners to keep the costs down, which means it's non-standard and untested. Gamer stuff, put in as a "value add," tends to be non-standard and only tested with Windows. Middle-of-the-road professional stuff tends to be standardised and well-supported, in my experience.

---

### Post by jhanarato on 2019-07-29
> **CatKiller said:**
> 

Really cheap stuff might cut corners to keep the costs down, which means it's non-standard and untested. Gamer stuff, put in as a "value add," tends to be non-standard and only tested with Windows. Middle-of-the-road professional stuff tends to be standardised and well-supported, in my experience.

My use-case is an office machine. Most of my work is done in Firefox with Google Docs, Wordpress, Gmail, etc. I also do a bit of Python hacking and would like a machine that will run an IDE like PyCharm without struggling. Having used Linux as my primary OS since the late nineties, this is the first PC I'm actually building with the OS in mind. Up until now my PCs have just been repurposed Windows machines.

I discovered a couple of useful websites - PcPartPicker.com and LogicalIncrements.com. I chose the Ryzen as better value than the Intel Coffee Lake CPUs. Logical Increments suggested the Gigabyte mobo to go with the Ryzen (see the "minimum tier"). I'm planning to add an SSD, 16GB dual channel DDR4 RAM and a PCIe wifi card. I use a standing desk with a relatively small shelf for the tower so I'm going with a smaller tower and micro-ATX mobo.

So, any suggestions are welcome.

---

### Post by Yellow Pasque on 2019-07-29
I recently built a system with a Gigabyte B450 Aorus Wifi Pro and a Ryzen 2400G. I use Debian unstable/sid as my main distro, and everything I used worked there (audio, NVMe, LAN, SATA). I also installed KDE Neon's latest version (based on Ubuntu 18.04) and quickly tested the IGP and wireless there since I don't use them on my main install.

The only thing that didn't work is the ITE sensor chip. ITE doesn't open-source their documentation, so the voltage and temps from that sensor were garbage. (I knew that when I bought it. As long as the BIOS has good fan control and I can see the CPU temp, I'm happy).

---

### Post by CatKiller on 2019-07-29
> **jhanarato said:**
> So, any suggestions are welcome.
I use a Gigabyte X470, and everything's been fine, although I needed a bios update to be able to turn off the LEDs. After a quick look at the specs of the one you're looking at, the only thing I'm not sure about is the onboard network port: I don't have any experience with non-Intel network devices. But you're going to be using a separate one, anyway. Looks to me like it should be fine.

---

### Post by CatKiller on 2019-07-29
> **Yellow Pasque said:**
> The only thing that didn't work is the ITE sensor chip. ITE doesn't open-source their documentation, so the voltage and temps from that sensor were garbage. (I knew that when I bought it. As long as the BIOS has good fan control and I can see the CPU temp, I'm happy).

There is an it87 kernel module that works with most of those sensors. It never got upstreamed and the person that created it didn't want to maintain it any more, so it got abandoned. You can still find it, though, and it will probably work, at least for now. 

The cpu temperature is also reported by k10temp, so you're still getting good readings without using it87.

---

### Post by jhanarato on 2019-07-29
> **CatKiller said:**
> Looks to me like it should be fine.

OK, wish me luck then. Thanks all!

---

### Post by Yellow Pasque on 2019-07-30
> **CatKiller said:**
> There is an it87 kernel module that works with most of those sensors. It never got upstreamed and the person that created it didn't want to maintain it any more, so it got abandoned. You can still find it, though, and it will probably work, at least for now.

[https://github.com/a1wong/it87](https://github.com/a1wong/it87)
Yeah, I know all about that and I tried it, but the voltage values appear to be garbage. I'm not sure about the temps. temp2 and temp3 appear to always be 37C. 
I don't have a case fan hooked up at the moment to test the fan speeds:
```
$ sensors
it8792-isa-0a60
Adapter: ISA adapter
in0:          +1.77 V  (min =  +0.00 V, max =  +2.78 V)
in1:          +1.24 V  (min =  +0.00 V, max =  +2.78 V)
in2:          +1.09 V  (min =  +0.00 V, max =  +2.78 V)
+3.3V:        +1.67 V  (min =  +0.00 V, max =  +2.78 V)
in4:          +1.24 V  (min =  +0.00 V, max =  +2.78 V)
in5:          +1.11 V  (min =  +0.00 V, max =  +2.78 V)
in6:          +2.78 V  (min =  +0.00 V, max =  +2.78 V)  ALARM
3VSB:         +1.67 V  (min =  +0.00 V, max =  +2.78 V)
Vbat:         +1.64 V  
fan1:           0 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +42.4°C  (high = +70.0°C)
Tctl:         +42.4°C  
```

---

### Post by andrew.46 on 2019-07-30
Is this still a good time to buy a 2400G when the 3400G has just come out? Certainly if you are after a bargain the 2400G prices should be substantially lower now...

---

### Post by Yellow Pasque on 2019-07-31
> **andrew.46 said:**
> Is this still a good time to buy a 2400G when the 3400G has just come out? Certainly if you are after a bargain the 2400G prices should be substantially lower now...

The 3400G offers a bit more clock speed and a somewhat beefier cooler over the 2400G. They're about $20 apart right now from a quick check of prices. I don't think either one of them is a bad buy. I didn't want to wait for the 3400 because I was using an old Athlon X2 system and finally had the funds to replace it.

---

### Post by andrew.46 on 2019-07-31
> **Yellow Pasque said:**
> The 3400G offers a bit more clock speed and a somewhat beefier cooler over the 2400G. They're about $20 apart right now from a quick check of prices. I don't think either one of them is a bad buy. I didn't want to wait for the 3400 because I was using an old Athlon X2 system and finally had the funds to replace it.

Fair enough, I have only just finished selling off [my own Athlon system]("http://www.andrews-corner.org/builds/Athlon.html") so I know where you are coming from. It is actually a little surprising how much these older systems can accomplish with a judicious choice of Distro and applications...

---

### Post by emanual4real on 2020-01-15
I've got gigabyte b450 aorus pro wifi mini itx and having nothing but problems on Ubuntu 18.04.  Worked fine on initial install for a few days, then constant boot issues.  Still haven't resolved it.  Boot repair usb says I'm booting with UEFI but no UEFI partition.  Still researching.

---

### Post by CelticWarrior on 2020-01-17
> **emanual4real said:**
> (...) Boot repair usb says I'm booting with UEFI but no UEFI partition.  Still researching.

Simply not possible. UEFI mode requires an ESP (EFI System Partition). It may or may not reside in the same drive where the OS main partition is. Please check.

---

### Post by axenedu on 2020-02-16
I bought a Ryzen 5 3400G with a Gigabyte B450 AORUS M Motherboard. It doesn't detect HDMI output at all. I have the latest bios version of the motherboard, and I tested Ubuntu 19.10 with Kernel 5 and no results. So in my opinion, Bad Choice.

---

### Post by mörgæs on 2020-02-16
Does the daily build of 20.04 work better?

---

### Post by mastablasta on 2020-02-19
> **axenedu said:**
> I bought a Ryzen 5 3400G with a Gigabyte B450 AORUS M Motherboard. It doesn't detect HDMI output at all. I have the latest bios version of the motherboard, and I tested Ubuntu 19.10 with Kernel 5 and no results. So in my opinion, Bad Choice.


so HDMI output works in BIOS and possibly GRUB but not in (desktop) Ubuntu?

i would boot to text mode if possible and troubleshoot from there. just curious - does it work if you boot with nomodeset boot option? 

also as suggested 20.04 - does it work? 

eventhough this APU was supported in the old kernel.

---

### Post by DuckHook on 2020-02-19
The author of this thread left the building months ago. Please people: don't necromance old threads. But since this one has now clawed itself out of its grave, I suppose it must be permitted to shuffle along until it expires.

---

### Post by shurur9 on 2020-08-10
The board is only 2 years old!!..and selling big right now to those not interested in building on the bleeding edge.

I don't see why input on it is such a bad thing.

I just got the aorus b450 elite with amd ryzen 2600.
It ran great on the old hd with ubuntu 32 bit version 18...came right up and updated 2-3 years of updates!

Getting/finding useful help getting a new 64 bit ubuntu OS is maybe another thing.

I fixed my problem with making a bootable usb drive by finding help on another site. Supposedly I cannot list it on this site......

Well I am off to search for where the stickies..how-tos..are hidden on how to get ubuntu 64 to load on my board....maybe I will get another message from an admin that I can't reply to...

But anyway..this is a great board now that others on the forum have worked out all the bugs for me!! This is why I love you guys...the helpful ones anyway..

 It is Especially easy if you are just running a little gt 1700 gpu!!

---

### Post by QIII on 2020-08-10
Reburied.

RIP.

---

