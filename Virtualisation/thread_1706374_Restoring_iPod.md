---
title: "Restoring iPod"
date: 2011-03-13
forum: Virtualisation
---

### Post by Sailor5 on 2011-03-13
Greetings!

So my iPod Touch 2g has been in dire need of a restore for some time now. But I don't have access to a Macintosh or Windows OS I only use the great Ubuntu. I do however have a Virtual Machine with XP & Vista installed. After Googling I found that it is possible to restore your iPod using iTunes via Virtualbox but are un-able to find a tutorial on how do actually do so.

Can anyone link me to one? I tried just installing iTunes and plugging in the iPod. It was a wild stab in the dark, needless to say it didn't work, the only thing I can gather from Googling (is that the proper term?) is that you don't use Virtualbox _OSE_ which I'm using. However the package the web page I was viewing suggested installing was not in the repos?

So anyone know how to do this?

Thanks bye!

---

### Post by Hedgehog1 on 2011-03-13
To get the USB support your iPod needs, you do need to use the non-open-source version of Vbox.

The good news is I think you can just reuse your current XP VM files (no need to reinstall XP or Vista).

iTunes seems to be a very common reason to use vBox among Ubunitans!  It is loaded on my own VM of Win7, too.  :D


***The Hedge***

:KS

p.s. you can make a sharable folder and populate iTunes from that, because when you load the updated iPod software, the iPod is wiped clean.

---

### Post by Sailor5 on 2011-03-13
> **Hedgehog1 said:**
> To get the USB support your iPod needs, you do need to use the non-open-source version of Vbox.

The good news is I think you can just reuse your current XP VM files (no need to reinstall XP or Vista).

iTunes seems to be a very common reason to use vBox among Ubunitans!  It is loaded on my own VM of Win7, too.

Ah thanks! Where do I get the 'non open sourced' version? I again scooted around Google but was unable to find it.

---

### Post by Hedgehog1 on 2011-03-13
The main download page is: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

> VirtualBox 4.0.4 for Linux
Note: The package architecture has to match the Linux kernel architecture, that is, if you are running a 64-bit kernel, install the appropriate AMD64 package (it does not matter if you have an Intel or an AMD CPU). Mixed installations (e.g. Debian/Lenny ships an AMD64 kernel with 32-bit packages) are not supported. To install VirtualBox anyway you need to setup a 64-bit chroot environment.

Please choose the appropriate package for your Linux distribution:

Ubuntu 10.10 ("Maverick Meerkat") i386 | AMD64
Ubuntu 10.04 LTS ("Lucid Lynx") i386 | AMD64
Ubuntu 9.10 ("Karmic Koala") i386 | AMD64
Ubuntu 8.04 LTS ("Hardy Heron") i386 | AMD64
...

Select the i386 if you are running 32 bit Ubuntu, or AMD64 if you are running 64 bit Ubuntu.

You will download a file that ends with a .deb  (mine was called virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb)

In the terminal:

```

/usr/bin/software-center '/home/**[COLOR="Red"]hedgehog[/COLOR]**/Downloads/virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb'
```

Replace **[COLOR="Red"]hedgehog[/COLOR]** with your user name.

***The Hedge***

:KS

---

### Post by Sailor5 on 2011-03-13
Thanks for your continued help but there's yet another problem. I installed VirtualBox and the addon that allows USB 2.0 and although all connected USB devices do show up in the 'USB Devices' list it won't let me check any of them. If I was to put a normal usb stick into the computer it doesn't show up in the VM however like I said it does appear in the list of currently connected USB devices.

What did I miss?

---

### Post by Hedgehog1 on 2011-03-14
There is the USB setup on your Windows VM:

[IMG]http://img683.imageshack.us/img683/2255/vboxusbsetup.png[/IMG]


[SIZE="3"][B]And adding yourself as a Vbox user:  [How-to-Fix-VirtualBox-USB-Support]("http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml")
[/B][/SIZE]


***The VIRTUAL Hedge***

:KS

---

### Post by Sailor5 on 2011-03-14
I did everything you said however the options where still greyed out. It appears I needed to run virtualbox as root before it could use USB devices. But after that everything is working now Huzaaaaa!!!

Thanks for your help Hedgehod!

---

### Post by 300Z on 2011-03-14
What about installing itunes using PlayOnLinux?
I have installed the latest itunes 10.x but haven't tried upgrading my iphone yet.

---

### Post by Hedgehog1 on 2011-03-14
> **300Z said:**
> What about installing itunes using PlayOnLinux?
I have installed the latest itunes 10.x but haven't tried upgrading my iphone yet.
 
Are you suggesting this as an alternative to the (already working) Box install for the OP, or are you asking if it will work for you?
 
Either way is OK, I just am not sure what you re trying to say.  More options are always preffered, and most of us have iPods/iPhones
 
***The Hedge***
 
:KS
 
p.s. As a Hedgehog, I found the iPod Nano 6g is the first iPod small enought for me.  I just wish Hedgehogs had pockets to put things like that in.... :D

---

### Post by 300Z on 2011-03-14
> **Hedgehog1 said:**
> Are you suggesting this as an alternative to the (already working) Box install for the OP, or are you asking if it will work for you?


I suppose that would be both a question and suggestion at the same time? I guess I'm just wondering if anyone tried it that way yet..?

---

