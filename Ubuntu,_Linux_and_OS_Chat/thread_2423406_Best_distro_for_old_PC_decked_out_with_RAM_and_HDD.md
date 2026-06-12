---
title: "Best distro for old PC decked out with RAM and HDD space - old games, multimedia, web"
date: 2019-07-23
forum: Ubuntu, Linux and OS Chat
---

### Post by greatinca on 2019-07-23
My leanings: Mint, Lubuntu.

System specs

[LIST]
[*]HP DM1 3010NR. 64-bit Netbook. Manufactured early 2011. 
[*]AMD E-350 APU (CPU with embedded GPU) 1.6GHZ. Dual-core 64-bit. 
[*]Gigabit ethernet, Wireless-N Wi-Fi (not AC, no 5ghz), BlueTooth, Verizon 4G 
[*]2TB 5400 RPM hard disk drive (upgrade) 7mm heigh (1tb per platter) 
[*]32GB DDR3-1600 RAM (2x16GB so-dimm sticks; upgrade). 
[/LIST]


Intended uses:

[LIST]
[*]Firefox & Chrome 
[*]Watch movies. X264 1080p. Close equivalent to Media Player Classic. 
[*]Games - Open source, emulators, closed-source freeware, and commercial. Nothing newer than 2010 unless it is one of those low-spec games 
[*]Pictures, books, music 
[*]LibreOffice 
[*]BOINC (background science crunching), with VirtualBox if able (for LHC project apps). 
[/LIST]


Secondary Circumstances:

[LIST]
[*]Need Ethernet, wi-fi, and graphics drivers to work 
[*]Four systems bought for $50 each from boot-to-BIOS / intact screen parts/repair as-is auctions on eBay. 2TB HDD and 16GB RAM Modules purchased from NewEgg. 
[*]The RAM's very high speed isn't utilized, but the BIOS is using a very low CAS latency to get partial exploitation. 
[*]CPU is underclocked to control heat (Cheap A/C 85) and bring power consumption on par with a more modern but more expensive Gigabyte Brix or Intel Nuc 
[*]CPU is the main system bottleneck, then HDD. 
[*]Oodles and kaboodles of RAM, more than all the software the slow CPU can run can ever use. 
[*]Huge 5400rpm HDD to be filled up to the brim with games, movies, music, books, and pictures 
[*]Reason for Linux: Out of windows 7 license keys and Windows 10 driver support for these PCs is poor. 
[/LIST]


User:

[LIST]
[*]Set-up user is experienced windows user with light Linux experience (I can format XFS drives and set up swap partitions via GUI). Can do home-DIY IT & network. 
[*]End users are intermediate windows users with no linux experience with semi-regular contact to me. 
[*]Don't mind lightweight desktop. Like LXDE over XFCE. Don't know LXQT but seem positive. Good with Cinnamon. Don't dig GNOME 
[*]Windows Aero type features not required 
[*]Prefer paint.net over GIMP 
[*]Prefer Media Player Classic Home Cinema over VLC. 
[*]No one minds using closed-source freeware or commercial software 
[*]Need large repositories and good software compatibility especially games and emulators. 
[*]Willing to use WINE but native software is preferred. End users won't be into tinkering WINE to make stuff work. 
[/LIST]

---

### Post by wildmanne39 on 2019-07-23
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by mastablasta on 2019-07-23
> **greatinca said:**
> My leanings: Mint, Lubuntu.

System specs

[LIST]
[*]HP DM1 3010NR. 64-bit Netbook. Manufactured early 2011.
[*]AMD E-350 APU (CPU with embedded GPU) 1.6GHZ. Dual-core 64-bit.
[*]Gigabit ethernet, Wireless-N Wi-Fi (not AC, no 5ghz), BlueTooth, Verizon 4G
[*]2TB 5400 RPM hard disk drive (upgrade) 7mm heigh (1tb per platter)
[*]32GB DDR3-1600 RAM (2x16GB so-dimm sticks; upgrade).
[/LIST]

it will use AMD radeon opensoruce driver. they should work well. don't expect to do too much gaming with that GPU. i have E-450 with Kubuntu and Left for dead works on lowest settings on windows 7. so that is your limit. source games should work on lowest. windows games.... hmm... maybe the range would be FPS from 2008 and older?! additionally only radeon driver are available for this chip and i am not sure they offer the full support for it.  i know back in the 2016 they could overheat the GPU (i.e. power management was not good). maybe they improved by now. more info on support can be found on x.org page.

[QUOTE]

[LIST]
[*]Need large repositories and good software compatibility especially games and emulators.
[*]Willing to use WINE but native software is preferred. End users won't be into tinkering WINE to make stuff work.
[/LIST]


Linux games are on Steam, some are on GOG. there is not many good opensource games these days.

you will need to use Wine or Play on Linux, or Lutris or Proton to run windows games. sometimes there is an overhead. so while they kind of work on windows they might not work on linux. otherwise the Platinum rated games are usually just "install and play".

Kubuntu has similar interface to windows. it also has all settings in GUI and KDE (Qt based) programs (k3b, VLC, kdenlive, digikam...) are feature rich. good news for advanced windows users. there is also simple desktop software like Krita. for small picture editing i use nomacs. it's fast and has many options, but not as much as GIMP.
Paint and GIMP do not belong to the same group. GIMP is image manipulation program, Paint is not really meant for that and is more suited towards drawing. maybe better to compare Paint and Inkscape or Krita.

media players- install whichever you want. there are plenty of those arround including some that use CLI.

5400 RPm will be slow. i hope this is not a "Green" hard disk. they tend to power down. for OS install it is best to use "blue" or "black" HDD with 7200 rpm+ or better yet, to add a SSD. data will be fine on 5400 rpm, but access is slower and it might not matter as much. 

If you want to go super light then Lubuntu is the way, but since you have plenty of RAM i am not sure why you wouldn't want to have a descent DE. taking Lubutnu instead of Kubutnu might save you a few hundred MB of ram. that's it. you declared 32 GB (minus 512 MB for the GPU). Kubuntu for example will turn off special desktop effects when going full screen (e.g. games). you wont' be using full ram, unless you open A LOT of tabs on browser.

BTW DM 1 and this chip only supports **up to 8 GB ram**: [https://support.hp.com/in-en/document/c02861756](https://support.hp.com/in-en/document/c02861756)

---

### Post by greatinca on 2019-07-23
I have 32GB installed in all 4 machines, and 16 GB on 6 others that have windows 7 on them and it is all recognized.  I have never had problems going over documented maximum supported RAM amounts or speeds on consumer class machines (only business class)

HDD is WD blue.  There are no greens for laptop drives, and WD merged green into blue for desktop drives. Windows 10 is assertive on shutting all these drives down, especially if not the system drive.

I was hoping for an in-RAM distro like puppy to help all the RAM overcome slowness of HDD.  Puppy itself is too light though, and proprietary stuff. I've seen Lighthouse64 mariner and FatDog but they don't use ubuntu or debian repositories as far as I know of, and LightHouse64 I'm not sure on its future maintenance.  Windows 10 will assertively consume excess RAM for disk cache (Windows 7 caps out at 8GB about for disk cache) which is smarter than RAM disk though. Not sure if Linux distros are as agressive as Windows 10 on gobbling excess RAM for disk cache.  RAM disk cache of course needs long time stability. But with how stable windows has become can go whole month without rebooting (just updates), months if ignoring the updates.

---

### Post by TheFu on 2019-07-23
I used an AMD E-350 APU for my media center PC until it couldn't handle the new Hidef videos.  Never got it to play anything over 600p resolution without stuttering, but anything 600p and less worked great.  The APU/GPU doesn't have any hardware video decoding for video. No mpeg2. No h.264, no dream about h.265/AVC1/HEVC.  This is a common issue on low end CPUs that need the CPU to decode all video, higher resolution kills the CPU.

If you remove the video playback stuff, Lubuntu should be fine.  For videos, basically PAL DVDs, 576p, are the limit on the resolution due to the CPU. Forget about netflix, amazon video, hulu, hidef video.

An E-450 APU is much, much, faster than the E-350 APU.

How do I say this nicely - a Raspberry Pi v3b+ is a more capable computer for your needs.  In a few months, when the power and overheating issues are solved, a Pi v4 will be.  If you need something today, now, then an Odroid or Rock64 or RockPro64 would be much faster, have cooling solved and handle 4k video, at the $60-90 price point.  I'm waiting for a fan kit to be cheaply included with the r-Pi v4. Heatsinks aren't enough according to the reading I've done, the CPUs are thermally limited otherwise.

---

### Post by greatinca on 2019-07-23
Any way to get more RAM on a Pi4b?  4GB isn't very much at all. I want 16GB. Also want something more dependable than MicroSD for storage. Also don't think many Linux games on GOG/Steam will do Arm64. Raspberry Pi4b does show promise for replacing Minix and Skystream even with just 4GB for pirate-friendly Android TV box (torrentted movies on local attached storage, Kodi).

HP DM1 are overwhelmingly E-350.   HP DM1 play high-profile 1080p X264 no problem via Media Player Classic.  Must use DXDA / hardware decoding (DXDA is strictly windows I think).  These machines don't do software decoding at all.

Foster kids with placement stability will graduate to a more expensive i7 Brix or Nuc or higher-spec ultraportable if/when they can keep DM1 without losing it, destroying it, getting it stolen, or getting it permanently or long-term confiscated (teachers).

---

### Post by mastablasta on 2019-07-24
> **greatinca said:**
> I have 32GB installed in all 4 machines, and 16 GB on 6 others that have windows 7 on them and it is all recognized.  I have never had problems going over documented maximum supported RAM amounts or speeds on consumer class machines (only business class)
.
recognised and used? i though there is actually hardware limit. maybe i should upgrade my DM1 to 6 GB as planned... though the other side of disk drive has windows 7 home (it came pre-installed) and that one supports 2 GB max. i use the windows side for a few games and in the future i might still need it for certain websites that require windows apps.

issue is still radeon driver i guess. you can go very light using Debian stable and LXQT or Lubuntu. not sure where they are with radeon driver at the moment. i doubt they will do plenty of work for these old chips. plus they are all into AMDGPU driver for newer chips.

radeon features: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)
the chip is under: [TABLE="class: mointable"]
[TR="bgcolor: #F2F2F2"]
[TD]Evergreen[/TD]
[TD]CEDAR, REDWOOD, JUNIPER, CYPRESS, PALM (Wrestler/Ontario), SUMO (Llano), SUMO2 (Llano)[/TD]
[TD]HD5430 - HD5970, all HD6000 not listed under *Northern Islands*, HD7350
[/TD]
[/TR]
[/TABLE]
radeon info: [http://manpages.ubuntu.com/manpages/bionic/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/bionic/man4/radeon.4.html)

on windows you can actually play a thing or two.: [https://www.notebookcheck.net/AMD-Radeon-HD-6310.40952.0.html](https://www.notebookcheck.net/AMD-Radeon-HD-6310.40952.0.html)

in linux AMD dropped support for this chip, so whatever the community did in opensource driver is there. 

chip info:
**IGP (HD 6000)[COLOR=#54595D][[/COLOR][edit]("https://en.wikipedia.org/w/index.php?title=List_of_AMD_graphics_processing_units&action=edit&section=51")[COLOR=#54595D]][/COLOR]**


[LIST]
[*]All models feature the UNB/MC [Bus]("https://en.wikipedia.org/wiki/Computer_bus") [interface]("https://en.wikipedia.org/wiki/I/O_interface")
[*]All models do **not** feature double-precision FP
[*]All models feature Angle independent anisotropic filtering, UVD3, and [Eyefinity]("https://en.wikipedia.org/wiki/AMD_Eyefinity") capabilities, with up to three outputs.
[/LIST]

GPU chip will be bottle neck.

you can also get a very light deskotop by installing from netinstall image and just adding lightdm and XFCE or even just a windows manager (e.g. IceWM). it might look a bit like windows XP but it will fly.


RAM is there to be used. Linux will use it if it is available. It will utilize it as much as possible. so having more of it is a plus.

edit: linux doesn't need a reboot. it reboots only for patching the kernel, but this can be done without reboot thanks to livepatch : [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)

---

