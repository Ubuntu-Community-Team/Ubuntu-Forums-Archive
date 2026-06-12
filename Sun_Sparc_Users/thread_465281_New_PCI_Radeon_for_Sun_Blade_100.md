---
title: "New PCI Radeon for Sun Blade 100"
date: 2007-06-05
forum: Sun Sparc Users
---

### Post by ghotli on 2007-06-05
I've scoured the internet for the answer to this question, and I can't seem to get it working. I have a SunBlade 100 with the server install of Ubuntu 7.04 Feisty installed on it. The operating system works flawlessly as long as I am using the command line. The problems come after I type the command "sudo apt-get install ubuntu-desktop". It's the same Xorg problems that everyone else is having with fiesty. I get the mmap error. I have tried alot of things described in the forums to no avail. I added Option "ReferenceClock" "29.500MHz" to the devices section of the xorg.conf file. That didn't help. 

Anyway, I assumed that the problem was with the linux support for the onboard video card. Consequently, I bought a 64mg ATI Radeon 7000 PCI card and I want to use that card as the default video card instead of the onboard one. 

This is where things get tricky.

By typing show-devs into the OBP, I can see that the sparc box recognizes that the card is present in the PCI slot. I have tried the instructions referenced [here]("http://ubuntuforums.org/archive/index.php/t-257913.html") to change the default video card to point to the new PCI video card. When I do this, I can't get video out of the PCI card or the onboard video and I have to blindly type "set-defaults" and "reset-all" in order to get video out of the onboard video again. Upon further investigation I found that show-displays does not list my PCI video card on it's list of avaliable video cards.

But the plot thickens.

When I boot up into ubuntu and look at the dmesg, it turns out that Linux is recognizing the radeon video card and apparently creating a framebuffer for it. 

Partial dmesg output:

[   53.341611] atyfb: 3D RAGE XL (Mach64 GR, PCI-33) [0x4752 rev 0x27]
[   53.342437] atyfb: 8M SDRAM (1:1), 29.498928 MHz XTAL, 230 MHz PLL, 83 Mhz MCLK, 63 MHz XCLK
[   53.413977] Console: switching to colour frame buffer device 144x56
[   53.437693] atyfb: fb0: ATY Mach64 frame buffer device on PCI
[   53.438590] radeonfb: Found Intel x86 BIOS ROM Image
[   53.447118] radeonfb: Retrieved PLL infos from BIOS
[   53.447136] radeonfb: Reference=27.00 MHz (RefDiv=60) Memory=150.00 Mhz, System=150.00 MHz
[   53.447152] radeonfb: PLL min 12000 max 35000
[   55.378982] radeonfb: Monitor 1 type CRT found
[   55.378994] radeonfb: Monitor 2 type no found
[   55.415270] radeonfb (0000:01:01.0): ATI Radeon QY

So here's my question. Is there a way to write my xorg.conf file so that X only uses the radeon PCI card, instead of going through the broken onboard video card.

---

### Post by cantormath on 2007-06-15
was it hard getting the feisty installed on the sunblade?
How does it run?

---

### Post by ghotli on 2007-06-15
Feisty runs flawlessly on the sunblade 100 for me. Minus the fact that the X server doesn't work. But for my sysadmin responsibilities I don't really need X anyway. Installing Feisty instead of Solaris 10 makes this a box that I can actually use productively. Apt-get works great, and virtual consoles are invaluable. I have a few virtual consoles set up just tailing some logs, and the others are just for logging into different servers. Suprisingly the best thing about switching to ubuntu from solaris is that everything on the console is colorful out of the box. It really makes working in the console environment easier to do.

---

### Post by Crimson Drake on 2007-06-17
From my experience with Sun Blade 100, the only video card you can install is Sun "certified" ... regular cards will not work (tried so many PCi ones) - you will only get a blank screen.

As for X Server, try adding this option for ATi card:

> 
Section "Device"

Identifier      "Generic Video Card"
Driver          "ati"
Option          "reference_clock" "28.636 Mhz"

EndSection


---

