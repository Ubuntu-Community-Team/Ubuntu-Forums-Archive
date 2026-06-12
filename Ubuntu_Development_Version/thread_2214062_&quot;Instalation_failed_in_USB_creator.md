---
title: "&quot;Instalation failed in USB creator"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by vcbranco on 2014-03-30
Hi,

When I try to create a bootable instalation usb stick I have always the error "instalation failed".

There are something I can do or I have to wait for the bug fix?


Best regards

---

### Post by sdowney717 on 2014-03-30
use unetbootin, it just works even in Trusty, it works.
I can even leave extra files on the flash drive, unetbootin will just overwrite what it needs.
So I easily switch between 32 or 64 bit.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I have never been able to use usb creator.
I think all you need is run thusly.

scott@scott-P5QC:~$ sudo apt-get install unetbootin
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unetbootin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
scott@scott-P5QC:~$

---

### Post by vcbranco on 2014-03-30
In 12.04 works well, never had any problem

---

### Post by sammiev on 2014-03-30
I'm a fan of unetbootin, had troubles will USB creator and never looked back since.

---

### Post by forcecore on 2014-03-30
usb creator has been always fail to me too because i use to create minimal Unity desktop with Remastersys and only unetbootin works

---

### Post by sudodus on 2014-03-30
***Unetbootin*** is a good tool. There are good instructions at this link

 [Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

But sometimes it does not work. If the iso file is a hybrid iso file, you can make a USB boot drive by cloning or 'flashing' it with ***dd***. But dd is risky, and is nick-named 'disk destroyer' for a reason, so I made a shell-script ***mkusb***, that helps you find the correct target drive and make the cloning or 'flashing' operation safer. See this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

All current Ubuntu iso files are hybrid iso files. You can convert many [but not all non-hybrid] iso files to hybrid iso files with ***isohybrid***, that comes with the Ubuntu repositories. If not installed, run

```
sudo apt-get install isohybrid
```

and convert it with ```
isohybrid installer-file.iso
```

See ```
man isohybrid
```

---

### Post by cariboo on 2014-03-30
I've been using dd for the last several releases, and never had a failure. Use the following command:

```
sudo dd if =trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

substitute the name of the iso you downloaded for the one in the above command, and also substitute your usb device location instead of /dev/sdc.

---

### Post by sammiev on 2014-03-30
> **cariboo907 said:**
> I've been using dd for the last several releases, and never had a failure. Use the following command:

```
sudo dd if =trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

substitute the name of the iso you downloaded for the one in the above command, and also substitute your usb device location instead of /dev/sdc.

+1 for dd but I have seen it used incorrectly too many times causing large problems by new comers.

---

### Post by sudodus on 2014-03-30
> **cariboo907 said:**
> I've been using dd for the last several releases, and never had a failure. Use the following command:

```
sudo dd if=trusty-desktop-i386.iso of=/dev/sdc bs=1M
```

substitute the name of the iso you downloaded for the one in the above command, and also substitute your usb device location instead of /dev/sdc.

Sorry for picking of details, but there should be no space between if and the equal sign in the dd command line.

> **sammiev said:**
> +1 for dd but I have seen it used incorrectly too many times causing ***large problems*** by new comers.

This is why I recommend ***mkusb*** instead of using dd directly.

---

### Post by cariboo on 2014-03-30
> **sudodus said:**
> Sorry for picking of details, but there should be no space between if and the equal sign in the dd command line.
This is why I recommend ***mkusb*** instead of using dd directly.

My proof reading skills after working all night, are not what they should be. :) I really should head off to bed. :)

---

### Post by QDR06VV9 on 2014-03-30
> **cariboo907 said:**
> _My proof reading skills after working all night, are not what they should be_. :) I really should head off to bed. :)
  Boy can I relate to this at times;)
Good Night:-\" (Lullaby Here)

---

### Post by vcbranco on 2014-03-30
Thanks everyone

---

