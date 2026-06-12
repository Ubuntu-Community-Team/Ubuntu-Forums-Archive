---
title: "I'm Confused."
date: 2016-03-10
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2016-03-10
Hey all.

I'm confused as to life cycle support so here is what is installed.
Lubuntu 14.04.1 LTS 32 bit.

System:    Host: Dell-Precision-380 Kernel: 3.13.0-79-generic i686 (32 bit, gcc: 4.8.2) 
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Precision WorkStation 380


I keep reading that Lubuntu 14.04 is only supported until 2017.
I have also read that any 3.13.xxx kernel is an LTS and supported for 5yrs until 2019.

Original install was from Lubuntu 14.04.1 iso download.
In my system info it shows ubuntu 14.04.4 LTS.

So which could it be 3yrs or 5yrs. 
I have read about the hardware enablement stacks etc and now I'm really confused.

Thanks

---

### Post by QIII on 2016-03-10
Hello!

Lubuntu's LTS cycle is 3 years.

---

### Post by grahammechanical on 2016-03-10
It does take a lot of peering at the screen to understand what the devs are talking about. Here is the wiki page. Look at the chart 14.04.x Kernel support.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

1) If we installed 14.04.0 with kernel 3.13 and are still on it, then the kernel will be supported with security fixes until April 2019.
2) If we installed 14.04.1 with kernel 3.13 and are still on it, then the kernel will be supported with security fixes until April 2019.
3) If we installed 14.04.2 with kernel 3.16 then the kernel will only get security fixes until August 2016.
4) If we installed 14.04.3 with kernel 3.19 then the kernel will only get security fixes until August 2016.
5) If we installed 14.04.4 with kernel 4.2 then the kernel will only get security fixes until August 2016.

These are called point releases and it is possible to upgrade to the next point release without upgrading to a newer kernel. To get the newer kernel we need to run a command to bring in the upgraded hardware enablement stack with the newer kernels. Once we have upgrade from kernel 3.13 then we have to continue upgrading the hardware enablement stack to continue to get kernels that are still being supported.

Those using 14.04.2; 14.04.3 & 14.04.4 will need to upgrade to the hardware enablement stack of 14.04.5 to get kernel support until April 2019. To find out what kernel we are running,

```
uname -r
```

Of course, by August 2016 we might be thinking of upgrading to 16.04 and starting the process all over again.

Regards.

---

### Post by poorguy on 2016-03-10
Hey QIII,

That is what I have read and that is what Lubuntu forums show.
So not all LTS distros are 5yrs. 
The hardware enablement stacks are confusing to me.

Thanks.

---

### Post by poorguy on 2016-03-10
Hey grahammechanical,

The link you posted is where I have been reading and is probably how I confused myself.  It is somewhat confusing.

Ran the code (uname -r) you posted and this is my kernel (3.13.0-79-generic) so I'm good untill 2017.

Thanks.

---

### Post by mikodo on 2016-03-11
Yes but, that is only for the kernel. The lubuntu maintainers are only going to support the libraries for it until it is EOL which, as you pointed out is in 2017, (that is usually because of less developers and maintainers to maintain longer LTS's  and to be be able to also attend to the 9 month interim cycles between them with, the effort it takes to develop, test and fix new bugs).

 Xubuntu (also has 3 years support. Again, not as many devs and maintainers as Ubuntu. Now though, if one runs Xubuntu longer than the support cycle, it is not a good idea generally as there can be libraries too that are not supported that can be a security or compatibility problem . With Lubuntu, the little I understand of its' development right now, it is even a little more of a problem as, they are rapidly changing the code base for Lubuntu from GTK to the newer code base QT. I think there are going to be more inconsistencies between older EOL Lubuntu distros and this newer code because of that compared to Xubuntu. Xfce is moving slower in development and the devs are busy fixing bugs and only porting to GTK3. I am not suggesting that Xubuntu is better or that anyone use it over Lubuntu. I am only using it for a comparison of two somewhat similar distros and how it might be more of a disadvantage right now for one to use an EOL release of Lubuntu over its' somewhat similar distro, Xubuntu.

I use Xubuntu but, wouldn't use it past the date of it coming EOL either.

I hope, I haven't made things less clear for you.

Addendum: Just in case you were thinking of using HWE and continually enabling it until 2019 which is the end of the 5 year cycle for Ubuntu 14.04 LTS. I think I was reading more into your question than was really there but, the information is still valid. 

If not pertinent info for you, well, just disregard this part.

---

### Post by poorguy on 2016-03-11
Hey mikodo,

I think this is how I wound up getting confused is with all of the info about the HWE.
It can be confusing. 

I also use xubuntu.
I really like the lighter distros as they run better and offer the same for a lot of my older hardware.

Yeah I'm good until 2017 and then I will try the upgrade or do a new install.

Thanks.

---

### Post by mikodo on 2016-03-11
Cool. And, the EOL of those distros are April 2017. FYI.

My days of distro hopping is over. Old guy too and, I need to try to concentrate my remaining firing and functioning neurons to administrating one desktop/OS.

Lubuntu is really interesting though. That newer code base of QT is the same as what KDE (like Kubuntu) is using. There are many possibilities for that. KDE has a large array of apps and libraries that are very good. Couple that with the newer ideas of the developers in LXQT, (newer Lubuntu), and it is worthy of watching as a side bar for me. The devs have some new and innovative ideas for a "light distro" that, I will at sometime be revisiting as it has this newer upside to its' development potential. I hope it can gains more traction as "they" say. Who knows. You could see me using it in the future.

Addendum again: I went off on a tangent about Lubuntu and couldn't remember what else I wanted to say about the "point" releases. I went out for a cigarette and remembered. Ya, I started again.

With my older computer when it came time to fresh install to the 14.04 release I, at that time just before the end of 12.04 support, (actually I may have run Xubuntu 12.04 a month or two past it's EOL by the time I got to fresh installing I think), I had the option to choose 14.04.0; 14.04.1; and 14.04.2. I chose 14.04.1 as a newer point release than 14.04.0  as it had a better chance of having more bugs fixed with it. I didn't go to 14.02.2 as I wanted the best chance for support for my older computer during the life cycle of 14.04. Had I chosen 14.04.2 then I would be updating the Kernel through the HWE Stack through the 14.04 cycle and with that comes a possible risk that, my older hardware support would be dropped in the newer Kernel for support for newer hardware. Older hardware support is dropped as time and effort is put into newer drivers etc for newer stuff. It probably wouldn't haven't mattered within that short time, (basically two years from last year when I installed 14.04.1 to April 2017 when I will have to fresh install again to the 16.04 release but, I didn't need to take the risk with my older computer and its' peripherals not being supported during those 2 years. I tried 14.04.1 in a live DVD and it worked so, I didn't see why I would need to "fix what ain't broke" with newer kernels in the same release period when I didn't have to.

I hope to have a new build done before having to install 16.04.1 that the newer kernel will hopefully have support for with my newer hardware. I expect though, that the old computer which I use now, will still be supported too as a second computer but, at sometime if it keeps working it, will eventually not be supported any more. That could be a long time still for this 2007 designed computer I hope.

Have a good day!

---

### Post by poorguy on 2016-03-11
Hey mikodo,

My goal is to do 2 things.

(1) is to see how an actual upgrade from an old distro to new distro works instead of only having read about them. 
Never doing such I can't say so I am looking forward to my own experience with that.

(2) is to be able to install a brand new release and using it all the way to another new release.
Another thing I haven't ever done as I have only been a Linux user for a little over a year.

No matter how it goes I will be able to have my own real live opinion based on real live experience.

---

### Post by howefield on 2016-03-11
Just for info, an interesting command to use is

```
ubuntu-support-status
```

eg, on this couple of days old xenial installation..

```
hugh@xenial-laptop:~$ ubuntu-support-status 
Support status summary of 'xenial-laptop':

You have 1814 packages (93.6%) supported until March 2021 (5y)
You have 42 packages (2.2%) supported until March 2019 (3y)
You have 38 packages (2.0%) supported until December 2016 (9m)

You have 19 packages (1.0%) that can not/no longer be downloaded
You have 24 packages (1.2%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
hugh@xenial-laptop:~$
```

using..

```
ubuntu-support-status --show-all > ~/Documents/Support
```

will run the command and create a file called Support in your Documents folder (easier for browsing the output than the terminal).

---

### Post by poorguy on 2016-03-12
Hey howefield,

Now that does look interesting and seems to be good info to know.
I will give that a try and see what I find.

Thanks.

---

### Post by poorguy on 2016-03-12
thomas@Dell-Precision-380:~$ ubuntu-support-status
Support status summary of 'Dell-Precision-380':

You have 166 packages (12.7%) supported until May 2017 (3y)
You have 1093 packages (83.4%) supported until May 2019 (5y)
You have 4 packages (0.3%) supported until December 2016 (9m)
You have 17 packages (1.3%) supported until February 2015 (9m)

You have 1 packages (0.1%) that can not/no-longer be downloaded
You have 29 packages (2.2%) that are unsupported

See this is what I don't understand.
Lubuntu 14.04 LTS is supported until April 2017.

Now this shows 1093 packages (83.4%) supported until May 2019 (5y)
Is this the amount of Ubuntu base packages that are in Lubuntu.

This is confusing.

---

### Post by sudodus on 2016-03-12
Thanks for a valuable command, howefield :-)

[SIZE=3]I tried 'ubuntu-support-status --show-unsupported' and get the following output:[/SIZE]

```
$ ubuntu-support-status --show-unsupported
Sammandrag av supportstatus för &#8221;xenial32&#8221;:

Du har 108 paket (4.3%) som stöds till december 2016 (9m)
Du har 1913 paket (76.9%) som stöds till mars 2021 (5y)
Du har 346 paket (13.9%) som stöds till mars 2019 (3y)

Du har 9 paket (0.4%) som inte (längre) kan hämtas
Du har 113 paket (4.5%) som inte stöds

Inte längre möjliga att hämta:
linux-headers-4.4.0-8 linux-headers-4.4.0-8-generic 
linux-headers-4.4.0-9 linux-headers-4.4.0-9-generic 
linux-image-4.4.0-9-generic linux-image-extra-4.4.0-9-generic lynx 
lynx-cur mplayer2 

Stöds inte: 
arp-scan ascii aspell-sv aview cabextract consolekit dos2unix elyxer 
extlinux filezilla filezilla-common flashplugin-installer 
fonts-horai-umefont fping gddrescue geany geany-common 
gir1.2-gtk-vnc-2.0 gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0 
gir1.2-spice-client-glib-2.0 gir1.2-spice-client-gtk-3.0 
gnome-dictionary gnome-sound-recorder gnuplot-data gnuplot-x11 gogo 
googleearth-package gstreamer0.10-gnomevfs gthumb gthumb-data hexchat 
hexchat-common hexchat-perl hexchat-plugins hexchat-python htop 
hwinfo iotop jhead libavcodec-extra libck-connector0 libfilezilla0 
libgdict-1.0-9 libgdict-common libglpk36 libgsoap8 libgtk-vnc-2.0-0 
libgvnc-1.0-0 libhd21 libjpeg-turbo-progs liboctave3 libopenblas-base 
libosinfo-1.0-0 libqrupdate1 libreoffice 
libreoffice-report-builder-bin libsndio6.0 libspice-client-glib-2.0-8 
libspice-client-gtk-3.0-4 libvirt-glib-1.0-0 libx86emu1 libxdo3 
links2 lubuntu-restricted-addons lubuntu-restricted-extras mbrola mc 
mc-data octave octave-common orpie p7zip pv python3-smbc qalc 
qalculate-gtk recoll s-nail spice-client-glib-usb-acl-helper 
ssh-askpass stellarium stellarium-data testdisk 
ttf-mscorefonts-installer udftools unetbootin unetbootin-translations 
unison unison-gtk unrar virt-manager virt-viewer virtinst virtualbox 
virtualbox-dkms virtualbox-ext-pack virtualbox-guest-additions-iso 
virtualbox-qt wajig wine wine-gecko2.21 wine-mono0.0.8 wine1.6 
wine1.6-i386 winetricks xdaliclock xdotool xournal xsane xsane-common 
xsel yad
```

[SIZE=3]1. 'Stöds inte' means 'Not supported'[/SIZE]

If I understand correctly, it means 'not supported by Canonical'. I think many of these program packages are well known and well supported, but there might be a few risky packages among them.

[SIZE=3]2. 'Inte längre möjliga att hämta' means 'No longer possible to download'[/SIZE]

We can also see, that lynx and mplayer2 are abandoned. I won't miss lynx too much, but I have really liked mplayer2. It has been good for my ageing hardware.

[SIZE=3]3. Bug #1556399: I tried to make the output English with the command[/SIZE]

```
LANG=C
```

but it did not work. I created the following bug report.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1556386](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1556386)

but also the following ***public*** bug report from a clean live system:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1556399](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1556399) 'LANG=C; ubuntu-support-status --show-unsupported fails from non-English language'. If you are a non English speaker, please check if you are affected by it too!

---

### Post by sudodus on 2016-03-12
> **poorguy said:**
> thomas@Dell-Precision-380:~$ ubuntu-support-status
Support status summary of 'Dell-Precision-380':

You have 166 packages (12.7%) supported until May 2017 (3y)
You have 1093 packages (83.4%) supported until May 2019 (5y)
You have 4 packages (0.3%) supported until December 2016 (9m)
You have 17 packages (1.3%) supported until February 2015 (9m)

You have 1 packages (0.1%) that can not/no-longer be downloaded
You have 29 packages (2.2%) that are unsupported

See this is what I don't understand.
Lubuntu 14.04 LTS is supported until April 2017.

Now this shows 1093 packages (83.4%) supported until May 2019 (5y)

So whats up with that.

The (Ubuntu) packages under the hood are supported until May 2019

---

### Post by vasa1 on 2016-03-12
@sudodus, could you please explain ```
lubuntu@lubuntu:~$ LANG=C
lubuntu@lubuntu:~$ ubuntu-support-status --show-unsupported
**Traceback (most recent call last)**:
  File "/usr/bin/ubuntu-support-status", line 145, in <module>
    print(_("Support status summary of '%s':") % os.uname()[1])
UnicodeEncodeError: 'ascii' codec can't encode character '\xf6' in position 29: ordinal not in range(128)
```What did you do to generate the "Traceback" in [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1556399?](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1556399?)

---

### Post by poorguy on 2016-03-12
Hey sudodus,

Thats kinda what I was thinking and the only thing that made any sense to me but had to find out for sure.

Thanks.

I couldn't get this to run it said command not found.
Run with --show-unsupported, --show-supported or --show-all to see more details

---

### Post by sudodus on 2016-03-12
I booted from the daily Lubuntu xenial-desktop-i386.iso and ran the live session in Swedish.

I ran 'LANG=C' and after that 'ubuntu-support-status --show-unsupported'.

Then the traceback was created automatically (by 'ubuntu-support-status')

---

### Post by sudodus on 2016-03-12
> **poorguy said:**
> Hey sudodus,

Thats kinda what I was thinking and the only thing that made any sense to me but had to find out for sure.

Thanks.

I couldn't get this to run it said command not found.
Run with --show-unsupported, --show-supported or --show-all to see more details

will this command run for you?

```
ubuntu-support-status --show-unsupported
```

---

### Post by poorguy on 2016-03-12
> **sudodus said:**
> will this command run for you?

```
ubuntu-support-status --show-unsupported
```

Yes.

Sure can make a difference when entered the right way.

Thanks.

---

