---
title: "Install Debian 5 From USB Flash Drive"
date: 2009-02-18
forum: The Cafe
---

### Post by Vince4Amy on 2009-02-18
Is there any easy way to install Debian 5 from a USB Flash drive before I wipe the Acer Aspire One and put XP on it. Every time I try to install Debian it complains about there being no CD Rom Drive.

---

### Post by TravisNewman on 2009-02-18
Not for the same version, but this should help:
[http://wiki.flimzy.com/index.php/Install_Debian_on_USB](http://wiki.flimzy.com/index.php/Install_Debian_on_USB)

EDIT: sorry, that's wrong, that's going the other way around.
EDIT 2: try this one [http://d-i.pascal.at/](http://d-i.pascal.at/)

---

### Post by kerry_s on 2009-02-18
[http://wiki.debian.org/DebianAcerOne](http://wiki.debian.org/DebianAcerOne)

---

### Post by Vince4Amy on 2009-02-18
Thanks, But I'm doing this from Windows.

---

### Post by maybeway36 on 2009-02-18
Use the netboot installer from the mini.iso. It's just the kernel and initrd; everything else is downloaded from the Debian mirror.

---

### Post by Vince4Amy on 2009-02-18
> **maybeway36 said:**
> Use the netboot installer from the mini.iso. It's just the kernel and initrd; everything else is downloaded from the Debian mirror.

Thanks I tried that, it complains about the CD ROM not being found. I'm just installing Xubuntu right now to see how it runs I just hope that I can work round the webcam bug in 8.10.

---

### Post by TravisNewman on 2009-02-18
Vince have you tried unetbootin?
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by Vince4Amy on 2009-02-19
> **panickedthumb said:**
> Vince have you tried unetbootin?
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Yes I did, however it complains about the CD-ROM Not being found still.

I tried mounting the USB flash drive to /cdrom but then it complained about it not being a proper CD or something.

---

### Post by Antman on 2009-02-19
Try downloading the [Debian LiveUSB img ]("http://cdimage.debian.org/cdimage/release/current-live/i386/usb-hdd/")and creating a live USB flash with the Linux or Windows instructions listed here: [http://wiki.debian.org/DebianLive/Howto/USB]("http://wiki.debian.org/DebianLive/Howto/USB")

---

### Post by Vince4Amy on 2009-02-19
> **Antman said:**
> Try downloading the [Debian LiveUSB img ]("http://cdimage.debian.org/cdimage/release/current-live/i386/usb-hdd/")and creating a live USB flash with the Linux or Windows instructions listed here: [http://wiki.debian.org/DebianLive/Howto/USB]("http://wiki.debian.org/DebianLive/Howto/USB")

Wow thanks for that info:) do these let you install from the Live Image?

---

### Post by Antman on 2009-02-19
Ouch... I just tested this with my 1gb USB stick. It boots up fine, but I don't see an installer. ](*,)

---

### Post by Vince4Amy on 2009-02-19
I couldn't find one either, XFCE Debian was much better than Xubuntu.

---

### Post by Antman on 2009-02-19
I haven't tried this yet, but maybe this will work:
[http://numpanglewat.wordpress.com/2009/01/23/installing-debian-lenny-from-a-usb-memory-stick-usb-hdd/]("http://numpanglewat.wordpress.com/2009/01/23/installing-debian-lenny-from-a-usb-memory-stick-usb-hdd/") 
I don't see a Windows option listed here though.

---

### Post by Vince4Amy on 2009-02-19
Thanks for that, I managed to get access to a Linux machine to do this:)

---

### Post by maybeway36 on 2009-02-19
Debian doesn't have a live CD installer in Lenny. I hope it does for Squeeze.

---

### Post by Antman on 2009-02-20
> **maybeway36 said:**
> Debian doesn't have a live CD installer in Lenny. I hope it does for Squeeze.
Yeah... found that out the hard way.;)

Score one for Ubuntu, Mepis, Fedora, sidux, and openSUSE. :KS

---

