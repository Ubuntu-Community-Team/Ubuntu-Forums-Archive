---
title: "Ubuntu Server asks for CD Drive when using USB"
date: 2010-01-01
forum: Server Platforms
---

### Post by Peter09 on 2010-01-01
Can anyone help?

I am trying to install Ubuntu 9.10 Server using a USB stick. The target machine is a headless system with no CD drive. During the boot process all is ok until the installation starts in earnest - it has asked me for language and keyboard details etc. 

The problem then is that the installation fails because it cannot find a CD drive to pull the rest of the system from (despite me using the usb stick). I can not get further than this.

Anyone suggest anything?

---

### Post by BkkBonanza on 2010-01-01
How did you create the usb stick image? With the default method it will install from itself onto the machine. But if it wants to look on /cdrom/casper then you may try making a symlink to the correct location. Something like,

ln -s /wherever_files_are/casper /cdrom/casper

---

### Post by Peter09 on 2010-01-01
Thanks for the reply - it turned out to be a problem with unetbootin, I tried a different utility and all was ok.

---

### Post by WOTHed on 2010-01-03
> **Peter09 said:**
> Thanks for the reply - it turned out to be a problem with unetbootin, I tried a different utility and all was ok.

How did you do it!

I was going to resort to using the alternate install mixed with the server iso .seed file.

Please share with us what you used to get the server iso working?
:D

---

### Post by WOTHed on 2010-01-03
.

---

### Post by Peter09 on 2010-01-04
How did I get it working?

Well do not know really. 

The non-working drive was built using unetbootin started from a terminal, the working one was built by using the menu item

System->Administration->USB Startup Disk Creator

I have no further information than that. Hope it helps.

---

### Post by WOTHed on 2010-01-04
> **Peter09 said:**
> How did I get it working?

Well do not know really. 

The non-working drive was built using unetbootin started from a terminal, the working one was built by using the menu item

System->Administration->USB Startup Disk Creator

I have no further information than that. Hope it helps.

Ok cool, if I could just ask two more things.  
1 Was that from a live cd or from an installed ubuntu (and what version)?
2 If you pointed the program to an iso what was it, ubuntu-9.10-server-i386.iso ?

---

### Post by Skidbladniir on 2010-01-04
I did it from a live CD, with the i386

---

### Post by WOTHed on 2010-01-04
Hmm I have only used the windows version usb-creator.exe I got it from the netbook iso.
I will try the ubuntu linux port one and see how I go.

Someone tell me where i usb-creator.exe is that works?

Or fix it! The one I used would only work on the netbook iso.

It keeps giving some sort of md5sum error but my iso all check out I've checked.

---

### Post by stlsaint on 2010-01-16
i have this very issue as well...i am using hardy iso and usb creator in karmic and i have been unable to install. Ask for cd-rom also!

---

### Post by WOTHed on 2010-01-21
> **stlsaint said:**
> i have this very issue as well...i am using hardy iso and usb creator in karmic and i have been unable to install. Ask for cd-rom also!

Try this site [http://www.linuxliveusb.com](http://www.linuxliveusb.com)

I actually gave up in the end and obtained a drive to plug into my headless box but I will give that site a go eventually for future use.
It's sposed to be really good!

If you ever try karmic server iso from a karmic desktop usb creator I'd love to know too as people have told me it works.

But again for hardy try linuxliveusb.

(the next LTS is only months away!)

---

### Post by WOTHed on 2010-01-21
Ok never mind

From the website:
> These versions WILL NOT WORK :

    * Ubuntu 8.04 (Hardy Heron) , 7.10 (Gutsy Gibbon) and previous versions
    * Any ISO that does not contain a Live system (like alternate and server versions of Ubuntu)


Hm this i what I thought (about the second bullet) it's because server is not a live cd and I'm guessing it needs the bios to run the cd which most usb creators are not made to deal with.

I could be wrong about the bios but obviously usb creator programs are usually made for live systems that have there own independent means of mounting USB's and CD's

But still I'd love you to try converting karmic server's ISO to usb on a karmic deskop usb creator.

Have been getting good reports so maybe ubuntu has come to the party and made something fancy for the latest non live iso's.

---

### Post by alfmarius on 2011-08-29
I managed to get this working thanks to this link: [http://askubuntu.com/questions/56174/install-ubuntu-10-10-server-from-usb-with-grub4dos](http://askubuntu.com/questions/56174/install-ubuntu-10-10-server-from-usb-with-grub4dos) 

When Ubuntu Installer complains about no CD-ROM select go to shell console option,

Use a set of commands like this one:  
mkdir /mnt/tmp
mount /dev/<your USB dev path here, probably sdb1 if you have 1 HDD> ~/mnt/tmp
mount -o loop -t iso9660 <path to ISO on your USB> /cdrom

---

