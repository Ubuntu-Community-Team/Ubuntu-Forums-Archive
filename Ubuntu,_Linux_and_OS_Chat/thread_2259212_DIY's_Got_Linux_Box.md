---
title: "DIY's: Got Linux Box?"
date: 2015-01-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2015-01-02
I'd like to chat with other builders about the mini-itx form factor Linux box -- or others. I could have put this post in Hardware but this post is for "watercooler chat" rather than a problem.

As you can see from my specs below, this is my (first) mini-itx form factor Linux box. The standard form factor for the itx motherboard is 170 mm x 170 mm (6.75" x 6.75"). The external dimension of the smallest available case, which is the M350 Mini-Itx enclosure, is 192 mm x 210 mm x 62 mm.  I intend this build for world travel, particularly in developing countries. I can seal this computer in a one gallon ziplock bag with silicate gel to protect it from moisture, wrap this in bubble wrap to protect against shock, and throw the whole computer in a small shoulder bag.  Then, wherever I go, I can buy a used LED monitor with a D-Sub connector, grab a mouse and keyboard, and I'm in business.  Plus with dual Linux OS's, Xubuntu and Ubuntu 14.04 LTS, I always have one backup OS should I need to investigate a crash from the same system hardware.

The mobo is an industrial board, the same used in banks for ATM machines, with COM ports, that is the NF9JQ87 by jetwaycomputer.com, an impressive website with ample documentation.  Although an expensive board, it has excellent backward compatibility for outputting to a D-Subbed display most commonly available in developing countries: two Ethernet ports, PS keyboard and mouse, also critical because most used mice are not USB, USB 3.0 and 2.0, and, most importantly, for monitor output--D-Sub and Div-X and HDMI.

An excellent U.K. site is: mini-itx.com  An excellent U.S. site is: mini-box.com  Both sites will teach you about the components that are available for this form factor. Essentially, we are talking about a full-featured desktop computer in a very small size which incorporate two differences from the ATX cpu: a. There is no discrete power supply. Instead the power supply consists of capacitors on the 24 pin motherboard connector, otherwise the same as ATX, b. There is no discrete graphics card; instead one relies on embedded graphics as in the Haswell chip. (I can still run Second LIfe reasonably well). There is one PCI-e slot but this is generally utilized with a riser so as to put in a board at right angles. There was no room for the SSD, so I installed that with industrial velcro. You've probably seen that even in desktop cpu cases that case builders, to my knowledge, are not yet building cases with permanent SSD options; you have to use an adapter.

This post is an invite for chat about YOUR mini-itx builds or YOUR Linux builds in general.

---

### Post by DuckHook on 2015-01-03
A wonderfully offbeat thread, but where to begin?

Well... may as well get the bad news out of the way first. The integrated graphics on this thing is going to give you conniptions. If it's like mine, it's a GMA 3600 that uses the Cedarview driver. This is a proprietary steaming pile of excrement driver that will send some monitors into shutoff mode, and render others smoking. Either way, you will be left dumb, deaf and blind. When it does recognize the EDID on a monitor and actually manages to drive the screen, it will confine itself to a little XGA-sized corner of the console. Thankfully, for monitors on which it actually works, X11 will occasionally successfully resize the framebuffer to give you proper resolution. But it's still a gawdawful, buggy, idiosyncratic, haunted piece of kit that will have you tearing your hair out or blubbering like an idiot trying to make it work. It will show an active connection to a non-existent laptop screen that you simply cannot turn off no matter what parameters you send to it either through xrandr or at boot. It is absolutely imperative that you install your OS with the alternate DVD and choose ssh-server at install time so that, in the event you are left blind, you can ssh into the guts of the system to fiddle and fuss with it. Documentation is awful. The phrase "spartan" is not even close. I appreciate your link, because it's the first time I've seen actual meaningful specs on the thing&#8213;the ASUS site being worse than useless. It appears to be the little orphan that they would rather forget.

The good news is that once you actually get it working, it's a tiny little thing that takes just itsy-bitsy sips of wattage, is completely solid state, and can run unattended for months. Mine came in the form of an ASUS EB1030, is about the size of a large paperback, and is as light as a bird. I have it running a command-line minimal Ubuntu, but with two hyperthreaded cores, it does a wonderful job of acting as my torrent server, NAS server backup and NTP server. I am also considering turning it into a VPN server, VM server and gateway, but don't know if I want to have so much exposure on one machine. It certainly has the CPU horsepower to tackle far more than it's handling now.

If the graphics system could just be garburated and replaced with something not high on drugs, it would be a fantastic solution to so many things.

Let us know how it goes. For my part, I've never dealt with such a schizophrenic little box of contradictions in all of my HW dealings, and I've had to wrestle with some pretty ugly alligators.

---

### Post by gordintoronto on 2015-01-03
I've run Mint from a live CD on a Zotac Zbox with an i3 processor, and everything just worked. I actually installed the pfSense firewall/router, and that worked perfectly. (Two gigabit Ethernet ports make a great firewall!) Also installed Windows 8.1 pro with Classic Shell on another unit, and it works nicely...

The Zbox is not cheap, but it sure works. I would love to try one with an i5 and a big SSD.

---

### Post by bytr on 2015-01-04
My computer was built in 2013 with the following components:

[LIST]
[*]Motherboard: ASRock H77M-ITX
[*]Processor: Intel Celeron G1610 with PCCOOLER S85
[*]Memory: UMAX Cetus DCDDR3-16GB-1333
[*]Storage: PQI Tiffy (as Live USB), WD Red WD20EFRX
[*]PSU: FSP FSP135-AHAN1
[*]Chassis: abee acubic E10G
[/LIST]
And I'm always using the pre-configured Ubuntu as a live session user, it was created by using the Ubuntu Customization Kit.

---

