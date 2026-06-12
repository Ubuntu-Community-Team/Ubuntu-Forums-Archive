---
title: "New (Old?) Project"
date: 2016-08-09
forum: The Cafe
---

### Post by Kale_Freemon on 2016-08-09
Hello all!

Just to start this off, I've had a Dell Dimension 4500 around for the past 3 or so years (maybe longer?). I hardly ever did anything with it as it is an old computer that my grandfather got around '02 - '03. 

I had pulled out the CD-ROM drive, and put in a DVD-ROM drive I've had kicking around since 9th grade. From there, I would install my OS of choice at the time, and then I'd pull out the drive, and replace it with a hard drive. I had four HDDs in there, all of which I had laying around from old computers I use to own, including the stock 80GB one. I even upgraded the RAM to 1GB with some RAM modules I had.

For awhile, I had it set up to play with Arch (which was really fun). After I got bored of that, I decided to install a copy of Windows Server 2008 that I got through the college I was going to, and turned it into a file server / web server. Yes, it was a legal copy of Windows Server that Microsoft gave away to IT students.

Again, after I got bored of that, I decided to install Lubuntu 14.04 onto it and just turn it into a home file / print server. It worked well like that for a few months, up until I my ex and I divorced. After that, the computer just sat in a closet hardly ever being used. I pulled it out once just to see if I could turn it into a temporary wifi range extender in conjunction with a second router, and it was kinda cool.

Now that my life has improved (moved to a new apartment, and got my life back together), I decided to pick up a monitor from a local Goodwill for $24.99, new speakers from Wal-Mart for $11.88, and install Lubuntu 16.04 LTS. The goal was to revive the machine, and try to make it at least somewhat usable in 2016.

At first, it was a pain as the stock ATI Rage 128 Ultra card that was in it couldn't support the resolution that my monitor wanted to work with. So, I had to find a work around just to get my monitor to display an image. After that, I noticed that the card couldn't handle video almost at all, and the entire machine ran sluggishly. So, I went onto eBay and started hunting down a replacement card for cheap.

I managed to find a used PNY AGP card, which uses the Nvidia GeForce 5200 FX GPU for $18.99 and free shipping. Since the chip is legacy, and Nvidia no longer supports it, I'm forced to use the open source drivers. But, after installing it, I noticed a huge improvement in performance, video playback, and was able to use the optimal resolution for my monitor.

While on eBay, I also decided to hunt down a replacement processor. After some research, I was able to find a compatible Pentium 4 3.06 GHz processor to replace the stock 2 GHz P4 that is in it (so old that it doesn't even have hyper threading). This set me back about $13.00, and I'm still waiting on it to arrive from China (hoping it's not a fake, lol).

Overall, here's the TL;DR overview of the current hardware I have in the case:

Stock motherboard, fan, Creative SB sound card, PSU, and 2 GHz Pentium 4 processor
PNY Nvidia GeForce 5200 FX 256MB AGP GPU
1GB DDR RAM
DVD-ROM Drive (identified by the system as an HL-DT-STDVD-ROM GDR8162B)
80GB HDD for the OS (hosting both Lubuntu 16.04 LTS and Windows 7 Ultimate)
40GB HDD for /home
40GB HDD for Windows 7 installed applications

My next intended replacements are the PSU, and possibly an SSD for the boot drive (if I can find one that will work at a decent price).

The end goal of my project is to make the machine work relatively well in 2016 without breaking the bank, thus avoiding the need to junk it. It's a budget revival/rebuild.

Currently, I'm spending more time using this old Dell than I do my 2015 System76 Lemur. So far, so good.

I'll update this post as I go along.

Please excuse the mess you see in the pictures. My desk is always the designation for clutter.

[[IMG]https://s10.postimg.org/ga3yepgud/20160809_200001.jpg[/IMG]]("https://postimg.org/image/ga3yepgud/")


[[IMG]https://s10.postimg.org/y1k66wlmt/20160809_200013.jpg[/IMG]]("https://postimg.org/image/y1k66wlmt/")


[[IMG]https://s10.postimg.org/9z3cc14zp/20160809_200024.jpg[/IMG]]("https://postimg.org/image/9z3cc14zp/")


[[IMG]https://s10.postimg.org/ggm8vjfd1/20160809_200148.jpg[/IMG]]("https://postimg.org/image/ggm8vjfd1/")

---

### Post by Bucky Ball on 2016-08-10
An SSD and a decent, efficient PSU and this machine might last another ten years ...

---

### Post by mastablasta on 2016-08-10
ATI 9600, 9800 and then later radeon HD 36xx (maybe even some 4xxx) AGP series work very well on linux. in fact they probably work better than the nvidia you installed. 
Rage 128 has only software rendering support available in opensource drivers, so that was the main issue. 
i would rather use a 1TB HDD then getting SSD. these older driver are probably IDE and with newer sata the reis noticable improvement in speed. there is not much need for SSD for this normal work. unless you need it to boot fast.

---

### Post by Kale_Freemon on 2016-08-10
> **mastablasta said:**
> ATI 9600, 9800 and then later radeon HD 36xx (maybe even some 4xxx) AGP series work very well on linux. in fact they probably work better than the nvidia you installed. 

The prices for them do seem to be pretty good on eBay. I might try one out in the future when I have a little bit more money. Right now, I'm just glad that it's in a usable state.

> **mastablasta said:**
> 
Rage 128 has only software rendering support available in opensource drivers, so that was the main issue. 

Even then, it only had about 16MB of graphics memory. So, I doubt it would have been very useful at all. It even sucked on Windows XP when my grandfather was using it.

> **mastablasta said:**
> 
i would rather use a 1TB HDD then getting SSD. these older driver are probably IDE and with newer sata the reis noticable improvement in speed. there is not much need for SSD for this normal work. unless you need it to boot fast.

The question is, how would SATA benefit me at all when this machine only has IDE capabilities? Even then, the SSD is not a requirement, just an idea. Something a little more fun to do with it if I have the extra money.

[quote=Bucky Ball]An SSD and a decent, efficient PSU and this machine might last another ten years ...[/quote]

Maybe. Though, I'm not holding my breath. I'm just seeing how far I can push this machine before I can't push it any further. The more time I can give it, the better.

---

### Post by qyot27 on 2016-08-10
> **Kale_Freemon said:**
> The question is, how would SATA benefit me at all when this machine only has IDE capabilities?
It won't, really, except that you'll have a dickens of a time finding new drives with IDE interfaces, whether they're SSD or large-capacity HDD.  Unless the motherboard itself has SATA connections (and on a computer that old, it would definitely only be first generation SATA), the only way to enable it is to buy a SATA host* card that hooks in via the Conventional PCI ports, so you'll be intrinsically bottlenecked by the PCI interface, which is roughly equivalent to the transfer speed of a 7200 rpm HDD.  That means that you may get a bit of a boost, since the speed of an ATA-6 hard drive at 7200rpm is slightly lower than PCI, so the drive will be able to get closer to its limits, but that's still your wall.  An SSD likely wouldn't yield any improvement beyond a regular HDD in that situation, apart from being near-silent and running cooler so you could save energy.  Especially since SATA host cards for PCI are for the first generation (1.5Gbit/s) and you won't see dramatic improvements with SSD vs. HDD.

*being a host card is important, or else the machine won't boot from any drive hooked through it.


[https://en.wikipedia.org/wiki/List_of_device_bit_rates](https://en.wikipedia.org/wiki/List_of_device_bit_rates)

Standard 32-bit PCI operating at 33MHz has a bandwidth of 133MB/s; operating at 32-bit @ 66 MHz or 64-bit @ 66 MHz will raise that to 266MB/s or 533MB/s, respectively, but I don't know how common those configurations are, so it's probably best to assume that's not the case here.

[A 7200rpm HDD has a transfer rate of approximately 128.75 MB/s as of 2010.](https://en.wikipedia.org/wiki/Hard_disk_drive#Data_transfer_rate)  Like I said, it's nearly equal to that of standard PCI.

First generation SATA (1.5 Gbit/s) has a bandwidth of 187.5 MB/s.  If the card is hooked in through PCI, the rate will never be higher than what PCI can do, so it'll top out at 133MB/s and will never saturate the full 187.5MB/s it theoretically *could* do.  So even if you put a 10,000rpm or 15,000rpm HDD or an SSD in there, the speed still wouldn't go above 133MB/s.

All of that is also referring to *peaks*, not sustained throughput.  So an SSD might perform objectively better and sustain those speeds easier and for longer than a 7200rpm drive might, but 133MB/s is as far as it can ever go in that configuration.  Under those situations, you won't be able to see a lot of the tremendous SSD speed benefits that SATA 3.0 Gbit/s or 6.0 Gbit/s would have gotten you.


If the IDE ribbon cable is itself limited the same way the HDD interfaces are, then you could also have the problem that even if the drive was ATA-6, the cable might only be rated for UDMA ATA-4 or ATA-5 speeds, in which case going through PCI with SATA could get you a much nicer boost, but in reality you may not notice too much.

---

### Post by qyot27 on 2016-08-10
Also, from that lshw screenshot, that card's not AGP, it's PCI (or hooked into one of the unofficial types of AGP/PCI hybrid ports, which means they're still limited by PCI constraints).  And since PCI shares bandwidth, installing a SATA host card and hooking drives through it will lower the effective bandwidth for the drive below even that 133MB/s (or 266MB/s that it looks like that port might be capable of).

---

### Post by Kale_Freemon on 2016-08-10
> **qyot27 said:**
> Also, from that lshw screenshot, that card's not AGP, it's PCI...

Nope. Definitely an AGP card. I did a lot of research and looking around before I purchased this card to ensure that it'd work in my machine first.

Very possible, though, that the card is running as a PCI device due to a driver issue. Either way, the card and the port are both AGP, and the card works just fine for me at the moment.

As far the the SATA/SSD thing goes:

[quote=:qyot27][COLOR=#000000]It won't, really[/quote]

Kind of what I was thinking. At the moment, the drives that are in the machine are plenty fast enough (thank god for a lightweight system), and are showing no signs of failure just yet.[/COLOR]

---

### Post by Bucky Ball on 2016-08-10
If the machine has only IDE, I know of no SSD that is IDE. Maybe I'm missing something. Think you can get IDE to SATA converters but its been awhile since I needed one (years). Still, no biggie as you're not there yet ...

Don't know the technicalities, but would IDE make an SSD worthwhile even if you could attach with adapter? Does it have the speed capabilities?

---

### Post by Kale_Freemon on 2016-08-10
> **Bucky Ball said:**
> If the machine has only IDE, I know of no SSD that is IDE. Maybe I'm missing something. Think you can get IDE to SATA converters but its been awhile since I needed one (years). Still, no biggie as you're not there yet ...

Don't know the technicalities, but would IDE make an SSD worthwhile even if you could attach with adapter? Does it have the speed capabilities?

I doubt that it does. But, it's just an interesting idea. lol

Right now, I have to consider buying another graphics card as the latest Ubuntu kernel update kinda messed up the driver. Had to revert back to an old kernel.

---

### Post by qyot27 on 2016-08-10
> **Bucky Ball said:**
> Think you can get IDE to SATA converters but its been awhile since I needed one (years).
The adapters that exist are flimsy circuitboard affairs that you have to also make sure to insulate with electrical tape.  It's less hazard-prone to get a host card and use it through that; you'll have to take a speed hit either way.

[This is the one I popped into my old setup.](https://www.amazon.com/Vantec-6-Port-SATA-Host-Card/dp/B002PX9BX2)  Trying to boot from an eSATA drive was ridiculously unstable, but I mostly blame the drive enclosure for that since both the internal 1TB drive and the Blu-ray burner I needed the card for work fine in both WinXP and Ubuntu.  The only other complaint is that ReactOS doesn't seem to like the card at this point in time, so I can't even use the LiveCD.  That's one of the biggest of ReactOS' issues that have to get sorted out before I can replace XP on there.

---

### Post by mastablasta on 2016-08-11
eh no SATA...too old to service...

although i did manage to find a motherbaord that had both AGP and PCIe on it with DDR2 and DDR slots on it (only one can work and only up to 2GB). it has SATA and IDE.

plenty of issues with it on Linux (though it works sort of). main issue is sound. second issue is that PCIe is vesion 1 and i couldn't get the newer nVidia card working on it. AGP card Works well at i think 4x speed. nothing fancy but good enough for Office work. it runs Kubuntu 14.04. we also play some older games on it (minecraft, DOS games, Quake, Diablo2...).

---

### Post by poorguy on 2016-08-13
Not as old as your Dell 4500.
I found it laying in a pile of trash on big trash day. :)
I can't believe someone just tossed it. :o

System:  Dell-XPS-200 Kernel: 3.13.0-93-generic i686 (32 bit, gcc: 4.8.4) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Dell DXC051
           Mobo: Dell model: 0DD431 Bios: Dell version: A03 date: 10/28/2005
CPU:       Dual core Intel Pentium D CPU (-MCP-) cache: 1024 KB flags: (lm nx pae sse sse2 sse3)
           Clock Speeds: 1: 2792.967 MHz 2: 2792.967 MHz
Memory: 3.0 GB DDR2 
Graphics:  Card: NVIDIA GT216 [GeForce 210] Resolution: 1280x720@60.0hz 
           GeForce 210/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 340.96
Audio:     Card-1: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda
           Card-2: NVIDIA GT216 HDMI 
Drives:    HDD Total Size: 80.0GB model: ST380819AS

---

### Post by Kale_Freemon on 2016-08-15
> **poorguy said:**
> Not as old as your Dell 4500.
I found it laying in a pile of trash on big trash day. :)
I can't believe someone just tossed it. :o

System:  Dell-XPS-200 Kernel: 3.13.0-93-generic i686 (32 bit, gcc: 4.8.4) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Dell DXC051
           Mobo: Dell model: 0DD431 Bios: Dell version: A03 date: 10/28/2005
CPU:       Dual core Intel Pentium D CPU (-MCP-) cache: 1024 KB flags: (lm nx pae sse sse2 sse3)
           Clock Speeds: 1: 2792.967 MHz 2: 2792.967 MHz
Memory: 3.0 GB DDR2 
Graphics:  Card: NVIDIA GT216 [GeForce 210] Resolution: 1280x720@60.0hz 
           GeForce 210/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 340.96
Audio:     Card-1: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda
           Card-2: NVIDIA GT216 HDMI 
Drives:    HDD Total Size: 80.0GB model: ST380819AS

Not a bad find. It's unfortunate that people would just throw away perfectly good machines. The least they could do, if they want to get rid of them, is to donate them.


As an update on my 4500:

I went ahead and just nuked both my 16.04 and Win 7 installs in favor of installing 14.04 and Windows XP Pro. The reasoning here is that, with XP I could install some older games that don't get along as well with newer hardware (i.e. Silent Hill 2 and Splinter Cell Pandora Tomorrow).

With 14.04, the thought was to be able to leverage the proprietary drivers for my Nvidia card. The problem here was that the driver was never tested once it reached 14.04.2. As such, I was unable to install and use the driver since it is no longer compatible (and I'm not digging up 12.04 for this project). That being said, 14.04 still works best as it seems to work with the open source driver better than on 16.04 with the most recent update (which pretty much caused my card to be next to useless).

I am considering ditching this card as it has been a painful experience in Linux, but it works so well with several games on Windows XP that I'm finding it difficult to want to replace it with something that I'm not sure will behave nearly as well. As such, the 4500 is seeing most of its time in Windows XP.

I know what you are all probably thinking:

"XP is end of life, and is so insecure to run now!"

While this is, mostly, true, I have employed a couple of strategies to help get around the security flaws inherent in running such an old system.

1. I am running a 100% up to date anti-virus via Avast.

2. Replacing Windows firewall with a far more up to date firewall via Zone Alarm.

3. Use a VPN if I am wanting to, for whatever reason, hide myself (not really using it at all).

4. Using an up to date version of FireFox.

5. Not using it to log into my bank accounts or access anything uber sensitive (hence the reason I don't use the VPN).

6. A registry hack that allows me to install updates for POSReady2009, which is pretty much XP for cash registers.

7. Most importantly, using common sense when on the internet, as I would on any system regardless of age or type.

I also received the 3.06GHz Pentium 4 that I was waiting to arrive from China, and installed it a couple of days ago now. Been running quite well after updating the bios.

So far, I feel as if this computer has definitely received a new lease on life. I will get around to finding a better card to run in Linux, but the current set up works well enough for now. So far, I think I'm definitely pulling out every inch of value this old girl has to offer. :D

---

### Post by Delupara on 2016-08-15
interesting, what motherboard is it?

---

### Post by qyot27 on 2016-08-16
> **Kale_Freemon said:**
> With 14.04, the thought was to be able to leverage the proprietary drivers for my Nvidia card. The problem here was that the driver was never tested once it reached 14.04.2. As such, I was unable to install and use the driver since it is no longer compatible (and I'm not digging up 12.04 for this project). That being said, 14.04 still works best as it seems to work with the open source driver better than on 16.04 with the most recent update (which pretty much caused my card to be next to useless).

I am considering ditching this card as it has been a painful experience in Linux, but it works so well with several games on Windows XP that I'm finding it difficult to want to replace it with something that I'm not sure will behave nearly as well. As such, the 4500 is seeing most of its time in Windows XP.
Were you using Unity or the one of the other DEs?  Because even my GeForce 6200 struggle(d|s) with Unity, but performs admirably for its constraints under LXDE.  Although honestly, yes, it all-around works better in Windows.  I mostly blame X.Org not being as usable on machines as old as that one, though (the CPU is a Pentium-III era Celeron, so no SSE2 or raw CPU power and what-all).

You want crazy, though, [put this in there](https://www.amazon.com/ZOTAC-NVIDIA-GeForce-512MB-ZT-60604-10L/dp/B0083Y1YVE/ref=sr_1_7?srs=2530845011&ie=UTF8&qid=1471320436&sr=8-7&keywords=pci).  I toyed with the idea of replacing the 6200 in mine with that, and since I already have a Blu-ray drive in this thing, I'd only need the playback software.  There's something perverse about the thought of a nearly 15 year old computer setup playing Blu-ray Discs back in real time...if the system RAM didn't suddenly become a bottleneck, anyway.  But since the 6200 hasn't failed, I didn't want to waste my money.

---

### Post by poorguy on 2016-08-18
> **Kale_Freemon said:**
> Not a bad find. It's unfortunate that people would just throw away perfectly good machines. The least they could do, if they want to get rid of them, is to donate them.
I agree.

> **Kale_Freemon said:**
> I know what you are all probably thinking:

"XP is end of life, and is so insecure to run now!"

While this is, mostly, true, I have employed a couple of strategies to help get around the security flaws inherent in running such an old system.
You are using common sense, the best anti-virus software for any OS.

I still use an XP computer for Microsoft Flight Simulator X and also for Engineering Design Software.

> **Kale_Freemon said:**
> I also received the 3.06GHz Pentium 4 that I was waiting to arrive from China, and installed it a couple of days ago now. Been running quite well after updating the bios.

So far, I feel as if this computer has definitely received a new lease on life. I will get around to finding a better card to run in Linux, but the current set up works well enough for now. So far, I think I'm definitely pulling out every inch of value this old girl has to offer. :D
Most of my Linux Computers are others discarded or ones I have found in trash piles on the side of the road.
Clean them up / upgrade them as spare parts allow and all of mine work flawlessly and are blazingly fast.

No complaints. :)

---

### Post by mastablasta on 2016-08-19
> **Kale_Freemon said:**
> 
1. I am running a 100% up to date anti-virus via Avast.


I use it as well now. Avira was lighter, better but it stopped the XP support in April this year.

> 
2. Replacing Windows firewall with a far more up to date firewall via Zone Alarm.

Another good alternative is Comodo which also offers virtual desktop, sandboxing, additional defence... used to use ZoneAlarm before but IMO they ruined the interface at some point. it's been a while since i looked at it though.

> 
4. Using an up to date version of FireFox.

i've added no script to it. scripts are allowed only on certain trusted websites, but then again who can you trust these days.

i use it for banking and other state services,at least until they bring the new form signing app to linux. right now they have it for Win only. bastards. anyway i browse only a couple of websites. facebook, gmail, 2 or 3 news sites, ubuntu forums. that's mostly it.

---

