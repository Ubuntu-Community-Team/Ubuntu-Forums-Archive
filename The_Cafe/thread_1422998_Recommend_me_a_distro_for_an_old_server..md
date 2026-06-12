---
title: "Recommend me a distro for an old server."
date: 2010-03-06
forum: The Cafe
---

### Post by kaldor on 2010-03-06
I have an old computer with only a 20 GB hard drive and 96 MB RAM. It can't run much. 

I currently have Damn Small Linux installed, but it's outdated and has horrible support for the majority of things; it doesn't detect CDs, USB devices, floppies, anything. 

I want a minimal OS that should work well as an SSH server. It's for backing up files. It's just very inconvenient having to boot up another computer, load the files from the USB hard drives to that, then use SSH to connect to the DSL server. 

500 Mhz processor
96 MB RAM
20 GB 
GUI not neccesary, but a minimal one would be nice just in case.

It used to have Windows 98 on it. Sadly enough, Windows 98 actually ran much, *MUCH* better than Damn Small Linux does now. I just want a basic server! lol

Suggestions?

---

### Post by jonabyte on 2010-03-06
Slackware, install the minimum and no gui

---

### Post by K.Mandla on 2010-03-06
Arch? Ubuntu command-line? Slitaz base? If you want something lightweight and minimal to work as a server, just about anything should do. Use whatever you prefer, and just install it without a GUI.

---

### Post by wojox on 2010-03-06
Try Debian Lenny with just a cli install.

---

### Post by antenna on 2010-03-06
A minimal Debian install would be my first choice too, probably with Openbox if you need a GUI.

---

### Post by snowpine on 2010-03-07
I agree with all of the above :) and also will add CentOS to the list.... it has great support for older hardware (so long as non-free drivers are not required).

---

### Post by swoll1980 on 2010-03-07
Ubuntu

---

### Post by Majorix on 2010-03-07
FreeBSD. Even though it is not a Linux distro, it still is UNIX, and works great as a server. The default install would have you using the command line (no GUI).

---

### Post by dragos240 on 2010-03-07
> **Majorix said:**
> FreeBSD. Even though it is not a Linux distro, it still is UNIX, and works great as a server. The default install would have you using the command line (no GUI).

It'll still take a while, installing everything with ports.

[COLOR=White]Although I suppose you could use add_pkg.....[/COLOR]

---

### Post by Queue29 on 2010-03-07
> **swoll1980 said:**
> Ubuntu

His computer doesn't even meet the minimum recommended specs for Ubuntu..

> 700 MHz x86 processor
384 MB of system memory (RAM)
8 GB of disk space
Graphics card capable of 1024x768 resolution
Sound card
A network or Internet connection

---

### Post by kgarbutt on 2010-03-07
Check out SLAMPP. It stands for: Simple Solution for Home Server. Memory requirements are 256MB. I don't run a server so I don't know the details.

---

### Post by Techsnap on 2010-03-07
> **jonabyte said:**
> Slackware, install the minimum and no gui

I second that. Slackware minimal would be a good choice.

---

### Post by blueturtl on 2010-03-07
> **antenna said:**
> A minimal Debian install would be my first choice too, probably with Openbox if you need a GUI.

+1 for Debian. On the other hand if you want more up-to-date packages Ubuntu *can* be installed without a desktop environment too (it's called the alternate install CD) which means it can run on a fraction of the official system requirements.

I have used Ubuntu/Debian on a Pentium 233 MHz with 64 MB RAM, it is possible if you convert to CLI or X+Fluxbox/Openbox. 

Most server software does not require graphics anyway, so your system will run an up-to-date server just fine.

---

### Post by MaxIBoy on 2010-03-07
If you don't need a GUI, then any modern, "cushy" distro will do. I use Ubuntu on my server:

[LIST]
[*]Pentium 2 @ 400 Mhz
[*]196 Mib RAM (used to be 128, upgrade had no noticeable speed improvement.)
[*]360 Mib swap
[*]3DFX Voodoo 3
[/LIST]
The server is, among other things, a torrent slave, NGINX webserver, CUPS print server, and a game server. Runs like a dream. 

In any case, with Wmii, I was able to have a very usable GUI setup on it as well when I was first configuring it. (But don't expect it to be exactly "zippy.")

---

### Post by koenn on 2010-03-07
> **Queue29 said:**
> His computer doesn't even meet the minimum recommended specs for Ubuntu..
The specs you quoted are for a desktop system. 

I run Debian Lenny servers on a couple of old PC's with specs similar to the OP's. They run just fine, doing dns, dhcp, squid, samba, nfs, torrents, ... Just start with a minimal install, and add software as needed. 

Ubuntu server is a CLI system not too different from Debian, so that would work as well.

---

### Post by kaldor on 2010-03-07
I was amazed that Ubuntu Server (old hardy disc I found) worked fine on this old computer. Quick and simple, everything worked.

Why, however, can't I seem to find any CDs or USB drives that are mounted? That was one of my problems on DSL. 

I wanted to try CentOS on this box like one poster said, but.. I thought it would be far too big for such a low-end machine.

---

### Post by cariboo on 2010-03-07
The sever version doesn't auto mount external devices by default. If you have external drives that are always connected you can add the drive to /etc/fstab.

---

### Post by dragos240 on 2010-03-07
> **kgarbutt said:**
> Check out SLAMPP. It stands for: Simple Solution for Home Server. Memory requirements are 256MB. I don't run a server so I don't know the details.

His server doesn't even have 100mb of ram.

---

### Post by NightwishFan on 2010-03-07
Debian stable? Mine boots at 26mb RAM even on 64-bit. Cram some swap in there and your good.

---

### Post by kaldor on 2010-03-07
> **NightwishFan said:**
> Debian stable? Mine boots at 26mb RAM even on 64-bit. Cram some swap in there and your good.

I've already put Ubuntu on it, but I haven't copied anything over yet. Are there any major benefits of using Debian over Ubuntu? I'm willing to try something new.

---

### Post by koenn on 2010-03-07
on a cli system, you would hardly notice any difference. software versions may differ a bit, and if you didn't install an Ubuntu LTS, you'll have to do the 6 monthly upgrade thing; Debian is more manageable when in that respect. 

Ubuntu has a couple of interesting server things going on (Eucalyptus, Virtualisation, ...) but you're not going to use those on *that* server.

---

### Post by kaldor on 2010-03-07
> **koenn said:**
> on a cli system, you would hardly notice any difference. software versions may differ a bit, and if you didn't install an Ubuntu LTS, you'll have to do the 6 monthly upgrade thing; Debian is more manageable when in that respect. 

Ubuntu has a couple of interesting server things going on (Eucalyptus, Virtualisation, ...) but you're not going to use those on *that* server.

I used Hardy. I still had a disc lying around. 

I've been trying to download Debian for the last few minutes, but wow.. their servers are slow! After clicking on my arch it just says "Loading..." and it has been that way for the last 10 minutes or so.

---

### Post by snowpine on 2010-03-07
> **kaldor said:**
> I've already put Ubuntu on it, but I haven't copied anything over yet. Are there any major benefits of using Debian over Ubuntu? I'm willing to try something new.

They are 95% the same, especially at the server level (Ubuntu is basically Debian code repackaged for a different audience). No real reason to switch IMHO. :)

---

### Post by kaldor on 2010-03-07
On another topic, is there any way I can make the server auto mount USB drives? To my understanding, editing the fstab is for permanent drives.

---

### Post by koenn on 2010-03-07
> **kaldor said:**
> I used Hardy. I still had a disc lying around. 

I've been trying to download Debian for the last few minutes, but wow.. their servers are slow! After clicking on my arch it just says "Loading..." and it has been that way for the last 10 minutes or so.
 never noticed them being slow.
maybe try a different mirror ? 

[http://ftp.belnet.be/packages/debian-cd/5.0.4/i386/iso-cd/](http://ftp.belnet.be/packages/debian-cd/5.0.4/i386/iso-cd/)

---

### Post by gordintoronto on 2010-03-07
Spend $20 on a USB to IDE adapter, pop the hard drive out and connect it to the adapter, discard the rest of the "computer."

It was lovely in 1996, but now it has a value of -$50.

---

### Post by NightwishFan on 2010-03-07
Debian and Ubuntu are nearly the same, but Debian focuses on quality and not cadence. (Not that Ubuntu is not high quality, just a term for the focus of their release). Debian Lenny, which is stable, is slightly more up to date than Hardy I think. I would advise either.

The Debian servers are not slow, they probably run Debian. :KS

---

