---
title: "Lubuntu 16.04: (completely) manual installation possible?"
date: 2015-11-17
forum: Ubuntu Development Version
---

### Post by oui on 2015-11-17
the live runs pretty on my PC but the beautiful graphic installation within the live system doesn't go: after "discover the file systems" (re-traduction from French) nothing more... wait wait wait 1 hour or more...

I would like to try a completely manual installation

how to unpack the initrd.lz

how to start the rebuild of the new initrd.lz for the installed system?

---

### Post by grahammechanical on 2015-11-17
May I suggest that you trying again to install and this time do not tick the box "Install third party software." The live session uses an open source video driver. The installation of third party software brings in a proprietary video driver. You say that the live session "runs pretty." So, I suggest not using a proprietary video driver until after the installation has completed and you can load into a working OS.

I may be wrong but there may be problems with proprietary drivers on your hardware. I would not call the Lubuntu Alternate ISO image a completely manual installation but it does use a text based installer. Look for Lubuntu Alternate amd64 or Lubuntu Alternate i386.

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds)

Regards.

---

### Post by oui on 2015-11-17
Hi
Thank you very much.

The next idea coming: As the live session seems to be completely operable, it would probably be possible to install completely normal using debootstrap?

But I will first read that [notice about initrd and it's build]("https://wiki.ubuntu.com/CustomizeLiveInitrd"), what I did just discover now!
Regards

---

### Post by oui on 2015-11-27
So... All my problem concerning the manual installation are solved.

1. DOWNLOAD:

I did download the two isos being able to be run on my laptop (amd64 + i386) from [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

2. PREPARE SYSTEM TO START ISO FROM HARDDISK:

and start them using grub with following registration in /etc/grub.d/40_custom as superuser (sudo) using your prefered  editor (or cat if you are an ambitious freak ):P !):

```
menuentry "Ubuntu 16.04" {
    insmod loopback
    insmod iso9660
    set isofile="/xenial-desktop-amd64.iso" # <- check here and adapt it!
    search -sf $isofile
    loopback loop $isofile
    linux (loop)/casper/vmlinuz locale=fr_FR bootkbd=us console-setup/layoutcode=us_intl iso-scan/filename=$isofile boot=casper file=/cdrom/preseed/ubuntu.seed quiet splash --
    initrd (loop)/casper/initrd.lz
}
```

after that, you need to make a

```
sudo update-grub

sudo reboot
```

You can now use  the iso live.

3. PHASE UBUNTU LIVE:

if you have enough RAM (I have 8 Gb!) the live Lubuntu system appear with 2 icons on the desk. one icon is an invitation to install on the harddisk.

But, before you hit on it to start the installation, you have to acquire superuser rights (you already have them but ubuntu will require a password and you have no root password at this time!) entering the root password you will:

```
sudo passwd root
```

You can now continue unmounting the iso used at starting time:

```
sudo umount -l -r -f /isodevice
```

4. START NOW THE NEW INSTALLATION

hitting on the icon on the desktop.

Note: this new installation will install grub again. After reboot, you have no immediate access to live systems registered in your old /etc/grub.d/40_custom!

Good luck!

  
THIS IS NOT A REAL COMPLETELY MANUAL INSTALLATION BUT IT WORKS ;) ...

---

### Post by ventrical on 2015-11-27
The standard method we use in development version to restore .iso images to flash drives so that they are bootable and installable (workable) is use ubuntu 'disks' assuming you already have an  ubuntu operating system > 12.04.

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

[s]Using the alternate (manual) method is to  tap the Ctrl+Shift key while the USB is booting and you will get the text menu options to install alternately.[/s]

 What I meant was this correction here -> [http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12144867#post12144867](http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12144867#post12144867)

my apologies..

Regards..

---

### Post by Chanath on 2015-11-27
> **oui said:**
> I would like to try a completely manual installation. 
Do you want to install the live iso completely manually? It can be done.

---

### Post by oui on 2015-11-27
> **Chanath said:**
> Do you want to install the live iso completely manually? It can be done.

oh! it was effective my initial question

(because a completely manual installation make probably free of such limits like RAM size or availability of other hardware components like usb sticks etc. as far as your "main memory" is adequate, you can do all steps with minimal requirements, and can start step by step the new system command line only first etc. I don't like to use USB stick at all: it is my conviction under environmental considerations. USB sticks become to fast to old and are not used any more, because the size of sticks being older than 6 months are considered as ridiculous. stick are a real muck-up of important ressources for the future. it is not easy to recycle them... And I say thanks, a lot of thanks to Ubuntu to give us with the casper iso's to use a away able to use only the main memory, different of Debian, being not using casper but live and I know no way to avoid the use of usb sticks or to avoid to burn and muck-up a rowling CD without need to install Debian! Use USB sticks is conform to the yet existing Debian logic but is absolutely not logic any more with Ubuntu: With casper did Ubuntu made a giant step forward better than Debian! How will you otherwise differentiate Ubuntu from Debian if you don't take care about more progressive technologies...)

---

### Post by Bucky Ball on 2015-11-27
Going for a manual install as you are is a big step as a result of the graphical install not working. Still, you seem to be enjoying the learning curve, but it's probably just a graphics issue. Switching off third-party drivers, as suggested, may have helped, but I didn't see that you tried it. 

Did you try the nomodeset option switch on a regular install? Did you try a [s][minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") or[/s] a server install? They are text based and don't use a graphical interface for the install.

---

### Post by Chanath on 2015-11-28
One more question, oui, do you have another Linux distro installed in your system?

For your 2nd question about initrd.lz, you might find the answer here; [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)

---

### Post by oui on 2015-11-28
> **Chanath said:**
> One more question, oui, do you have another Linux distro installed in your system?

yes, of course, my main OS is lubuntu 14.04 and it works pretty but I know, that it is old. I did for ex. have the need to use Calligra to years ago. It would be nonsens to add it to 14.04 as Calligra is really completely under continuous development and more than 1 1/2 is a terribly long time! Divers functions (see forum of KDE community)  can not be present in 14.04 but are yet solved... for this reason it would be right to adopt a newer OS but, after 14.04 (I am using) will 16.04 the 1th LTS...

and I suppose it is the same with divers other app's (Merkaartor, beginning new again under a new developer staff etc.)...

learn it: you need an really actual system to install the most actual app's ):P

> For your 2nd question about initrd.lz, you might find the answer here; [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)

thank you very much!

---

