---
title: "Clean install Lubuntu on Lemur Ultra"
date: 2013-06-30
forum: System76 Support
---

### Post by ciaran1980 on 2013-06-30
I have been running Ubuntu 13.04 on my Lemur Ultra. It is a little sluggish for my liking and I would like to clean install Lubuntu. I am quite a novice when it comes to installing Linux distros. If anybody could give me some guidance on how to go about this on this hardware from a LiveUSB, I'd be very appreciative. Also, does anybody have any experience of running Lubuntu on System76 hardware. Are there any issues?

---

### Post by sudodus on 2013-06-30
If you have already backed up your data, you can make mistakes, that costs only a little time :-)

A clean install would be the easiest way to install, particularly if you accept the default installation that the installer wants. It should give you one root partition with the operating system and space for your files, and one swap partition, to be used, when the RAM cannot contain all the data, that needs to be remembered.

Do you have a 32-bit alias i686 version or a 64-bit alias amd64 version of Lubuntu? Or have you not downloaded anything yet?

And what about the present system, Ubuntu 13.04, 32-bits or 64-bits?

An alternative, particularly if you have not downloaded lubuntu yet, is to install the desktop environment only:

```
 sudo apt-get install lubuntu-desktop
```
or
```
 sudo apt-get install lubuntu-desktop --no-install-recommends
```

This will install the desktop environment with or without the extra tools, that come with lubuntu, and you might not need, because you have tools from Ubuntu.

You can select session (lubuntu or ubuntu) at the login screen (click the circular icon in the attached picture).

The other desktop's files take some space on the hard disk drive, but they are not running, so you will see a big difference in performance between lubuntu and ubuntu.

---

### Post by snowpine on 2013-06-30
Simply install "lubuntu-desktop" with a few mouse clicks in the Software Center, then log out and select it from the login screen as sudodus suggests. :)

If you want to completely uninstall the Unity desktop (it will not speed up your computer, but it will reclaim a little extra hard drive space) then follow this tutorial: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

---

### Post by amjjawad on 2013-06-30
> **snowpine said:**
> Simply install "lubuntu-desktop" with a few mouse clicks in the Software Center, then log out and select it from the login screen as sudodus suggests. :)


Hi,

Please note that installing "lubuntu-desktop" is NOT like installing Lubuntu (Fresh New Install). Two different approaches :)

Just to be extra clear so that the OP knows what is going on!

Thank you!

---

### Post by snowpine on 2013-06-30
> **amjjawad said:**
> Hi,

Please note that installing "lubuntu-desktop" is NOT like installing Lubuntu (Fresh New Install). Two different approaches :)

Just to be extra clear so that the OP knows what is going on!

Thank you!

There is no difference. The Psychocat tutorial I linked to above will give you "pure" Lubuntu just as though you had done a fresh new install (but much less effort).

Lubuntu = Ubuntu + LXDE + application suite

---

### Post by amjjawad on 2013-06-30
Hello and thank you for choosing Lubuntu!

> **ciaran1980 said:**
> I would like to clean install Lubuntu. 

1- Make sure to  backup your Data

2- [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

3- During the installation, for me, I always choose "Something else" but that is me. I'd like to have more control over the installation process and create the partitions I need. I usually use GParted to prepare the partitions (Root, Home and SWAP partition) and then install. It is your call :)

[IMG]http://i42.tinypic.com/2qv44z9.jpg[/IMG]


Your Q is quite general and to give you a general guide, I need to give you a Full HOWTO which is not ready yet from my side - used to write so many HOWTOs in the past. There is actually a Wiki Page that I really need too update but I have no time.


> I am quite a novice when it comes to installing Linux distros. 


Do not worry, installing is really easy when it comes to Ubuntu and its variants. I know, it is easy for me to say it because I have done more than 1000 installations in the past 2 years but trust me, it is easy for you too if you know what you are doing. IMHO, the best way to practice is to use Virtual Machines or install Lubuntu to USB Drive: [http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Thanks!

---

### Post by amjjawad on 2013-06-30
> **snowpine said:**
> There is no difference. The Psychocat tutorial I linked to above will give you "pure" Lubuntu just as though you had done a fresh new install (but much less effort).

Lubuntu = Ubuntu + LXDE + application suite

I think you did not read my post carefully. I was very much accurate and specific :)

[http://ubuntuforums.org/showthread.php?t=2158735&p=12712383#post12712383](http://ubuntuforums.org/showthread.php?t=2158735&p=12712383#post12712383)

I have mentioned clearly that:>  installing "lubuntu-desktop" is NOT like installing Lubuntu (Fresh New Install)

Commenting on your statement: 
> **snowpine said:**
> Simply install "lubuntu-desktop" with a few mouse clicks in the Software Center, then log out and select it from the login screen as sudodus suggests. :) 

I did not comment on your link :)
I was commenting on installing "lubuntu-desktop" package over an installed Ubuntu (or any other variant). So, I was very specific and careful of what I'm stating.

As for your link, I have never ever tried that so I can't advise something I haven't tried - this is how I help others.

Installing the desktop package over an installed system will increase the disc space + the packages + there will be the apps of both the installed system and the desktop package that one installed. In this example, the user will have both Ubuntu's Apps + Lubuntu's Apps.

However, the link you suggested (which I did not comment on), it could fix this issue and leave the user with pure Lubuntu Installation.

FOR ME, I always prefer fresh new installation but that is me. YMMV :)

Thank you!

---

### Post by ciaran1980 on 2013-06-30
Thanks everybody for their input! The installation wassurprisingly straightforward. I created a live USB using [UNetBootin]("http://unetbootin.sourceforge.net/"). I choose the USB as the boot device and did a clean install choosing the "Erase Ubuntu 13.04 and reinstall" option. The entire installation took a total of twenty minutes. I changed the boot device back to the computer. My first impressions are extremely positive. The system is much more responsive. Everything seems to working fine out of the box (wifi, etc). Thanks again!

---

### Post by amjjawad on 2013-07-01
> **ciaran1980 said:**
> Thanks everybody for their input! The installation wassurprisingly straightforward. I created a live USB using [UNetBootin]("http://unetbootin.sourceforge.net/"). I choose the USB as the boot device and did a clean install choosing the "Erase Ubuntu 13.04 and reinstall" option. The entire installation took a total of twenty minutes. I changed the boot device back to the computer. My first impressions are extremely positive. The system is much more responsive. Everything seems to working fine out of the box (wifi, etc). Thanks again!

This is like Music to my ears. Well, didn't hear it though, just read it :D

I'm very glad to know that and I'm even happier that you like it ;) 

Thank you for choosing and using Lubuntu :)

Should you need anything, make sure to bookmark this link: [https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)

Enjoy the speed and simplicity ;)

---

