---
title: "Ubuntu 8.04 in Virtual PC 2007 refuse to show desktop"
date: 2008-08-06
forum: Virtualisation
---

### Post by 33333248 on 2008-08-06
Hello.

I downloaded the ubuntu 8.04 and intended to emulate it in virtual pc 2007. I have given it 768Mb ram and a 15Gb Hdd (virtual). I start the virtual pc (VPC) and tell it to load off the ISO file. It does. the boot screen shows up.
Now i go to "start ubuntu (no change)" and this results in the screen going black, and giving me the error...,

[  166.365624] isapnp: checksum for device 1 is not valid (0x89)
And a pop-up

An unrecoverable processor error has been encountered.
The virtual machine will reset now.

I have also tried the trick where you press F6 and replace the last word with about 30 characters, this achieves the same effect
I am using VPC on my Aspire (see signature for specs)

Can some one please help me out here? 
Would be much appreciated.
Thanks

p.s. I am very new to linux, and i really do not like command line interfaces.

---

### Post by Garratt on 2008-08-22
[This Link worked for me...]("http://arcanecode.wordpress.com/2008/04/07/installing-ubuntu-804-beta-under-virtual-pc-2007/")


But i did get the exact same error you described, i just reset, and the third or 4th time it worked...
I still get the same errors on loading screen but the system doesn't get stuck on it like it did the first few times, now it just continues loading.... so if you really wanna try it just keep resetting the maching untill it works.

 also i turned OFF hardware assistance the time it worked, so this might make all the difference, or it might make no difference...

Kinda a waste of time tho, xvmbox or vmware is better alternative.
because vpc additions cannot be installed, so you got no decent resolution and cannot share files, or drag and drop files, etc...

---

### Post by 33333248 on 2008-08-24
Thanks heaps. I tried the reseting thing, and disabling the hardware emulation, but it still refuesed to boot. 

I found my old 7.04 disc the other day and removed my hard disks from the motherboard and power sources, and installed it into my SD card. I have given up on the virtualization, and just did a regular install. It was ok, until i tried to change the screen flicker. i changed it from 75hz to 60hz, and logged off. i logged back in, and the screen had gone striped, with about 3 different screens on the same one. I changed the resolution to 800x600, and logged off again. This time i was left with a garbled screen even worse than the last, and about 7 copies of the screen. My monitors native resolution is 1440x900 and its LG. I was using the VGA port.

---

