---
title: "Win portable USB on Ubu 17.10"
date: 2017-11-19
forum: Windows
---

### Post by pointy2 on 2017-11-19
* ADMINS...please move this thread if needed, to proper forum.* 

I have a new laptop with AA 17.10 i7 archetecture KabyLake, secured pretty well and am now ready to get to work on this machine. While the Gimp and Inkscape are now installed for my graphics design work, I prefer Adobe PS and AI, which do not run well on Mate. 

Is there a way to run a portable stripped down Win7 from a USB, and is it recommended to run on Ubuntu? I did not want a dual boot, since the start/restart to load the different os' is counter productive for my applications. Only Adobe and light FF browsing would be utilized on the portable Win7.

---

### Post by Irihapeti on 2017-11-19
Since this is about Windows, I've moved it to ***Windows***.

Depending on how much RAM you have, you might be able to run Windows 7 in Virtualbox. I believe that you have to have a full retail version for this to work; an OEM version can only be installed on the original motherboard.

---

### Post by oldfred on 2017-11-19
If in i7, then you have UEFI hardware, did you install Ubuntu in UEFI boot mode?

The Windows 7 installer is BIOS only but can be converted to UEFI.
Because Windows licensing is for one computer, it does not run from portable USB flash drives. 
I believe a eSATA drive will work as it is seen as an internal drive.

---

### Post by yancek on 2017-11-20
When you purchase a microsoft windows operating system medium, you are actually paying them for the right to use one and only one instance of it on one and only one machine.  This is explained in excruciating detail in the EULA for each system.  If you try to install windows on any usb drive you will see the following message:

> "windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports" 

If you have up to date hardware, virtual software might be the answer or oldfred's suggestion.

---

### Post by pointy2 on 2017-11-20
I'm reading that virtual machines don't function well on a wifi connection. I've looked at zen, and virtualbox (which was not recommended by the ubu guru I consulted with). As of now, I'm looking at a couple of Inkscape alternatives for my vector images. As for PS, the Gimp is pretty much fully compatible with PS plugins. I just don't want aall of that garbage that MS packages with their OEM installs. Youtube has a vid of someone running Vector Magic on Ubuntu...seemingly flawlessly. Just no instruction on how that was accomplished.

---

### Post by C.S.Cameron on 2017-11-20
I have been running Windows 7 and 10 in VBox with a Ubuntu host for quite a while now.
It is quite slow running off a flash drive, (it is a USB3 drive but only seem to do USB2 speeds).
Installed on my laptop VBox, it is workable if I only run one major program at a time, (AutoCAD, CAESAR, Firefox).

Edit:
I have one USB2 pendrive with Windows XP installed using the Ngine method: 
[http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)
This might work for running Adobe stuff if installed on a USB3 drive and securely locked down - ie no internet.

---

### Post by pointy2 on 2017-11-21
Thanks for that, CS Cameron. my desision hasn't been made as of yet, and really want to break out of the Window, and learn this Linux system. Got to say, I was so incredibly blinded to the lack of security and ease to compromise an out of the box Windows OS.

---

