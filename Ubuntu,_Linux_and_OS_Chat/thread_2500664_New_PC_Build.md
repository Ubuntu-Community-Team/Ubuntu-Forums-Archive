---
title: "New PC Build"
date: 2024-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2024-09-08
I've been asked to build a new pc - which in itself is not a problem.  However, I remember seeing a little while ago something about a new intel chip designed(? - probably got that wrong) for windows 11 that caused problems for a ubuntu build.  What are the chip types I should be looking out for (to avoid) for a new ubuntu build?  (Probably going to base this build on a i5).

---

### Post by Quarkrad on 2024-09-08
Actually, just seen a build with Ryzen 5 4600G - will drivers for this be a problem?  (Always built machines based on intel).

---

### Post by oldfred on 2024-09-08
I believe the issue was overheating whether Windows or Linux with 13 & 14 Gen chips.
But only i7 & i9. 
May be a default overclock on motherboard.

If choosing one of those check for more details, as not sure what models, motherboards or settings may be required.

---

### Post by 1fallen on 2024-09-08
> **Quarkrad said:**
> Actually, just seen a build with Ryzen 5 4600G - will drivers for this be a problem?  (Always built machines based on intel).
Nope all should be good to go, stay on a at least 5.8 kernel.

I've seen threads here over the past couple of months with some quirks on kernel 6.8.

I flat love mine:
```
CPU:  Info: 6-core model: AMD Ryzen 5 5600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 827 min/max: 400/4280 cores: 1: 400 2: 400 3: 400 4: 400
    5: 2251 6: 400 7: 2014 8: 400 9: 2060 10: 400 11: 400 12: 400



```

And Sorry but I'm a nVidia guy, no problems for me on any nVidia driver:
```
Graphics:  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] driver: nvidia
    v: 560.35.03
  Device-2: AMD Cezanne [Radeon Vega Series / Radeon Mobile Series]
    driver: amdgpu v: kernel



```

Good Luck with your build though....no matter which platform you choose.

---

### Post by him610 on 2024-09-08
Over the past eighteen years, I have built four systems with AMD processors and upgraded one. Never have I experienced any issues with AMD processors (Athlon 64 X2, Athlon 5350, A9-9400, Ryzen 5 2600, Ryzen 5 5600G) using software and drivers provided by Ubuntu.
Have fun building your new machine.

---

### Post by werewulf75 on 2024-09-08
Never had a problem with AMD CPUs and Radeon GFX and Linux yet, even on old AMD Athlon64 X2.

---

### Post by TheFu on 2024-09-09
The only issue with Ryzen is that it is very picky about having "matched" RAM.  That means RAM kits with all the sticks bought at the same time, in the same bundle/package.

I had a Ryzen 2600 and initially put 16GB of G.Skill DDR4 3200Mhz RAM into it. A year later, my workloads had grown to use 15GB of that RAM, so more was needed. Bought 16GB more with the exact same SKU from the manufacturer - same specs across the board. It was the same RAM.  But it wouldn't boot passed the BIOS screen.  I knew Ryzen was picky, so I started researching solutions and asking for help from Asus (the motherboard vendor).  The solution was to slow the RAM clock speed until it was stable enough.  So, I did that. It wasn't until 2666 Mhz that the system would stay booted for at least a week.  I ran like that for a year.  
I should say.  1 pair (2x8G) of RAM worked perfect at 3200Mhz.
The other pair (2x8G) of RAM also worked perfect at 3200Mhz.  Both sets together were unstable at any speed faster than 2666Mhz.

Then I replaced another computer with a Ryzen 5600G. On purpose, I bought the exact same motherboard I already had. I wanted to reuse the knowledge I'd already gained on that specific B450 motherboard.  RAM was cheaper, so I bought 32G (2x16G) of RAM, also G.Skill 3200Mhz.  It "just worked".  On a weekend, I swapped the RAM around between the 2 systems.  The instability followed where ever I put the 4x8GB of RAM running at 3200Mhz.

About a year later, I decided the 40% performance increase with a 2600-->5600G upgrade (literally, just the CPU was changed), was worth $100 and there was a deal on 5600G for a few days at $99. Bargain!  The CPU upgrade was smooth, fast, and worked perfectly.  I also got to pull my nVidia 1030 GT GPU from the system, saving nvidia hassles, instability, and power use.  The 1030 is a very low-end GPU that I was forced to buy when nVidia decided to drop driver support for my prior, working fine, 7200GS GPU.  I never wanted the 1030, but I'd been buying cheap nvidia GPUs since the early 2000s.  The built-in GPU on the Ryzen 5600G is more capably than the 1030GT and drivers for it have been included in the linux drivers since 5.8.x kernels. Basically, it just works.

I know nothing about the 4xxxG CPUs.  I'd have to compare price to cost to performance to see if it made sense to bother with a less capable Ryzen CPU.  Recently, there have been some 5500GX Ryzens on the market for a fair price. They are a little slower than the 5600G, but more available from AMD. We all have budget limitations.  At least with an AM4 socket, CPU-only upgrades are truly CPU-only upgrades, so doubling the performance will be possible when the 57xx and 58xx CPUs become cheap on the used market.

I switch between AMD and Intel CPUs based on which has the most value for my USD.  I also look at max power use, since power isn't dirt cheap here.  Replacing a 1st gen Core i7 with that Ryzen 2600 saved me about $10-15 every month in the power bill.  I retired 2 computers and put all that workload onto the 65W Ryzen.  That reduced cooling needed, and the savings rippled other places too. Basically, the Ryzen system (CPU, RAM, MB) paid for itself in lower power costs in about 24 months.

Right now, some Intel CPUs are attractively priced for the rated performance, so it isn't so clear. The iGPUs in the Ryzens ARE much better than the iGPUs from Intel.  That might be a consideration for some.  Neither are gaming system GPUs, so don't expect that, but my 5600G can transcode in hardware to either h.264 or h.265 without impacting the CPU utilization.  The quality of the encoding sucks even with very large file sizes allowed. Since I don't currently have any desktop Intel iGPUs that are capable of video encoding, I can't say anything about the performance or quality of the results.  I do have an 11th gen core i5 laptop. I haven't tried using the iGPU for video encoding. Hummm.

I do understand that newer AM4 motherboards are less picking about RAM.
```
$ inxi -bz
System:
  Kernel: 5.15.0-119-generic x86_64 bits: 64 Desktop: FVWM2 2.6.8 
  Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: **ROG STRIX B450-F** GAMING v: Rev 1.xx 
  serial: <filter> UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:
  6-Core: AMD **Ryzen 5 5600G with Radeon Graphics** type: MT MCP speed: 4209 MHz 
  min/max: 1400/4200 MHz 
Graphics:
  Device-1: AMD driver: **amdgpu** v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: **amdgpu**,ati 
  OpenGL: renderer: **AMD RENOIR** (DRM 3.42.0 5.15.0-119-generic LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6 
Network:
  Device-1: [B]Intel I211 Gigabit Network driver: igb 
[/B]
```
Oh ... and if you can, get an Intel NIC built-in.  Saves all sorts of hassles.

Looking at the inxi above, I should probably check for a BIOS update. Yep, there's a 2024/03/22 update. When I first bought the motherboard, BIOS upgrades were really easy, over the internet. That capability was removed. Now the update has to be done using a FAT32 USB flash drive, which is a bit of a hassle for me.  At least because I have 2 identical MBs, I can stage the upgrades - do a less critical system first - see how it goes.

---

### Post by him610 on 2024-09-10
> I do understand that newer AM4 motherboards are less picking about RAM.
```

inxi -Mmxxz
Machine:
  Type: Desktop Mobo: ASRock model: B450M/ac serial: <filter>
    UEFI: American Megatrends v: **P8.01 date: 03/13/2023**
Memory:
  RAM: total: 22.84 GiB used: 3.1 GiB (13.6%)
  Array-1: capacity: 128 GiB slots: 4 EC: None max-module-size: 32 GiB
    note: est.
  Device-1: DIMM 0 size: 4 GiB speed: 2133 MT/s type: DDR4
    manufacturer: Crucial part-no: CT4G4DFS8213.M8FB
  Device-2: DIMM 1 size: 8 GiB speed: 2133 MT/s type: DDR4
    manufacturer: Crucial part-no: CT8G4DFS8266.M8FD
  Device-3: DIMM 0 size: 4 GiB speed: 2133 MT/s type: DDR4
    manufacturer: Crucial part-no: CT4G4DFS8213.M8FB
  Device-4: DIMM 1 size: 8 GiB speed: 2133 MT/s type: DDR4
    manufacturer: Crucial part-no: CT8G4DFS8266.M8FE

```
MB Bios code upgraded about six months ago.

---

### Post by TheFu on 2024-09-10
2133 MT/s RAM is far below the speed that AM4 is capable.  Remember that Ryzen performs better with faster RAM.  The specs on my MB and CPU say 3200Mhz is the speed.  I didn't get two different sets of 2x8GB RAM (total 32GB) to be stable until I slowed it to 2666Mhz. I could feel and measure the performance difference between the 2 different speeds, after I replaced all the RAM with with 2x16GB sticks at 3200Mhz.

Have 2 systems like this now:
```
Memory:    RAM: total: 30.71 GiB used: 4.76 GiB (15.5%) 
           Array-1: capacity: 128 GiB slots: 4 EC: None max module size: 32 GiB note: est. 
           Device-1: DIMM_A1 size: No Module Installed 
           Device-2: DIMM_A2 size: 16 GiB speed: 3200 MT/s type: DDR4 manufacturer: G Skill Intl part-no: F4-3200C16-16GVK 
           Device-3: DIMM_B1 size: No Module Installed 
           Device-4: DIMM_B2 size: 16 GiB speed: 3200 MT/s type: DDR4 manufacturer: G Skill Intl part-no: F4-3200C16-16GVK
```
I need to reboot and assign 8G of that RAM to the iGPU to use it more like a full GPU just with fewer pipelines.

Read that the 4600G and 5600G have the exact same iGPU inside. Only 7 GPU cores, but that's better than spending $300 for a discrete, if you are tight on money or don't really want a gaming GPU.  The 4600G has a slightly slower CPU.

---

