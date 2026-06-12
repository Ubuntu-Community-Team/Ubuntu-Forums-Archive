---
title: "ubuntu gnome installation and boot failed"
date: 2015-04-02
forum: Ubuntu Development Version
---

### Post by orj-gmail on 2015-04-02
I installed a beta (daily) 29. march. Installation worked and I  had ubuntu-gnome running. Today 2.april there were some updates (don't  know if my problem related to the updates) after a reboot I can't get  into ubuntu-gnome. Grub is coming up (I've a dual install with windows)  and if I choose ubuntu I see the gnome foot and 3 blinking dots or only a  grey screen. Thats all. I used 64bit efi install before. So I tried the  old iso-dvd of my successful install some days before for making a  fresh install. Only came to the foot with 3 dots. Downloaded and burnt a  new iso of today, same result: foot and 3 dots. I've no idea what to  do. Anyone experienced the same or similar problem?
Edit: I can't get in a live session with none of the two isos only get foot...

The isos were properly burned. Checked it. Grub seems to be ok at least I can boot to windows.

64bit efi intel i7 8GB RAM

---

### Post by cariboo on 2015-04-02
Have you tried starting with:

```
nomodeset
```

enabled?

---

### Post by orj-gmail on 2015-04-02
> **cariboo907 said:**
> Have you tried starting with:

```
nomodeset
```

enabled?

No, how I do it? It Is an option to choose when I try to make an install from the dvd-iso?

edit: found some information and did the following: when the dvd boots there is a grub-ui, in the install-option I pressed e, looked for a line linux/boot.....quiet splash. After quiet splash I inserted no nomodeset with a space between quiet splash and nomodeset. Rebooted but the only effect was that the foot and blinking dots were bigger, nothing more happened.
Did the same thing for my installed, inaccessible ubuntu-gnome -> grey screen. What now? I don't know if it matters, I've an ATI-graphic-card.

edit  I wanted to exclude a hardware problem, so I downloaded a fedora-alpha-3-iso and I could boot to live-session. It seems to be something wrong with the ubuntu-gnome-iso, but it seems no other users&testers have this problem. Rare.

---

### Post by ventrical on 2015-04-02
Press any key while iso is booting , choose English then , F6 key then a menu will appear at the bottom and choose <nomodeset>

or

[http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)

---

### Post by ventrical on 2015-04-02
> **cariboo907 said:**
> Have you tried starting with:

```
nomodeset
```

enabled?

@cariboo907

The current method used: [http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

will create a workable image on a USB flash disk, however, after using the <depress spacebar> method of evoking the alternate options page which include the menu to set <nomodeset> it will all work well until you attempt to shut down  or restart the PC. It will present the option to <remove usb and press enter to continue> but it will not shut down. Once manually shutdown it will then not recognize the installable USB disk in BIOS. This is serious bug .. at least for those who try to use nomodeset during pre-install process.

Regards..

---

### Post by cariboo on 2015-04-02
I use either Disks or dd to create a usb boot device depending on which sock I put on first, that particular day. ;) I haven't needed nomodeset for several release, but when my Asus GT-750 graphics card went defective that was the only way I could boot into live media.

---

### Post by sgage on 2015-04-02
I just (5 minutes ago, 20:20 EDT) installed today's daily UG from a USB stick burned with unetbootin. Worked perfectly...

---

### Post by cariboo on 2015-04-02
Nomodeset is only needed if the included graphics drivers won't work with your video card, so depending on a users setup, some installs will work without problems, while others will be nothing but problems.  I have two installs on fairly new hardware, both are uefi systems, although I went with legacy mode on my desktop. When I first got it last year, it was just the normal boring install,  but as time went on and the graphics card slowly went defective installs became more problematic forcing me to use nomodeset to get a working installation. Replacing the graphics card with my old standby GeForce 210, has solved all the installation problems.

I installed Vivid on my notebook system in Secure boot mode, and because of it's Intel chipset, it was just another boring installation. :)

BTW I've got about two weeks to get the GT-750 replaced before the warranty runs out. I best get busy. :)

---

### Post by ventrical on 2015-04-02
> **sgage said:**
> I just (5 minutes ago, 20:20 EDT) installed today's daily UG from a USB stick burned with unetbootin. Worked perfectly...

mkusb also will work. It does not destroy USB install image when trying to exit from <nomodeset> set system. The PC will still recognize the USB in BIOS and boot very effectually. Not so with disks or SDC.

Regards..

---

### Post by orj-gmail on 2015-04-03
> **ventrical said:**
> Press any key while iso is booting , choose English then , F6 key then a menu will appear at the bottom and choose <nomodeset>

or

[http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)

Thank you for the hint, problem solved, now ubuntu-gnome up and running again.

---

