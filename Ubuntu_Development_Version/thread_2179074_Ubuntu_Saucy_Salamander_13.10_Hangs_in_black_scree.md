---
title: "Ubuntu Saucy Salamander 13.10 Hangs in black screen."
date: 2013-10-06
forum: Ubuntu Development Version
---

### Post by trever2 on 2013-10-06
Good evening everyone. This is my second attempt at trying to create a full install of ubuntu on a flash drive and was having some issues.

Firstly, I have an amd a10-4600m HP pavallion dv7-7010us laptop with no hard drive currently in the laptop. Any downloads I needed for the LIVE USB i did through my desktop.

In order to get the install on the flash drive, I used Universal USB Installer to download the ISO to a seperate flash drive to create a LIVE Usb, where I then booted up the laptop and began the installation process to my other flash drive. When given the options, I chose to erase all content and install the Saucy Salamander OS. This took quite a while, but it finally said installation complete and brought me to a screen saying to restart. I tried clicking on the button but it wouldn't restart, so I had to do a hard shut down and boot it up. I removed the Live USB this time and was brought to the grub menu through my other flash drive, where I clicked Ubuntu.

At this time, it started to boot, gave me a purple screen, did the ubuntu loading screen, and then brought me to a black screen. At one point a box at the top right popped up mentioning the ibus update, which i get any time I go into the LIVE USB version.

I've looked this up and tried ctrl,alt,f1, where I then was prompted to enter my username and password, but nothing would happen when I did this, where others mentioned it booting up.
I also took ubuntu into recovery mode, and pressed E to edit the code so that the splash was set to "nomodeset" like many people said, but when I tried to hit f10 to start it up, it brought me to a screen where it just said loading ramdisk. One of the times the screen flicked black a few times but would not boot up still.
Someone also mentioned that it could just be the dim light, but I messed with that and it did nothing.

Other small things to mention, if I try to boot it directly into recovery mode and then switch to regular mode like some people have also mentioned, recovery mode just gives me a black page with a huge script that I don't know what it means and then it just allows me to type at the bottom but nothing does anything.
Also, if I don't go to the boot order on startup, then my computer gives me the message "no bootable OS detected, insert boot disk" or something similar. That also happens if I don't directly choose the file that I want to boot up.
So to get anywhere, I always hit f9, click on files, then either choose grub or the other file that boots straight into the OS. when I choose grub, it works fine, but most of the time when I choose the OS option, it gives me an empty script and all I can do is hit ctrl alt del to go back to the BIOS

To me, it seems like it might be a graphics card driver issue like others have said, but I can't seem to get on to the OS to update the drivers at all.
If anyone has any advice to get it to work, that would be helpful. Otherwise, I'm going to try a previous version and see if it's just this version on my laptop.
I will also try the USB on my desktop when I get home. Thanks in advance.

---

### Post by ventrical on 2013-10-06
I was able to install Lucid for the first time to a USB drive using a bootable CD. I had to download ImageBurn in WindowsXP to burn the image to the CD. The same process can be used to burn an Image to a DVD (as the iso's are bigger now and will not fit on a CD). Once I have the DC/DVD burned I boot the CD/DVD with the flash drive already installed. After the CD/DVD get to the part where it starts to recognize hard drives on the PC it will detect the USB (at least 16GB eh) as a real hard dirve !! Then, install as a normal install from there. Do not choose third party stuff or "updates" from the Ubiquity installer as it will most likely bork your install.

 Hope that helps.

ps. When I install to USB on laptops I take the physical hdd right out. hasn't failed yet. The USB acts like a normal hdd and is actually sometimes faster that an hdd depending on your form factor :) lol If you have an install of Ubuntu on your desktop then use a 2GB USB and SDC. THEN. Boot from that on your laptop with the 16GB (or whatever) USB already installed in the laptop.

Hope this helps too.

*note of caution*

 With Lucid I can stick my USB drives into any PC with any graphics adapter card and it will work but that is not the case with the most recent releases and you will be sure to bork your system's graphics config if you install it in a , lets say, nVidia or Ati graphics chipset and then try to run it on Intel based chipset laptop/pc.

Regards..

---

### Post by grahammechanical on 2013-10-06
> [COLOR=#000000]it brought me to a screen where it just said loading ramdisk[/COLOR]

That is normal. We do not see it when we select Ubuntu from the Grub menu but when we open the Advanced Options sub-menu and select Ubuntu from there it will load an initial ram disk and tell us that it is doing so. If you look through the parameters of the Ubuntu you were editing you would see the instruction to load initial ram disk.

This I think is also normal

> [COLOR=#000000]tried ctrl,alt,f1, where I then was prompted to enter my username and password, but nothing would happen when I did this, [/COLOR]

You are now at a command prompt. We need to enter commands otherwise it will do nothing. May be you are entering commands but you do not make that clear. What commands?

It is also usual on 13.10 for the splash screens to switch from the Grub purple background to the Ubuntu purple screen with the dots and then to a black screen and (hopefully) to the login screen. I even see a black screen between the login screen and the desktop wallpaper.

Most of the things that you mention seem usual if not normal to me. This is the bit that would have helped

> [COLOR=#000000]Other small things to mention, if I try to boot it directly into recovery mode and then switch to regular mode like some people have also mentioned, recovery mode just gives me a black page with a huge script that I don't know what it means and then it just allows me to type at the bottom but nothing does anything.[/COLOR]

Those messages might or might not help identify what is wrong. May I make a suggestion?

Re-install but this time do not tick to install third party software. In this way a proprietary video driver will not be installed. You will load with the Nouveau open source driver. That might work better. Nouveau is the Jack of all trades video driver. Whereas a proprietary driver is appropriate to the video card in that one machine. This is fine if you only use that USB stick in that machine. You can experiment with video drivers after you get a working Ubuntu install. You go to System Settings>Software and Updates>Additional Drivers tab. I just do not trust propietary video drivers when it comes to installing.

This

> [COLOR=#000000]So to get anywhere, I always hit f9, click on files, then either choose grub or the other file that boots straight into the OS. when I choose grub, it works fine, but most of the time when I choose the OS option, it gives me an empty script and all I can do is hit ctrl alt del to go back to the BIOS[/COLOR]

I do not understand. I do not know what you are talking about. But then again I am not familiar with the workings of your machine's BIOS.

Regards.

---

