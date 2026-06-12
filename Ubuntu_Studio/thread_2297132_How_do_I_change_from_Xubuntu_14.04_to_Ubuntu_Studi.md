---
title: "How do I change from Xubuntu 14.04 to Ubuntu Studio 14.04?"
date: 2015-10-01
forum: Ubuntu Studio
---

### Post by Ranger48 on 2015-10-01
Hello everyone,

I am currently using Xubuntu 14.04 but I would like to change to Ubuntu Studio 14.04. Could someone tell me whether it is possible to do this without losing data or applications? If so, how exactly do I go about it?

Thanks in advance.

---

### Post by qamelian on 2015-10-01
You can simply install the various Ubuntu Studio metapackages via whichever package manager you use. Here is a list of the various metapackages:

```
plymouth-theme-ubuntustudio - Ubuntu Studio Plymouth theme
ubiquity-slideshow-ubuntustudio - Ubiquity slideshow for Ubuntu Studio
ubuntustudio-audio - Ubuntu Studio Audio Package
ubuntustudio-audio-core - Ubuntu Studio Audio Core Package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-controls - Ubuntu Studio Controls is a small application that
ubuntustudio-default-settings - default settings for the Ubuntu Studio desktop
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-font-meta - Ubuntu Studio fonts Package
ubuntustudio-generation - Transitional Package
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-icon-theme - Ubuntu Studio Icon Theme
ubuntustudio-installer - Software installer for Ubuntu Studio
ubuntustudio-lightdm-theme - UbuntuStudio LightDM theme
ubuntustudio-live - Ubuntu Studio live media support
ubuntustudio-look - Ubuntu Studio look
ubuntustudio-menu - Menu for Ubuntu Studio
ubuntustudio-photography - Ubuntu Studio Photography Package
ubuntustudio-publishing - Ubuntu Studio Publishing Package
ubuntustudio-recording - Transitional Package
ubuntustudio-screensaver - Ubuntu Studio screensaver
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
```

---

### Post by tgalati4 on 2015-10-01
Welcome to the forums.

The best way is to backup your projects, personal data, and configuration settings (basically your /home/Ranger48 directory).  Make a installation USB stick of Studio 14.04 and perform a fresh installation, then copy your personal data back.  Keep the same username to make the configuration files work correctly.

An easy way, but prone to breakage, is to change your /etc/apt/sources.list to point to Studio 14.04 and perform a dist-upgrade.  That will leave you with a mixture of Xubuntu libraries and Studio libraries, and some programs may not work correctly.

---

### Post by Ranger48 on 2015-10-01
Hi qamelian,

Thanks for your reply. What about the low-latency real-time kernel? Surely this is important to get the full benefit of the Studio packages?

Hi tgalati4,

Thanks for your reply. A fresh installation seems like the right way to do this, but then I would probably have to re-install all my favourite applications?

---

### Post by jejeman on 2015-10-01
I don't think that installing US over Xubuntu is a good idea. US is made to be installed as a fresh OS.
Just install software that you need.
What do you need? Why go for US?

---

### Post by qamelian on 2015-10-01
I've installed Ubuntustudio on a number of systems by just installing the necessary metapackages and have never had any problems. I've been doing this for years. The low-latency kernel can be installed by installing the package linux-image-lowlatency.

---

### Post by tgalati4 on 2015-10-01
If the metapackage method works, then use it.  If it doesn't, then you know why.

You can get a list of what you have currently installed:

```
dpkg --get-selections > packagesthaticurrentlyhaveinstalledonmysystem.txt
```

---

### Post by Ranger48 on 2015-10-02
Hi jejeman,

I have used Ubuntu Studio before and I really liked the crisp, clean look and snappy response. I thought it would be nice to have the audio and video production tools, but you are probably right. I may as well install the necessary packages only. I would probably not even notice the advantages of the rt kernel.

Thanks for your advice everyone. I will try installing the necessary packages one by one and see what happens.

---

### Post by yoshii on 2015-10-05
> **qamelian said:**
> I've installed Ubuntustudio on a number of systems by just installing the necessary metapackages and have never had any problems. I've been doing this for years. The low-latency kernel can be installed by installing the package linux-image-lowlatency.

Can the linux-image-lowlatency be installed into Lubuntu?  

At one point I was interested in creating a more minimal Ubuntu Studio onto Lubuntu since Ubuntu Studio comes with a lot of stuff I don't need.  

I'm really curious about this.  I use Reaper in Wine currently on Ubuntu Studio.

---

### Post by Bucky Ball on 2015-10-05
Simply install either ubuntustudio-desktop, or, if you just want audio packages, ubuntustudio-audio. For graphics, ubuntustudio-graphics. That's it. Mix and match. For everyone's info, Ubuntu Studio uses xfce4 so installing the ubuntustudio stuff is not an issue and I'm not quite getting some of the posts here. :-k 

ubuntustudio-audio can be installed in any Ubuntu flavour, along with its graphics, artwork and other packages. The RT kernel can be added manually if required (although the low-latency should be just fine). 

Installing packages one by one is the wrong advice and the wrong way to go.

* See post 3 [here]("http://ubuntuforums.org/showthread.php?t=910415&p=5727128&viewfull=1#post5727128"). In other words, the way I've described above has been around for ... seven years, and hasn't changed significantly. It is rule of thumb for adding UStudio stuff to other flavours.

---

### Post by tgalati4 on 2015-10-05
Yes, I misspoke.  It's not the mixture of libraries, it's the configuration differences between a stock Xubuntu installation and an Ubuntu Studio installation.  All it takes is one configuration file to get overwritten and you have a borked system that takes several hours to troubleshoot.

Simply adding the meta-packages should work fine.

Unless it doesn't.

---

### Post by Bucky Ball on 2015-10-05
> **tgalati4 said:**
> Simply adding the meta-packages should work fine.

Unless it doesn't.

hehe. There's always that. :D

---

