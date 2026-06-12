---
title: "Starting my Ubuntu Pentium 3 project."
date: 2010-03-11
forum: Testimonials &amp; Experiences
---

### Post by GeeLo on 2010-03-11
I was given a Pentium 3 Gateway Essentials tower. 

 Specs: Pentium 3 @ 450Mhz
 RAM: 250 MB (maybe more.. have to check again) I think SDRAM PC100.
 64 MB AGP card. 
 Might be a Creative Labs Sound Blaster sound card..
 A NEC Cd-rom drive.
 A HP CD-R Burner
 A internal 100 MB, I/O Mega Zip drive ( have not seen one of those in a while.)
 No hard drive. Installed a 10 GB Western Digital that I had in my parts bin.
 Installed a Gigabit NIC card that I had in my parts bin.
 Installed a PCI ATA card that I had in my parts bin.
 
 So in theory I could have 5 more hard drives installed in this tower, not including the USB External drives that I have.. but I'll have to plan that all out.

Tried to do a "regular" install of Ubuntu 9.10, but I do not have that much memory, so I am installing Ubuntu from the "Alternative" install CD that is just a text installer. Seems to be installing ok.. lets keep our fingers cross.

I did have to clean all of the "dust bunnies out.. but I know for a fact that I need to take the combo power supply / CPU fan out, clean it and put some fan oil in it. Does not look or sound bad.. but I know this thing has been pounded on.

If this installs ok.. this box would make a great Web Server using Apache or maybe a File server. 

More updates later..  ;)

---

### Post by prshah on 2010-03-12
> **GeeLo said:**
> this box would make a great Web Server using Apache

I have a remarkably similar configuration: AMD K6-2 450 Mhz / 256 MB RAM / 10 Gb IDE / Samsung IDE CDROM drive / Iomega Zip 100 internal / 10/100mbps LAN.

I use it as a webserver (with Joomla / Ubuntu 9.10 server / LAMP / no gui).

Forget about using it as a file server; it stutters under streaming loads. Also at one point tried to use it as a security camera recorder; not fast enough, and consumes too much power when compared with an Intel Atom based computer.

---

### Post by armandh on 2010-03-12
here are my OOTB Ubuntu and P-II/III experience

find some memory 
any one junking old boxes should have plenty
there is a big performance jump with 512 [or more with shared video]
same for faster processors lying about

if the mobo has onboard video it may be near junk
some however had onboard PCI video and the AGP slot was good to use.
64 mb is OK but get a better video card for DVD movies and compiz.

if the onboard video is AGP and there is no slot.....
I suggest Puppy Linux as the Ubuntu default compiz is a problem with most all the P-II/III onboard video I have come across.

on the success side
I used a 933 P-III 512 meg mem with a 256 meg video card DVI out as a media box feeding HDMI in to the family room flat screen.

I just did not play video and down load updates at the same time.

DO NOT trust old cd/dvd drives
I have had more install failures from this cause than any other.

a 10 Gb Hdd will do nicely for the OS and "some" storage

933 is about the bottom end for playing a DVD movie
866 starts to get a bit choppy.

if the FSB is 100 Mhz it is limited
the 100-800 I set up with 8.04 has been used by my brother in-law since then.
a rock solid mail and surf tool.

---

### Post by wandalalakers on 2010-03-12
I recommend puppy linux in this case.

---

### Post by juancarlospaco on 2010-03-12
If server: Ubuntu server
If desktop: Ubuntu minimal CD + IceWM

---

### Post by J_Stanton on 2010-03-12
i suggest doing an install with the mini .iso and building it up with lxde, fluxbox, or openbox. other than that, i would recommend puppy linux. or maybe even slitaz.

---

### Post by GeeLo on 2010-03-12
Thanks for the suggestions.. this P3 has been a bit more on the challenging side, seeing how it's not a 64 MB video card as I thought prior.. its an "8 MB" video card. :)

I have heard great things about Puppy Linux on older computers, but I wanted to give Ubuntu a shot. I was able to download the alternative 386 .ISO , made a install disk, and I have 9.10 installed! I love Gnome, but I'm using XFCE as it is a lighter "WM". 

All considering it's not a bad little box.. I have not configured Apache yet. I'm just installing all of the updates for it, then I'll work on using SCP to transfer my web site files and directories over.

More to follow, have a great weekend...

---

### Post by NightwishFan on 2010-03-12
If Ubuntu does not work out, try Debian. I booted my minimal Debian install using only 26mb of RAM. If you want really light, go with DamnSmallLinux, which is based on Debian. It uses a 2.4 kernel, and the whole system is only 50mb.

---

### Post by GeeLo on 2010-03-12
> **NightwishFan said:**
> If Ubuntu does not work out, try Debian. I booted my minimal Debian install using only 26mb of RAM. If you want really light, go with DamnSmallLinux, which is based on Debian. It uses a 2.4 kernel, and the whole system is only 50mb.


Thanks, I have also heard good things about DSL.. but so far so good with Ubuntu.. =D>

---

### Post by kerry_s on 2010-03-13
i have debian lxde on 450mhz 256mb ram, it's much faster then ubuntu was.

---

### Post by GeeLo on 2010-03-13
Well.... the computer is cleaned from the inside out. Added another 10 GB drive, as well as some USB external drives. Got a some web site up.. it's holding up really well. =D>

[http://linux.myeffect.net/](http://linux.myeffect.net/)


Might add a packet sniffer or some sort of IDS.

---

### Post by angryfirelord on 2010-03-14
> I have heard great things about Puppy Linux on older computers, but I wanted to give Ubuntu a shot. I was able to download the alternative 386 .ISO , made a install disk, and I have 9.10 installed! I love Gnome, but I'm using XFCE as it is a lighter "WM".
I would consider using LXDE instead. You still get the GTK icons so it doesn't look as ugly as IceWM, but you don't have to worry about higher memory footprints.

---

### Post by GeeLo on 2010-03-14
> **angryfirelord said:**
> I would consider using LXDE instead. You still get the GTK icons so it doesn't look as ugly as IceWM, but you don't have to worry about higher memory footprints.


Thanks, I'm trying it out now.. very nice and fast. Thanks for the suggestion!


Have a good day.

---

### Post by GeeLo on 2010-03-18
Had one small issue. After installing Ubuntu I did not notice that the highest resolution was 800x600, at first I thought this might of been the card, as it is only a 3DFX 8 MB AGP card. But it turned out that I had to make a orgx.conf file in /ECT/x11 , because Ubuntu 9.10 supposedly relies on HAL.

Then I found info on this page that solved my issue:
[http://ubuntuforums.org/showthread.php?t=907272&highlight=3dfx+voodoo3&page=2](http://ubuntuforums.org/showthread.php?t=907272&highlight=3dfx+voodoo3&page=2)

I was able to put this into the orgx.conf file making "vesa" the default driver. No 3-d effects.. but I was not expecting that any way with such a low end card.
After rebooting, now I have up to 1280x1024 monitor resolution. ;)

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

---

