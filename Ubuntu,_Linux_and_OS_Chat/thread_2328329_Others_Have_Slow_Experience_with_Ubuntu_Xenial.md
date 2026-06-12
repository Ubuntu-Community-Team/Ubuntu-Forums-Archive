---
title: "Others Have Slow Experience with Ubuntu Xenial?"
date: 2016-06-20
forum: Ubuntu, Linux and OS Chat
---

### Post by SciGuy1872 on 2016-06-20
Hi.  I was just wondering if anybody else has a slow experience with Ubuntu Xenial (Firefox, Chromium, typing, window commands, etc.)?--takes about three or four seconds. This desktop ran Precise perfectly (2.4 GHz, 1.2 GiB RAM, Nvidia GeForce FX 5200; right now, I'm using Intel® 845G x86/MMX/SSE2 for graphics--I'll switch to the other in a while).  Xenial is new, so maybe I just need to wait a couple of months for the OS to smooth out.

Just wondering,
                   Anthony

---

### Post by Bucky Ball on 2016-06-20
> **SciGuy1872 said:**
> I was just wondering if anybody else has a slow experience with Ubuntu Xenial (Firefox, Chromium, typing, window commands, etc.)?

No. Just fine and fast here, but the caveat is I'm not using a full-blown install. :)

I wouldn't have thought you'd get too far with 1.2Gb of RAM, though, particularly if you have a heap of apps open and a ton of tabs open in Firefox. Maybe try a lighter flavour, Xubuntu perhaps.

---

### Post by ajgreeny on 2016-06-20
I have it running in a VirtualBox VM and even there it is running absolutely fine with no difficulties at all running on an Intel i5-3750K 4GB ram out of 8GB on host.

If it runs as well as it does as a VM, I'm sure it would run even better as a hard-metal version.

I suspect that ypur graphics and low RAM are your main problems, but other users may have other ideas.

---

### Post by mastablasta on 2016-06-20
RAM and GPU are holding you down

there were some issues i read online (rambeing eaten, CPu usage high) but you would notice that using top command or looking into system process manager. uusally the reis a library or app causing it.

---

### Post by grahammechanical on 2016-06-20
Is this a discussion thread or a support thread?

If discussion, then 16.04 is running fine on my Intel core 2 duo 2.40 GHz + 1 GB RAM + Nvidia GT200 with 1 GB video memory.

If support, then open the details page. If graphics is listed as "llvmpipe" then you are using a fall back open source video driver that approximates Unity 3D on video adapters that cannot do the hardware accelerated 3D video rendering that Unity 3D requires.

With Ubuntu 12.04 if the graphic adapter could not run Unity 3D then Unity 2D was installed and it used Metacity and not Compiz as the window manager. But Unity 2D is no longer available. We get llvmpipe instead and it is slow even on video adapters that can run Unity 3D.

Based on something I read in another thread that FX5200 card will need the nvidia 173 driver and that is not present in the 16.04 repositories. The oldest nvidia driver available in 16.04 is nvidia 304 and that does not support the FX5200. I checked.

Regards.

---

### Post by ajgreeny on 2016-06-20
*Thread moved to **General Help**.*

---

### Post by Linuxisfast on 2016-06-20
No issues here either on 4th gen i7 with 32GB RAM, ThinkPad x220 with i5 or a old quad core AMD machine. 16.04 runs fast and boots fast.

---

### Post by SciGuy1872 on 2016-06-20
I meant for this thread to be discussion--I was just wondering if Xenial is slow for others (I had advice from someone that I might wait for a month before I do an install of 16.04).  Thanks for the tip that graphics and RAM are slowing me down.

---

### Post by fjgaude on 2016-06-20
I have a full-blown install on a Sky Lake system. It is faster than anything I've tried including Devil's Canyon!

---

### Post by vasa1 on 2016-06-21
> **SciGuy1872 said:**
> ... I had advice from someone that I might wait for a month before I do an install of 16.04 ...
+1
Wait for the first point release some time in July/August 2016. You'll have a system with most of the initial wrinkles sorted out.

---

### Post by makitso on 2016-06-21
Perhaps this is the issue?
[https://plus.google.com/u/0/+Itsfoss/posts/gph8pRRNrXm](https://plus.google.com/u/0/+Itsfoss/posts/gph8pRRNrXm)

---

### Post by oldfred on 2016-06-21
My old laptop with only 1.5GB of RAM and Intel video could not run Unity. It just was too slow.
So I installed fallback/gnome-panel and it worked reasonably well. Most would suggest Lubuntu or Xubuntu for that old of a system.

And you will have to search for video driver. 

May be best just to stay with 14.04 until it  expires in 2019.

---

### Post by kansasnoob on 2016-06-21
> **makitso said:**
> Perhaps this is the issue?
[https://plus.google.com/u/0/+Itsfoss/posts/gph8pRRNrXm](https://plus.google.com/u/0/+Itsfoss/posts/gph8pRRNrXm)

Interesting :)

Xenial (all flavors) has just been incredibly unstable for me on three different sets of hardware:

AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

Intel Motherboard: DB43LD
Intel Pentium Dual-Core CPU E5300 @ 2.60GHz
Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
3GB DDR2 RAM

Slowness, crashes, intermittent shutdown problems, etc.

Come to think of it I've not tried Kubuntu and it may be less reliant on gvfs, although some apps will be. Or maybe it's time to fiddle with something 100% qt based :-?

So far though I'm mostly just using Trusty because it is truly trusty, but I keep trying Xenial on at least one machine daily. I've even played with some proposed updates but it hasn't improved anything to speak of.

---

### Post by ventrical on 2016-06-21
> **grahammechanical said:**
> Is this a discussion thread or a support thread?

If discussion, then 16.04 is running fine on my Intel core 2 duo 2.40 GHz + 1 GB RAM + Nvidia GT200 with 1 GB video memory.

If support, then open the details page. If graphics is listed as "llvmpipe" then you are using a fall back open source video driver that approximates Unity 3D on video adapters that cannot do the hardware accelerated 3D video rendering that Unity 3D requires.

With Ubuntu 12.04 if the graphic adapter could not run Unity 3D then Unity 2D was installed and it used Metacity and not Compiz as the window manager. But Unity 2D is no longer available. We get llvmpipe instead and it is slow even on video adapters that can run Unity 3D.

Based on something I read in another thread that FX5200 card will need the nvidia 173 driver and that is not present in the 16.04 repositories. The oldest nvidia driver available in 16.04 is nvidia 304 and that does not support the FX5200. I checked.

Regards.

+1 . Yes Graham you hit the nail on the head again.  I am having nothing but success on both low-end and high-end  form factors.

 During the inception of llvmpipe I would sometimes forget that ticking off updates or drivers during the install sequence would most always  set me up with the wretched patch! :) Fortunately enough for me I have  a surplus of fairly decent legacy dual cores, ddr2ram and a variety of nVida graphics adapters. A large amount on my testing time is spent on unity8 and so far I have had very positive results with both xenial and yakkety.

  There is a bottom line with nVidia graphics as well as Intel. Some of the Intel you can get lucky but an update down the road can set you up to the black screen of death. With nVidia it is more cut and dry. It will just not work, period! llvmpipe is not the way to go.  it is not a bad investment to upgrade one's nVida card. Working cards are so cheap now.

short answer .. no slow downs here.

Regards..

---

### Post by mikodo on 2016-06-21
> **vasa1 said:**
> +1
Wait for the first point release some time in July/August 2016. You'll have a system with most of the initial wrinkles sorted out.
+1
 I usually wait untill then. I wanted to try 16.04 (Xubuntu) to test an app so, I installed it. I feel like a tester with the crashes and apport reports. :) Not my usual experience with first point releases.

Other than that, the system remains responsive. Memory has increased I noticed. I consider myself lucky in that this older designed system, (2007) with no dedicated graphic card that it runs so well on Xubuntu.

I get by with no proprietary drivers. I really didn't think I would use this system for another LTS release but, now I just might. 

Addendum. After re-reading ventrical's and Graham's posts above, I might still buy my new i5 system this 14.04 LTS cycle and maybe put in a PCI-E Nvidia card in this older machine for testing. I learned some things in this thread and have some ideas. :)

```
mikodo@mikodo:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb3
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0

mikodo@mikodo:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3942         707        2324         114         910        2908
Swap:             0           0           0

mikodo@mikodo:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +44.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +38.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +38.0°C  (high = +84.0°C, crit = +100.0°C)

mikodo@mikodo:~$ top

top - 12:45:16 up 36 min,  2 users,  load average: 0.01, 0.07, 0.09
Tasks: 206 total,   1 running, 204 sleeping,   0 stopped,   1 zombie
%Cpu(s):  1.7 us,  0.3 sy,  0.1 ni, 97.2 id,  0.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  4036992 total,  2370016 free,   727824 used,   939152 buff/cache
KiB Swap:        0 total,        0 free,        0 used.  2967660 avail Mem 


```

---

### Post by RichardET on 2016-06-23
> **grahammechanical said:**
> Is this a discussion thread or a support thread?

If discussion, then 16.04 is running fine on my Intel core 2 duo 2.40 GHz + 1 GB RAM + Nvidia GT200 with 1 GB video memory.

If support, then open the details page. If graphics is listed as "llvmpipe" then you are using a fall back open source video driver that approximates Unity 3D on video adapters that cannot do the hardware accelerated 3D video rendering that Unity 3D requires.

With Ubuntu 12.04 if the graphic adapter could not run Unity 3D then Unity 2D was installed and it used Metacity and not Compiz as the window manager. But Unity 2D is no longer available. We get llvmpipe instead and it is slow even on video adapters that can run Unity 3D.

Based on something I read in another thread that FX5200 card will need the nvidia 173 driver and that is not present in the 16.04 repositories. The oldest nvidia driver available in 16.04 is nvidia 304 and that does not support the FX5200. I checked.

Regards.

So you only have 1 GB of ram in your laptop?

---

### Post by pfeiffep on 2016-06-23
My 2 installs of Ubuntu MATE 16.04 are rock solid and more responsive than 14.04 Ubuntu with gnome flashback!

---

### Post by speedwell68 on 2016-06-24
I have to say that when I first installed Xubuntu 16.04 it did seem sluggish.  I re-installed it (I broke it doing something stupid) and it now seems to fly.

---

### Post by help_me2 on 2016-06-24
Fast for me.

---

### Post by ventrical on 2016-06-26
> **kansasnoob said:**
> Interesting :)

Xenial (all flavors) has just been incredibly unstable for me on three different sets of hardware:

AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

Intel Motherboard: DB43LD
Intel Pentium Dual-Core CPU E5300 @ 2.60GHz
Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
3GB DDR2 RAM

Slowness, crashes, intermittent shutdown problems, etc.

Come to think of it I've not tried Kubuntu and it may be less reliant on gvfs, although some apps will be. Or maybe it's time to fiddle with something 100% qt based :-?

So far though I'm mostly just using Trusty because it is truly trusty, but I keep trying Xenial on at least one machine daily. I've even played with some proposed updates but it hasn't improved anything to speak of.

Trusty is still a solid alternative. All may main work is done on that operating system. I have some of th same hardware that you have. What I have do to make xenial morw workable is  use SSD drives and more current video adapter hardware version. On a SATAII based motherboard  most hdds will slow a machine down considerably but my swappable SSDs bring my SATAIIs right up to speed. I still use standard SATA II hdds on several systems for testing but I haven't had much trouble with xenial but then most of my testing is done on bootups and just testing the live ISOs and doing fresh installs.

Regards..

---

### Post by ventrical on 2016-06-26
> **mikodo said:**
> +1
 I usually wait untill then. I wanted to try 16.04 (Xubuntu) to test an app so, I installed it. I feel like a tester with the crashes and apport reports. :) Not my usual experience with first point releases.

Other than that, the system remains responsive. Memory has increased I noticed. I consider myself lucky in that this older designed system, (2007) with no dedicated graphic card that it runs so well on Xubuntu.

I get by with no proprietary drivers. I really didn't think I would use this system for another LTS release but, now I just might. 

Addendum. After re-reading ventrical's and Graham's posts above, I might still buy my new i5 system this 14.04 LTS cycle and maybe put in a PCI-E Nvidia card in this older machine for testing. I learned some things in this thread and have some ideas. :)

```
mikodo@mikodo:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb3
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0

mikodo@mikodo:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3942         707        2324         114         910        2908
Swap:             0           0           0

mikodo@mikodo:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +44.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +38.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +38.0°C  (high = +84.0°C, crit = +100.0°C)

mikodo@mikodo:~$ top

top - 12:45:16 up 36 min,  2 users,  load average: 0.01, 0.07, 0.09
Tasks: 206 total,   1 running, 204 sleeping,   0 stopped,   1 zombie
%Cpu(s):  1.7 us,  0.3 sy,  0.1 ni, 97.2 id,  0.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  4036992 total,  2370016 free,   727824 used,   939152 buff/cache
KiB Swap:        0 total,        0 free,        0 used.  2967660 avail Mem 


```

You would be surprised how a cheap 120GB SATAIII SSD hdd can bring an older SATAII system up to Speed.!! I have extra SamsungSSDIII and KingstonSSDIII that I use to swap in and swap out on older machines when I am in a hurry. Saves tons of downtime :)

Regards..

---

### Post by mikodo on 2016-06-26
> **ventrical said:**
> You would be surprised how a cheap 120GB SATAIII SSD hdd can bring an older SATAII system up to Speed.!! I have extra SamsungSSDIII and KingstonSSDIII that I use to swap in and swap out on older machines when I am in a hurry. Saves tons of downtime :)

Regards..

I made up my mind today to put a nVidia card in this machine. I have been toying with the idea of putting in an Samsung SSD too. I've read what you have written about SSD's speeding up older machines before. It used to be that the 120 GIB Kingston was a lot slower than the 240 GIB ones or, so I had read. I could never bring myself to pay the money for the larger SSD especially since, the WD Black platter I have is doing quite well. I remember Welly Wu blogging about how he found the speed of his larger WD Black platter full of games being almost as fast as SSD drives were reported to be and that he felt the larger SSD's didn't warrant the return for the extra cost of them. He called the Black's "in the sweet spot", for him. But, I don't disbelieve your experience and since I have decided to keep this machine for testing and spend money on a dedicated video card, I'll consider a cheaper 120 GIB SSD for more speed too. I shouldn't need a lot of space for testing. 

By testing, I don't mean a lot while I am still working. But, I do want to see Unity8, Ubuntu Snappy Core and snap-updates while that is materializing now, rather than later when it has matured. Maybe I can squeeze some time in for that.

Best Wishes.

---

### Post by oldfred on 2016-06-26
Five or six years ago, my then 5 year old system was getting to the point I was thinking of building a new system. It was a Core2 duo based desktop. Microcenter had a sale on a small 60GB SSD house brand SSD for less than $100. My hard drives were all older and figured I could use new SSD in new build.

But SSD sped up old system so much, that I could not justify to myself a new system, much less to my spouse. And that was a slow SSD.

       Older SSD speed -T is cache, -t is device
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec
USB2 flash drive
/dev/sde1:
 Timing buffered disk reads:  50 MB in  3.07 seconds =  16.26 MB/sec 

My now finally new SSD:
      
 sudo lshw -C Disk -short
128GB Samsung SSD 840
 Timing buffered disk reads: 1548 MB in  3.00 seconds = 515.85 MB/sec 

But new hard drive is almost as fast as old SSD, but a lot slower than new SSD.
      
 1TB WDC WD10EZEX-00B
/dev/sdb4:
 Timing buffered disk reads: 514 MB in  3.00 seconds = 171.16 MB/sec

---

### Post by mikodo on 2016-06-26
Interesting oldfred, to see your comparisons, to kind of drive, age and size of SSD's.

From what I remember from a few years ago, when I was reading benchmarks of different SSD's, things have changed today. Then, Kingston SSD where then using a slower technology in their SSD 120 GiB but, had newer and faster technology for their 250 GiB and bigger ones than all other common SSD manufactures. Also, it seems the ideal of all manufactures is to use improved technology with newer drives. Hence, the improvements in speed and longevity.

[http://superuser.com/questions/977080/does-a-large-ssd-perform-better-than-a-smaller-one](http://superuser.com/questions/977080/does-a-large-ssd-perform-better-than-a-smaller-one)

"you have to compare the same SSDs otherwise  you compare apple and oranges. the amount of NAND chips impacts the  speed: "With a hard drive, data is basically written serially, down a  single channel. The stream may be interrupted by existing data, but  ideally it's all written in a neat, uninterrupted line. Inside an SSD,  data is written in a scattershot, parallel fashion down multiple  channels to the multiple NAND chips at once. The more NAND chips an SSD  has, the more channels it has to write/read across, and the faster the  drive will be."

Seems, the larger the SSD Drive, the more NAND chips they generally have and with that the more channels, to read/write across. A design to enhance the larger SSD to accommodate more data being used with them.

My WD Black Platter drive:

/dev/sda5:
 Timing buffered disk reads: 436 MB in  3.01 seconds = 144.65 MB/sec

Take care.

---

### Post by yoshii on 2016-06-27
No problems with slowness with 32-bit Ubuntu Studio v16.04 LTS on a circa 2015 AMD ENVY.  
I'm actually kind of surprised at how fast it boots.  Normal operation is fast too.

---

### Post by ventrical on 2016-06-29
> **mikodo said:**
> I made up my mind today to put a nVidia card in this machine. I have been toying with the idea of putting in an Samsung SSD too. I've read what you have written about SSD's speeding up older machines before. It used to be that the 120 GIB Kingston was a lot slower than the 240 GIB ones or, so I had read. I could never bring myself to pay the money for the larger SSD especially since, the WD Black platter I have is doing quite well. I remember Welly Wu blogging about how he found the speed of his larger WD Black platter full of games being almost as fast as SSD drives were reported to be and that he felt the larger SSD's didn't warrant the return for the extra cost of them. He called the Black's "in the sweet spot", for him. But, I don't disbelieve your experience and since I have decided to keep this machine for testing and spend money on a dedicated video card, I'll consider a cheaper 120 GIB SSD for more speed too. I shouldn't need a lot of space for testing. 

By testing, I don't mean a lot while I am still working. But, I do want to see Unity8, Ubuntu Snappy Core and snap-updates while that is materializing now, rather than later when it has matured. Maybe I can squeeze some time in for that.

Best Wishes.

You are always welcome to join the U+1 testing team.

[https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions](https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions)

Regards..

---

### Post by Liam_Murphy on 2016-06-29
All good for me with Ubuntu Unity. I admittedly am using an SSD, so that helps out a ton.

---

### Post by ventrical on 2016-06-29
> **Liam_Murphy said:**
> All good for me with Ubuntu Unity. I admittedly am using an SSD, so that helps out a ton.

To get the optimal  performance it is always good to have current hardware form factors. However some distros of Ubuntu , e.g. Mate work really well  on more legacy PCs circa 2006 and up but then there is always Xubuntu and Lubuntu which will run fast on standard dual cores back to machines 2004 and up.

Regards..

---

### Post by sgian on 2016-07-03
My computers with 4 GB of RAM or more all run noticeably faster on 16.04 than they did with 14.04.  However there is a memory control problem with 16.04 which I could see slowing down older computers with less RAM, which makes 16.04 a memory hog in my experience.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572801)  

So right now on the PC I am posting from, my system monitor in Ubuntu Gnome 16.04 is saying that I am using 2.1 GB out of my 7.9 GB of RAM with just Firefox and System Monitor open.  So with a computer that only has 1 or 2 GB of RAM, this usage would cause the Swap Space on the hard drive to be used which will further slow down the computer.

That is the reason why I am waiting to install 16.04 on an old single core PC with 3 GB RAM that I am using as a minecraft server, until this memory control problem is fixed.  I would recommend anyone with 2-3 GB or less of RAM to avoid Ubuntu 16.04 with Unity, Gnome, and XFCE also until this issue is fixed.  I don't know if KDE or Lubuntu is affected, I'm going to start a new thread for that because 16.04 really is a lot faster if you have the resources to handle the memory hog aspect of 16.04.

---

