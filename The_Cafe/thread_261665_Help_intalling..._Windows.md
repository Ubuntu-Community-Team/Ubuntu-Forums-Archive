---
title: "Help intalling... Windows"
date: 2006-09-20
forum: The Cafe
---

### Post by Mirrorball on 2006-09-20
A friend of mine just bought a computer and we succeeded at installing Ubuntu on it. But we don't know how to install Windows XP... The setup files are copied from the CD to the hdd but when the computer boots again we get an error message: "Error loading OS."

Hardware
Motherboard: ASUS A8N-VM
CPU: AMD ATHLON 64 X2 4600+ SOCKET939
RAM: 512MB DDR400 - SAMSUNG
HDD: SEAGATE ST3808110AS 80GB SATA II/8MB
DVDR-W LG GSA-H20N

Do we need drivers to install Windows XP on a SATA disk?

---

### Post by Brunellus on 2006-09-20
in a word:  yes.  Windows still doesn't play well with SATA out of the box, I'm given to undertand.

---

### Post by Mirrorball on 2006-09-20
Does Windows only read drivers on floppy disks? The computer doesn't even have a floppy disk drive... :(

---

### Post by Fully216 on 2006-09-20
For dual boot, install windows first then ubuntu.

---

### Post by darkhatter on 2006-09-20
Vista is going to fix that problem, but I believe you need to patch the install cd to include the sata driver, I have no idea how to do it but I'll look for you.

---

### Post by Mirrorball on 2006-09-20
> **Fully216 said:**
> For dual boot, install windows first then ubuntu.
Why? I've already installed Windows first or Ubuntu first, it didn't matter. I only had to reinstall grub.

---

### Post by Mirrorball on 2006-09-20
> **darkhatter said:**
> Vista is going to fix that problem, but I believe you need to patch the install cd to include the sata driver, I have no idea how to do it but I'll look for you.
Thanks, I'm searching Google as well and I just found a tutorial "Installing to SATA _WITHOUT_ a Floppy Disk", it looks complicated but let's see what I can do.

---

### Post by pelle.k on 2006-09-20
It IS comlicated indeed. I tried to create a live-cd out of a custom xp sp2 disk, but it failed over and over again. I got a "special" oem cd from FujitsuSiemens (built for my laptop) thats does work however.
The BY FAR easiest method is to load the drivers from a floppy. Go buy a floppy drive, it'll cost you like 10$ but it's SO worth it.

> Why? I've already installed Windows first or Ubuntu first, it didn't matter. I only had to reinstall grub.
Windows erases grub from MBR, and it doens't add ubuntu to it's own list of operating systems on the HD. That's why you should install windows first.

Do yourself a favour. Download [GAG]("http://gag.sourceforge.net/download.html") (sudo apt-get unzip so you can right click it and extract it....)
burn the cdrom.iso.
When you install windows and it erases grub, use the GAG disk too boot the root partition of ubuntu, then in ubuntu again, do
```
sudo grub-install /dev/sda
```

**Of course, this is not necessary if you choose to install windows first, ubuntu later :) **

---

### Post by Mirrorball on 2006-09-20
I usually reinstall grub using Knoppix (or Ubuntu's live CD). It's really easy, there is no need to install Windows first.
About the SATA driver, I've downloaded a program, NLite. If it doesn't help, I'll get a floppy disk driver, but I hope I don't have to, because it's useless.

---

### Post by Mirrorball on 2006-09-20
NLite did it! If anyone has the same problem, just use this program to add the drivers to the CD.

---

### Post by pelle.k on 2006-09-20
Congrats! :)  I wish it had been that simple when i tried to streamline those freakin' drivers once upon a time.

---

### Post by Mirrorball on 2006-09-20
Fortunately I had never had to install Windows on a SATA hdd. I had tried it once and it didn't work, but I didn't care because that computer was going to run Linux primarily. Meanwhile, a blessed soul created NLite.

---

### Post by PryGuy on 2006-09-21
WindowsXP works perfectly with SATA out of the box! Check is it an active partition you're installing Windows on. Windows can boot from an active primary partition only... ;)

---

### Post by Mirrorball on 2006-09-21
I could only install Windows after copying the SATA driver to the CD. It doesn't work perfectly out of the box.

---

### Post by Brunellus on 2006-09-22
> **Mirrorball said:**
> I could only install Windows after copying the SATA driver to the CD. It doesn't work perfectly out of the box.
ZOMG windows is not ready for the desktop!!!!!1one.

---

### Post by darkhatter on 2006-09-22
windows xp is really old, get a distro from the same year and it'll have the same problem.

---

### Post by PryGuy on 2006-09-22
> **Mirrorball said:**
> I could only install Windows after copying the SATA driver to the CD. It doesn't work perfectly out of the box.Do you have WindowsXP or WindowsXP SP1/2? That probably means a lot 'cause I tried it with SP2 integrated.

---

### Post by pelle.k on 2006-09-22
Windows XP SP2 integrated here, and no it didn't include my SATA drivers. This is also one of the reasons you slipstream such content with nLite.

---

### Post by K.Mandla on 2006-09-22
> **Brunellus said:**
> ZOMG windows is not ready for the desktop!!!!!1one.
:D

Further proof we should have a Windows subforum under 'Other OS Talk'. ;)

---

