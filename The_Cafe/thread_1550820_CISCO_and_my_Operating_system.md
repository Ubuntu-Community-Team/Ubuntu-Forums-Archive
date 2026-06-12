---
title: "CISCO and my Operating system"
date: 2010-08-11
forum: The Cafe
---

### Post by cap10Ibraim on 2010-08-11
I started a CCNA course , I find myself using windows command prompt , I searched a little and find the alternatives for a linux OS 
the question is do I need windows ? or it's just some commands and I'll be fine with Ubuntu? 
plus any tips for this course ?

---

### Post by conundrumx on 2010-08-11
> **cap10Ibraim said:**
> I started a CCNA course , I find myself using windows command prompt , I searched a little and find the alternatives for a linux OS 
the question is do I need windows ? or it's just some commands and I'll be fine with Ubuntu? 
plus any tips for this course ?

It depends what you're doing...

I assume you're using the command line interface, in which case any OS will be able to acess Cisco devices.

---

### Post by juancarlospaco on 2010-08-11
I finished it.

You dont need windows, windows is not nice to use with these,
even windows 7** dont have** Telnet/hyperterminal/sshClient on ALL versions, thats sux.

I use Ubuntu with its tools.
I use ssh, **Moserial** for Serial Terminal.
Not being a FanBoy, just Remember that** TCP/IP stack Born on Unix-Like systems**,
Microsoft just copied these.

If you want Tips,* mmm...*
*[SIZE="1"](im assuming that you already know some Bash)[/SIZE]*
use SSH, PuTTY, nMap, NetCat, use Moserial, get Cisco Packet Tracer, Wireshark,
get GNS3, get NetEmul, get JNetMap, PacketETH, GIP *(ip calculator)*, ARPing,
Jubarte Telecommunications Suite, Dia, Remmina, Complete AIRCrack Suite, Yersinia, driftnet.

On Hardware get a USB-to-Serial-DB9 adapter, and a DB9-to-RJ45 Serial cable as assentials.
*[SIZE="1"]Maybe a WIFI card that support Master Mode can be nice for learning some things[/SIZE]* ;)

Packet Tracer sux, it dont have features required for complex labs, 
but for the start is just fine, on meantime learn to use GNS3 using REAL ios.

Dont use IOS HTTP interface, stick with the CLI.

Dont be impressed by the Cisco hardware, these are just a mips computer,
i installed Linux on a Cisco 2600 router, very funny!, compiled an uClinux.

Not related to ccna but learn to use Quagga, 
that have the same protocols that Cisco, but not the Propietary ones, it have the same CLI.
Not related to ccna but learn to configure a Linux box to use the CLI throught the Serial port *(DB9)*, 
you can make a nice linux router with these. ;)

Good Luck.

---

### Post by lz1dsb on 2010-08-12
Great advices! I also use some of those programs you mention. The TCP/IP stack was really developed on Unix-like environment by Vint Cerf and Bob Kahn... juancarlospaco, how were you able to start Linux image on a Cisco Router? Basically you have to create a binary image, right?

---

### Post by juancarlospaco on 2010-08-12
> **lz1dsb said:**
> how were you able to start Linux image on a Cisco Router? Basically you have to create a binary image, right?

Check the uClinux project, 
its the Linux Kernel but optimized for embebed platforms,
if you ignore the Cisco Marketing, those routers are a PC,
with a cheap Mips processor, it have rom, ram, solid storage, and such.
You have to compile your kernel onto the binary image, 
i do it just for fun :)

---

### Post by kevin11951 on 2010-08-12
> **juancarlospaco said:**
> Check the uClinux project, 
its the Linux Kernel but optimized for embebed platforms,
if you ignore the Cisco Marketing, those routers are a PC,
with a cheap Mips processor, it have rom, ram, solid storage, and such.
You have to compile your kernel onto the binary image, 
i do it just for fun :)

What about OpenBSD?  You can run them on MIPS I believe, and its PF firewall is (IMO) better than Cisco's.

---

### Post by lz1dsb on 2010-08-13
> **juancarlospaco said:**
> ...
if you ignore the Cisco Marketing, those routers are a PC,
with a cheap Mips processor, it have rom, ram, solid storage, and such....
I completely agree with you. For so many years working in networking, I agree that Cisco is quite good in marketing ;) But that's true for all other major players.
Thank you, I'll check it out and give it a shot...

---

