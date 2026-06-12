---
title: "Server Install Help"
date: 2008-05-10
forum: Server Platforms
---

### Post by mzracer360 on 2008-05-10
I haven't posted here in a while.  The last time was when I was trying to reformat a Mirra backup server that quit working.  Since then, I finally was able to get the BIOS flashed so I could access the BIOS and be able to change it to boot from a CD-Rom drive, and allow the usage of the USB ports.  I have an old CD-rom drive hooked up to it, and a copy of the 8.04 Server Install CD.  Now, when I try to install, I get this error message:
Kernel panic - not Syncing: UFS: Unable to mount root fs on unknown-block (104,1)

thanks,

mzracer360

---

### Post by Rocket2DMn on 2008-05-10
So did the install actually finish and then you get that when you do your first boot?  If this is the case, it seems like a GRUB problem.  If so, then you can use the Super Grub Disk to reinstall GRUB and it should autodetect your installation - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
You can also try and edit the boot entry from GRUB, the first line should be something like "root (hd0,0)", but you need to make sure it is correct drive and partition number (count starts at 0).

---

### Post by Sef on 2008-05-11
Moved to Server Platforms.

---

### Post by mzracer360 on 2008-05-11
> **Rocket2DMn said:**
> So did the install actually finish and then you get that when you do your first boot? 

Nope, this shows up when I try to install.  I've also tried installing 7.10, and got the same error.

---

### Post by koenn on 2008-05-11
It would be helpful if you's say *when* during the install you get this error.

Assuming it's early in the procedure, this may mean that the installer can't loead the initramfs, possibly because it can't read from the CD (bad drive, bad CD, ...). It could also be bad RAM. You could try running memtest and check CD integrety to narrow this down some.

---

### Post by mzracer360 on 2008-05-11
I did the memtest, and it did not have any problems.  I get this error as soon as I type "install" and hit enter.  When I was trying to flash the BIOS, I installed FreeDOS from a CD and it worked just fine. :(

---

### Post by Rocket2DMn on 2008-05-11
So you flashed the BIOS with something other than what the manufacturer provides?  If so, that could be a problem since the new BIOS may have trouble detecting the hard drive.  It could also be that your install cd is bad - did you check the md5sum after you downloaded the iso?
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then the disc should be burned at a slow speed, like 4x, to help prevent write errors.  The built in checker on the cd seems to never actually detect when the cd is corrupted, so don't trust that to tell you if the cd is ok.

---

### Post by mzracer360 on 2008-05-11
The motherboard is a [VIA EPIA Mini-ITX]("http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=21")

[IMG]http://www.via.com.tw/en/images/products/mainboards/mini_itx/epia/epia_mini_itx.jpg[/IMG]

I found the BIOS and supplied flash utility on the VIA website.

edit - I forgot to check the md5sum on the copy of 8.04, but I did do it for my copy of 7.10.

---

### Post by Rocket2DMn on 2008-05-11
Hrmm, so you are trying to install from a usb cd drive?  It may be that although the BIOS sees the CD drive, the installer on the cd has trouble seeing itself and therefore cannot proceed.  You may need to get your hands on an internal cd drive.  I don't really know what else to tell you, it is difficult to troubleshoot when nothing actually is installed or loads.
You may consider some alternate options for installing:
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by mzracer360 on 2008-05-11
I snapped a quick picture with my camera phone of my setup:
[IMG]http://img.photobucket.com/albums/v242/mzracer360/0511081400-00.jpg[/IMG]

I'll look into installing with a USB flash drive, since the semester just ended and I won't need to use mine for school for a couple more months!!!

---

### Post by koenn on 2008-05-11
Is it possible to run Live CD's (Knoppix, Ubuntu Desktop ...) of that cd drive ?
I still suspect hardware trouble (Cd drive malfunction) 'cause the first things that happen when you boot an install disk is
1- liad the installer kernel
2- load a filsystem on a ramdrive

I don't know how FreeDOS boots, so it would be interesting to compare with other linuxes rather than DOS.

---

### Post by koenn on 2008-05-12
I happened to find some installation troubleshooting documentation (while looking for something else)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s03.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s03.html)
might be useful to diagnose / solve your install problems

---

### Post by mzracer360 on 2008-05-12
OK, so i created a bootable flash drive and put the Server Install CD files on it like the website said.  I verified that it was working with my laptop.  I could not get the Mirra to boot from USB though.  
I finally got into my current server PC and stole the cd-rom from it.  When i booted from the CD this time, it came right up when I entered "install".  But then it got stuck on "Detecting Network Hardware."  It displays the screen that says "Detecting Network Hardware" for about 30 seconds but then switchs to a screen that is all white, and that screen fades into a black screen with a small white rectangle along the bottom, then goes back to the "Detecting Network Hardware" screen and repeats.  I have some pictures of what it does, but haven't taken them off of my phone yet.  
Im going to try it some more tonight, but I may just give up.  I'm only doing this for fun, and to see if the Mirra Server is totally screwed, or if can still be useful in some other way.

---

### Post by Rocket2DMn on 2008-05-12
If you have a network cable connected to the computer during install, I recommend disconnecting it.  This at least skips over the part that asks you to configure your network interfaces, though it seems like your not even getting to that step.  It sounds like your computer may just not work very well with Ubuntu Server.  Depending on what you want to use the server for, there are other linux distributions that may see to your needs, some examples being Debian or CentOS (this is essentially RHEL - Red Hat Enterprise Linux).
Good luck.

---

### Post by koenn on 2008-05-12
[QUOTE=mzracer360;4943507]But then it got stuck on "Detecting Network Hardware."  It displays the screen that says "Detecting Network Hardware" for about 30 seconds but then switchs to a screen that is all white, and ... [QUOTE]
this means the installer can't figure out what driver to use for your etwork card, either because it can't detect the make and model, or because the install CD doesn't contain a driver for that NIC. 
Or the NIC is just broken. 

If you run the installer in expert mode you'll probably be given an option to skip that step or work around it by manually specifying a driver (eg a generic NE 2000 driver often works, or you can look up on the web what drivers you could use for the given make/model of network card)

---

