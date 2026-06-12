---
title: "Ubuntu AIO DVD"
date: 2014-05-19
forum: Ubuntu, Linux and OS Chat
---

### Post by zhpopivoda on 2014-05-19
Hi,

In few words I want to introduce project "Ubuntu AIO DVD".

&#65279;The plan is to bring Ubuntu and some of the official derivatives (Kubuntu, Ubuntu Gnome, Xubuntu and Lubuntu) on one iso file that can be burnt on one DVD or USB flash drive. Every one of them can be used as Live system, with no need of installation on hard drive, or can be eventually installed for full Ubuntu or any other system experience. 

We choose this iso to be multiarch, so that you can choose between 64bit or 32bit systems, depending of processor architecture and other computer hardware, but eventually we added one that is only with 32bit systems. The reason for that is, because Ubuntu, Kubuntu and Ubuntu Gnome usually run on newer machines, with more RAM memory and multi core processors, and on the other side Xubuntu and Lubuntu usually run on low specifications machines and we decided that those two to be 32bit systems. Other iso is for those who still uses 32bit systems and don't care about computer with high specifications.

ISO's can download from Sourceforge
[http://sourceforge.net/projects/ubuntuaiodvd](http://sourceforge.net/projects/ubuntuaiodvd).

We have reached almost 10000 downloads. :)

For more info you can visit our website
[http://ubuntuaio.wordpress.com](http://ubuntuaio.wordpress.com).

Cheers,
zpop and nihil enochian
Ubuntu AIO team

---

### Post by zhpopivoda on 2014-05-26
We are happy to announce:

> Torrents for Ubuntu AIO 14.04 ISO, Ubuntu AIO 14.04 ISO i386 and Ubuntu AIO 12.04 ISO are ready for download.

Torrents can be downloaded from [http://ubuntuaio.wordpress.com/downloads](http://ubuntuaio.wordpress.com/downloads).

Please seed! :)

---

### Post by grumblebum2 on 2014-06-18
I have created a partition just for storing ISO files and use the **/etc/grub.d/40_custom** file to add an iso to the grub menu.
At the moment I have set 2 ISO's to show in the boot menu.
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'ISO Elementary Luna  ' {

set isofile="/distros/elementaryos-stable-amd64.20130810.iso"

loopback loop (hd1,6)$isofile

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject nomodeset

initrd (loop)/casper/initrd.lz 

}

menuentry 'ISO Utopic Development  ' {

set isofile="/distros/utopic-desktop-amd64.iso"

loopback loop (hd1,6)$isofile

linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject 

initrd (loop)/casper/initrd.lz 

}
```

Do know what I need to add to this file for the ```
Ubuntu AIO ISO
``` to show in the boot menu.

---

### Post by zhpopivoda on 2014-06-18
Sorry, but I didn't tried to boot iso from hard drive.

Maybe this will help:
Within AIO iso: 12.04.4 i386, 12.04.4 amd64 and 14.04 efi, are whole Ubuntu iso's. So, in this case, I don't know how to add right path for casper folder.
Within AIO iso: 14.04 and 14.04 i386, are unpacked Ubuntu iso's. You can look inside AIO iso to see where is casper folder and then add right path in your file.

---

### Post by zhpopivoda on 2014-08-13
From 2014-07-16 Ubuntu AIO is part of Linux AIO project. Please visit Linux AIO website [http://linuxaio.net](http://linuxaio.net) for more information about this project.

---

