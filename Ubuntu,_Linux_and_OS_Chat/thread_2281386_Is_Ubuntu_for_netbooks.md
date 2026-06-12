---
title: "Is Ubuntu for netbooks?"
date: 2015-06-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Aidan_St.Louis on 2015-06-06
Hey guys, I've been running Lubuntu for a while and wanted to switch to Ubuntu. Problem is I don't know if my netbook is right for it. So, tell me what you guys think. Thanks a lot.

---

### Post by SeijiSensei on 2015-06-06
I've run Kubuntu on an ASUS netbook, but it has an ION graphics adapter that works well with the nvidia-304 proprietary driver.  If you have an all-Intel machine you might see poorer results.

---

### Post by TheFu on 2015-06-06
Depends on the netbook, storage, CPU and especially the GPU and GPU-drivers it has.  Generally, I think it is a bad idea, but I think Unity is a bad idea anyway. So - post that stuff and folks can say what they think.  The intel drivers for old Atom CPUs with on-board GPUs sucked. Unity was painful on the N280.

Now have a Haswell Celeron 2955U with built-in GPU. It is pretty fast and the GPU drivers are excellent. I wouldn't touch Unity on this machine. Storage is an m.2 SSD - so probably the fastest storage available besides a RAM-disk. 2G of RAM.

I run a plain WM, openbox or [fvwm-crystal]("http://home.gna.org/fvwm-crystal/") on it, over a minimal Ubuntu Server install. Not exactly end-user friendly, but an old-timer like me loves it!

---

### Post by Topsiho on 2015-06-06
There are netbooks and netbooks. I have one with an SSD of 8GB and 1.5GB RAM, and it is very slow using Unity (which is great, try it on a computer with a good graphics card with 3D acceleration), using Lubuntu it is acceptable. In an other netbook, with better specs, Unity may be an eye opener. Just try it :)

Topsiho

---

### Post by Bucky Ball on 2015-06-06
No idea of your hardware so impossible to say. I just bought a HP Stream 11 and Xubuntu works a treat. Unsure how Ubuntu would go and not interested in trying so makes it easy. ;)

---

### Post by kerry_s on 2015-06-06
i have a hp mini 210-1010nr, i use ubuntu-mate 15.04

---

### Post by Aidan_St.Louis on 2015-06-06
I have an Intel Atom Inside so thanks for that heads up

---

### Post by TheFu on 2015-06-06
> **Aidan_St.Louis said:**
> I have an Intel Atom Inside so thanks for that heads up

The specific model matters.

---

### Post by dankim913 on 2015-06-06
How well would Ubuntu work with this netbook?

[http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one](http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one)
1.6 GHz Intel Atom N270
1 GB RAM
Intel GMA950 Graphics Card

---

### Post by cariboo on 2015-06-06
I have a dead Compaq Mini 110 that ran Unity, although with later releases, it started getting slower and slower, I was running Xubuntu on it when it died, which it ran quite well. Specifications:

[LIST=1]
[*]Intel Atom N270
[*]1024.0 MB Ram
[*]Intel 945 Express Chipset Graphics
[/LIST]

---

### Post by TheFu on 2015-06-06
> **dankim913 said:**
> How well would Ubuntu work with this netbook?

[http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one](http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one)
1.6 GHz Intel Atom N270
1 GB RAM
Intel GMA950 Graphics Card

I had an Asus Eee with that exact CPU and 2G of RAM. Unity sucks on it. Lxde-ubuntu (Lubuntu) will work. Don't expect any fancy graphics or to playback any video over 600p (I tested and higher resolution stuttered). All video decoding happens through the CPU. There aren't any better GPU drivers.

I wouldn't buy one of those, plus the GPU uses shared RAM for video RAM, so that 1G really is more like 768MB.  If it is free, sure. But even for $20, I'd pass.

In fact, 2 months ago, I gave mine away to someone with a terrible laptop.  I've been rockin' a $199 Chromebook the last 18 months - running Ubuntu Server + a lite window manager (no DE).

---

### Post by kerry_s on 2015-06-06
> **dankim913 said:**
> How well would Ubuntu work with this netbook?

[http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one](http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one)
1.6 GHz Intel Atom N270
1 GB RAM
Intel GMA950 Graphics Card

your going to want a minimum of 2gb ram & if possible a ssd drive.

mine started out with 1gb ram & slow spinning drive. it was usable but slow. the first thing i did was upgraded ram, disk, battery.

---

### Post by Bucky Ball on 2015-06-07
> **kerry_s said:**
> your going to want a minimum of 2gb ram ...

... to get a satisfactory experience with Unity, and then you need to contend with the processor and if that will handle it.

---

### Post by mattharris4 on 2015-06-07
> **dankim913 said:**
> How well would Ubuntu work with this netbook?

[http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one](http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM/ref=sr_1_2?ie=UTF8&qid=1433635954&sr=8-2&keywords=acer+aspire+one)
1.6 GHz Intel Atom N270
1 GB RAM
Intel GMA950 Graphics Card

All of this is working on the fact that this processor is from 2009 and the computer does not have UEFI on it.

Frankly with this slow of a processor and only 1GB of RAM I wouldn't try Ubuntu on it, it is just too heavy and CPU and RAM intensive.  Even if you could get more RAM into this thing the Passmark score is only 280 (even most four year old computers score over 1000), in my experience with computers this slow Unity just doesn't work well.  

Even Lubuntu would scroll and load jerkily if you have a CPU intensive site such as SFGate up and 3+ tabs (the way I read a newspaper site I usually have 6-8 tabs up) and as it is currently configured you could also end up into swap area quite heavily on CPU and RAM intensive sites (SFGate with six tabs up uses 1200-1300MB of RAM).  Is there any way you can get at least a half-gig of additional RAM into this thing?  The way it is set up now other than being slow due to the Atom CPU you are set up OK for about 80% of websites using Lubuntu (or Xubuntu, IME the 32 bit version isn't any more CPU or RAM intensive than Lubuntu, although this doesn't apply directly to this discussion even the 64 bit version of Xubuntu is only about 10% more CPU and RAM hoggy), with 1.5GB or more of RAM (adding a half GB, a full GB would give you some buffer room) I think you could live with it as a second computer.

If you don't plan on using the internet with this thing (other than maybe to download Libre Office and maybe a printer driver) and only plan to use it to create and print word processing documents this computer would be fine using Lubuntu (I am sure you can download Libre Office from the Software Center without issue even with this processor and RAM, most printers will work once paired using open source drivers).

---

### Post by Aidan_St.Louis on 2015-06-07
I think I want to try Xubuntu so any thing on installation

---

### Post by The Cog on 2015-06-07
I've been running Xubuntu 32-bit on a couple of netbooks with this spec for some time now: 
[http://www.pcworld.com/product/31948/wind-u100-869us-netbook.html](http://www.pcworld.com/product/31948/wind-u100-869us-netbook.html)
One came with XP and one with Ubuntu. Both got wiped and replaced with Xubuntu immediately.
Not lightning fast, but usable. Upgrading to 2G RAM helped a little.

---

### Post by sudodus on 2015-06-07
Xubuntu is installed in the same way as the installation of Lubuntu from the desktop iso file. This link contains a lot of tips and links to other help pages about installing from USB drives.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Please ask more specific questions if you need help after browsing this link.

---

### Post by stalkingwolf on 2015-06-07
i have has several asus eees and now have 2 hp mini110s.   I ran UE on oneof the asus's have run zorin and currently run Mint 13 mate.  UE was slow but worked never used anything but gnome and mate and all worked fine.  even running skype and watching youtube videos at the same time

---

### Post by mattharris4 on 2015-06-08
^  From others reports MATE is a lot lighter on the CPU and RAM usage than Unity, that is for sure.  From personal experience GNOME 2 (which MATE forked off from and is still an option to use on Edubuntu) is also much lighter -- especially the Metacity version (there is also a version based off of Compiz which is for those that use "special" GUI features).  I haven't tried the current GNOME 3, the screenshots look nice but whether that looks good from a CPU and RAM use standpoint I don't know.  IME Lubuntu and Xubuntu are a bit lighter than GNOME 2 and probably MATE.

Stalkingwolf, have you tried Puppy Linux on any of those old netbooks?  From what is on the Puppy website version 4.3 sounds just about custom-made for them.  I would be interested to hear how well it works on them.  

I haven't used Zorin at all but from what is on its website it appears to have a GNOME 2 option as well as Unity and some GUIs made to look like Win 7, XP, 2000 and Mac OS X (some GUI versions require a "premium" version).  It is based on Ubuntu as well according to the website.  It likely would be an option for netbook users if the GNOME 2 GUI is selected.  I cannot comment knowingly about the other GUI options directly but Win XP was not that CPU and RAM intensive from what I remember so Zorin's GUI copy might be OK as well, as an alternative to buying and installing Win 7 or 8.1 on an underpowered netbook it might be worth a look as well.

---

### Post by kerry_s on 2015-06-09
+1 ubuntu-mate or xubuntu

i was running xubuntu but switched to mate. i'm using 15.04

but i suggest you try as many versions as you can, everyone 1 finds that 1 that just fits. as long as it does what **you** want is all that matters.

i have had everything on my netbook when i first got it, i was distro hopping every few days, eventually you will find what apps you prefer & how fast or slow you will tolerate to have what you want.

---

### Post by stalkingwolf on 2015-06-09
@mattharris4    yes ive used several releases of puppy and dsl.  there was also a release specifically for the EEE when i got my first one.  for myself they were good  but didnt meet other needs in my home.
 as time has progressed the release i use has as well.

---

### Post by Dragonbite on 2015-06-09
I've been pleased with Ubuntu Mate on my Gateway netbook (AMD Athlon 64 @ 1.2GHz & 2 GB RAM).  Lubuntu seemed too basic for me, Xfce worked alright and while KDE and Unity technically "worked", they were laggy enough that it wasn't too comfortable (KDE was better than Unity, though).  Gnome-shell, well it just never worked with whatever distribution I tried it with.

Mate gives me a nice mixture of comfortable performance, customizing-ability and looks pretty good.  This is also hte 64bit version of Ubuntu Mate (not the 32bit). The debate between using a 32bit or a 64 bit system continues.

I've also toyed with Windows 10 Technical Preview on  this machine, but don't recommend it ... and it isn't because it is from Microsoft either.

---

### Post by Bucky Ball on 2015-06-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by him610 on 2015-06-09
Yes, you can run just about any flavor of ?buntu on a netbook. I have an original Acer AOA 110-1722, originally came with 512MB Ram, since increased to 1.5GB. On my AOA, I have successfully installed and run Knoppix 7.06, Lubuntu 12.04, Ubuntu 14.04, and currently Chromixium 1.0 (which has Ubuntu 14.04 under the hood.) Since the hardware specs for a netbook is limited, the performance will vary depending on the applications in use.

A computer is a tool; learn how to use it.

Happy computing!

---

### Post by oldrocker99 on 2015-06-09
+10^6 for Ubuntu MATE. I started with 8.04, which had the GNOME 2.3 desktop, with which I fell in love. I was dismayed with the introduction of Unity, and defected to Linux Mint Lisa, which had the better-than-GNOME fork, MATE (pronounced mah-TAY, by the way. It's named after the caffeinated Argentinian herb.) and I was in love again. I found (and still find) Mint to be somewhat annoying to use, so I continued to use some *ubuntu release and installing from a PPA.

MATE, by the way, is lightweight indeed. Htop shows <500 MB used on bootup, which I consider *light*, considering that's less RAM than LXDE uses. And it is very customizable, to suit the user's preferences. I'm running it on a 32-bit(!) 2007 Lenovo 3000 N100, with pre-Sandy Bridge graphics, and can even run some Steam games well. Some. It is a crapshoot if I install a game and try to run it on this crappy little lappy. **BUT:** I can run LibreOffice, GIMP, pan, and other utilities and applications very well indeed.

I was very, very gratified to see Ubuntu MATE released, and am happily running 14.04 with no Unity at all, the way **I** like it. And isn't having the customizable desktop that you prefer part of the Linux experience?

---

### Post by Bucky Ball on 2015-06-09
Better still, Mate has recently become one of the officially supported Ubuntu flavours here. Threads about it were generally moved to the ***Ubuntu/Debian based*** section of the forum previous to this. ;)

---

### Post by kerry_s on 2015-06-09
> I was very, very gratified to see Ubuntu MATE released, and am happily running 14.04 with no Unity at all, the way I like it. And isn't having the customizable desktop that you prefer part of the Linux experience?

you should try 15.04 they are doing great things, 15.10 was nice to, but it broke on me, so i dropped back down to 15.04.
i just started mixing mine with some xfce parts, for example i find mate-panel to limiting so i replaced it with xfce4-panel, it has intelli hide. whisker menu is also easily changed to work in mate.

---

### Post by TheFu on 2015-06-09
For me, releases with less than 3 yrs of support just aren't worth my time.  Reinstalling a new OS every 6 months wastes too much time - even when I can bring over all the programs and settings and data in about 30 min.  Enough things have been changing every release to make the migration just not worth the effort.

For me.

One of my systems requires that I manually download, patch and build the kernel driver for the touchpad with every new kernel.  I'd rather do this until 16.04 is released than deal with all the unknowns from short-term support releases. Being predictable is more important than being "new" to many people.

In the mid-1990s, I did my bleeding edge work for Linux. Don't want that anymore.

---

### Post by Copper Bezel on 2015-06-10
I ran regular Unity Ubuntu (and Gnome 2 Ubuntu before that) as well as Shell on a netbook from like ... 10.10 to 12.10 or something? There's not really an immense amount of variation in netbook stats - they only existed because the extended life on XP for low hardware and then the transition from that to a cheap Windows 7 Starter license made them possible, so the 1.6 Ghz Atom processor, 1024x600 display, and 1 gig of installed RAM with a 2-gig strip as an add-on item at checkout were all basically mandatory. Geez, though, I really wouldn't want to use one as a general-purpose machine now. = /

---

