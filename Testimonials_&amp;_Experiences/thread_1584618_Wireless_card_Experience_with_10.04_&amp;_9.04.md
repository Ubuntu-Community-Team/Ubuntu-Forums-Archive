---
title: "Wireless card Experience with 10.04 &amp; 9.04"
date: 2010-09-29
forum: Testimonials &amp; Experiences
---

### Post by Orion2014 on 2010-09-29
So I've been using Ubuntu since version 7 now and it is, hands down, my favorite operating system. 

However, I recently acquired a small HP desktop and decided to install Ubuntu 10.04 on it, as I already have it running on my Dell laptop and have been running it for a while without issue. 

This desktop was a nightmare when it came to setting up my wireless card. I tried using a tangent PCI card, which would not work. I then broke out an old Linksys WUSB11 v2.6 I had laying around, still wouldnt work. 

I looked around on the net and after a while I found this page:

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)

So, I took a leap of faith, downloaded 9.04 LTS and installed it. And just like that, im up on the net. So just for kicks, I upgraded it through the software update and did not get rid of any packages in the process, thinking if its a driver issue, the driver should still be in tact after the update. 

No Mas, didnt work. 

So, I reverted back to 9.04, gave it a good update, and I think ill be fine running on 9.04 on my desktop. Its still a good, solid OS. 

But, I have to wonder, why would there be a driver in 9.04 that isnt in 10.04? I thought drivers were added, not taken away? Why would you lose support for a piece of hardware when updating versions like that?

Any input would be helpful.

---

### Post by ventrical on 2010-09-29
I don't think I can add anything that could be of help, but, I will say that I have taken my 8 GB persistive PenDrive with Ubuntu 10.4 and ran the OS on different PCs and it appears that Ubuntu 10.4 (and perhaps even earlier versions) have some sort of adaptive-roll-up|roll-back algorithms or routines.

What I mean to say is that I can take a HDD or thumbdrive with Ubuntu or Fedora 13 and then go and hook them up to other PCs and then back to the original PC and  if there was a dependency that was not being adressed, then it was adressed and resolved on the second or 3rd boot.

  I know this sounds weird but that what is happening on some of my PCs.  I can't adress the HP wireless prob. I do have an HP 733MH Pavilion and Ubuntu10.4 worked good but I decided to put Lubuntu on it. I also have Lubuntu installed on another pendrive and used that on an Acer 1.5MHz Inspiron. At first It would not detect the atheros wireless card so then I put the thumb drive into another socket and  the wireless icon configuator popped right up and I enetered in my WEP

Bingo ! :)

---

### Post by Orion2014 on 2010-09-29
If your suggesting that 10.04 "adapts" to hardware over time after either updates or excessive reboots, I tried that. The closest I got to it working was using ndiswrapper and it actually did SHOW the wireless networks, but it wouldnt connect to them. 

And no its not my router, because its working fine now. 

I just wonder why they would make changes like that from one distro to another that actually dumbs down the OS.

---

### Post by Arthur_D on 2010-09-30
AFAIK, if there's noone to maintain a driver, it's taken out of the kernel. Bad drivers can in certain circumstances harm hardware, so I understand the reasoning.

---

### Post by cchhrriiss121212 on 2010-09-30
I had the same issue with a USB wireless device, it still works but I have to do this:
Step1: add "blacklist rt2800usb" to:
/etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
/etc/modules
Step3: Reboot.

You may need to do something similar. It worked fine with 9.04, but needs this fix for 9.10 and has still persisted with 10.04. It's annoying as I found out that it is not an issue with another Debian based OS.

You get regressions in hardware support with every release, Ubuntu seems to be a case of 2 steps forward and one step back sometimes.

---

### Post by ilna on 2010-09-30
> **cchhrriiss121212 said:**
> I had the same issue with a USB wireless device, it still works but I have to do this:
Step1: add "blacklist rt2800usb" to:
/etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
/etc/modules
Step3: Reboot.
I have also tried to use rt2870sta under Maverick testing. The problem is the module loading doesn't create an appropriate device, i.e. 'ifconfig -a' doesn't show ra0 (or wlan0) inteface.

BTW, I have added my USB WiFi adapter to udev, and the module is loading after plugging the adapter in. But without creating an approriate device. /etc/Wireless does contain an approriate .dat file.

All above is related to ubuntu stock kernel rt2870sta module. Have tried to compile last Ralink's one, but have got a compilation error.

Where to dig in?

---

