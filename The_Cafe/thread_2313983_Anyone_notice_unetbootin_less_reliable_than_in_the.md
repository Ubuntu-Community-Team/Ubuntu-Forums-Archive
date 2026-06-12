---
title: "Anyone notice unetbootin less reliable than in the past?"
date: 2016-02-17
forum: The Cafe
---

### Post by furtom on 2016-02-17
I've always used unetbootin with success, that is until about the last 6 months or so.

It's nothing specific, but I've just noticed a lot more failures with Ubuntu. This is across old and new USB sticks and all different computers (all of which are good-old bios machines).

Last week, I couldn't get an HP Pavilion to boot with an unetbootin created drive (I then tried Ubuntu start up disk, which also didn't work).  Getting the OS not found error. I even bought a new stick just to make sure.

I wound up using dd, which worked like a charm on the first try.

Anyway, this isn't a call for help. Just a curiosity. Has anyone else noticed this? I'm wondering if recent versions of Ubuntu work less well with unetbootin for some reason.

---

### Post by sammiev on 2016-02-17
Same here. 

Using dd always work but dangerous to recommend to some.

[MKusb]("https://help.ubuntu.com/community/mkusb") has been great and great to recommend to new comers.

---

### Post by montag dp on 2016-02-17
I use Manjaro and mentioned Unetbootin on their forums.  Someone told me that it's not recommended, and I should use dd instead.  I guess because Unetbootin copies the files to the drive one-by-one instead of writing the whole ISO directly, so it is more prone to failures.

That said, the last time I used Unetbootin, I did have an issue where I needed to copy some additional files onto the USB drive before it would boot.  The files were menu.c32, libcom32.c32, libutil.c32, and vesamenu.c32 from /usr/lib/syslinux/bios.

---

### Post by sudodus on 2016-02-17
The version of ***Unetbootin*** in the Ubuntu repos is old. I would recommend that you get it from the developer's PPA. I think the PPA version works with the newest versions of Ubuntu (but I haven't tested a lot).

```
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin
```

***mkusb*** wraps security around dd to create live-only USB drives from all iso-hybrid linux iso files. It can also create persistent live drives with a casper-rw or persistence partition (from iso files based on Ubuntu and Debian Jessie). I try to keep it up to date including the developing version (now Ubuntu Xenial Xerus).

The Ubuntu ***Startup Disk Creator*** alias usb-creator-gtk and usb-creator-kde has had serious problems for several years, some say it has not worked well after Ubuntu 10.10. But a new version, 0.3.2, is developed and available in Xenial Xerus. It clones the iso file similar to dd and mkusb. I have tested it and I think this new version is very reliable. But the ability to create persistent live drives is dropped.

---

### Post by night_sky2 on 2016-02-17
I personally haven't experienced any problem with Unetbootin and the 14.04x LTS branch of Ubuntu.

The thing is that you need to format properly before creating a bootable USB flash drive. I use the ***Disks ***app for this purpose (available in the Software Center).

---

### Post by furtom on 2016-02-17
> **sammiev said:**
> Same here. 

Using dd always work but dangerous to recommend to some.

[MKusb]("https://help.ubuntu.com/community/mkusb") has been great and great to recommend to new comers.

Tell me about it. I **TRIPPLE CHECK** that one little letter... ;)

> **montag dp said:**
> I use Manjaro and mentioned Unetbootin on their forums.  Someone told me that it's not recommended, and I should use dd instead.  I guess because Unetbootin copies the files to the drive one-by-one instead of writing the whole ISO directly, so it is more prone to failures.

That said, the last time I used Unetbootin, I did have an issue where I needed to copy some additional files onto the USB drive before it would boot.  The files were menu.c32, libcom32.c32, libutil.c32, and vesamenu.c32 from /usr/lib/syslinux/bios.

> **sudodus said:**
> The version of ***Unetbootin*** in the Ubuntu repos is old. I would recommend that you get it from the developer's PPA. I think the PPA version works with the newest versions of Ubuntu (but I haven't tested a lot).

```
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin
```

Oh, I forgot to mention, I tried that. Not this last time, but a few weeks ago. It didn't help.

> ***mkusb*** wraps security around dd to create live-only USB drives from all iso-hybrid linux iso files. It can also create persistent live drives with a casper-rw or persistence partition (from iso files based on Ubuntu and Debian Jessie). I try to keep it up to date including the developing version (now Ubuntu Xenial Xerus).

The Ubuntu ***Startup Disk Creator*** alias usb-creator-gtk and usb-creator-kde has had serious problems for several years, some say it has not worked well after Ubuntu 10.10. But a new version, 0.3.2, is developed and available in Xenial Xerus. It clones the iso file similar to dd and mkusb. I have tested it and I think this new version is very reliable. But the ability to create persistent live drives is dropped.

I can't understand why it would ship if it doesn't work. Unetbootin has no obligation to make sure their software works with any particular distro. Canonical does, however.

I was thinking about mkusb, but I figured I might as well just use dd.

> **night_sky2 said:**
> I personally haven't experienced any problem with Unetbootin and the 14.04x LTS branch of Ubuntu.

The thing is that you need to format properly before creating a bootable USB flash drive. I use the ***Disk Utility *** app for this purpose (available in the Software Center).

I think the problems really started with 15.04. I always format before writing.

Thanks guys. Good to know I'm not just crazy. :p

---

### Post by Geoffrey_Arndt on 2016-02-17
Big time problems with Unetbootin and the related program from Ubuntu (Startup Disk Creator).   I first noticed it in 15.10 but it could have started before that.   The creation program/process seems to run as normal, no errors, but then just won't boot up from any PC.   But the same iso created in 14.04 has a 50/50 chance to boot "from 15.10" . . . . frustrating.    Might have to fire up my Windows partitions to install Pendrive Linux (I think that's the name of the program).   Don't know if issue more related to unetbootin code, or something in 15.10.

By the way, I also tried the latest unetbootin (from PPA mentioned above) . . . it made no difference - - still totally unreliable for creating a bootable usb-flash-stick.

---

### Post by Geoffrey_Arndt on 2016-02-18
Just saw a tutorial from Matthew Moore on "Disk Dump" (dd) for creating Live media . . . . looks good, I'll be using that in future until unetbootin issue(s) sorted out.

[https://www.youtube.com/watch?v=74A6pVrv0CA](https://www.youtube.com/watch?v=74A6pVrv0CA)

---

### Post by sudodus on 2016-02-18
> **furtom said:**
> Tell me about it. I **TRIPPLE CHECK** that one little letter... ;)
...
I was thinking about mkusb, but I figured I might as well just use dd.


If you are comfortable with a command line script, you can use [mkusb-nox](https://help.ubuntu.com/community/mkusb/v7) (No X). It is simpler and faster than mkusb, and it provides the same level of security. mkusb-nox helps with the 'triple checking' for you and reduces the risk of wiping the family pictures ;-)

---

### Post by user1397 on 2016-02-18
I've had problems with unetbootin in the past, but it's worked for me for the most part.  I usually use dd or whatever software the particular distro recommends (such as PenDrive Linux's Universal USB Installer as recommended on this page [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) )

---

### Post by mastablasta on 2016-02-18
I used it on windows and noticed unreliability also. now I am using Yumi or LinuxLiveUSB or single install (windows only)

---

### Post by furtom on 2016-02-18
> **sudodus said:**
> If you are comfortable with a command line script, you can use [mkusb-nox](https://help.ubuntu.com/community/mkusb/v7) (No X). It is simpler and faster than mkusb, and it provides the same level of security. mkusb-nox helps with the 'triple checking' for you and reduces the risk of wiping the family pictures ;-)

Very interesting! I was unaware of this. Thank you!

---

### Post by buzzingrobot on 2016-02-19
Linux Mint ships two little GUI apps -- USB drive formatter and USB driver writer -- that are nice. They're in Mint's repo if you want to go get them and have worked with no issues for me on the 14.04 releases. They install cleanly with no dependencies here. 

I typically use dd and yes, you need to point it at the correct device.  Run "lsblk" just before you use it to get a list of current devices.The designations for attached devices are not permanent and may change, especially if one or more are unattached while other(s) remain attached. *Always* check.

Always use 'sync' after dd to be sure the memory buffers are flushed and actually written to the USB stick.

---

### Post by furtom on 2016-02-19
> **buzzingrobot said:**
> Always use 'sync' after dd to be sure the memory buffers are flushed and actually written to the USB stick.

Yeah, I've heard that before, but I never did it. There must be something to it, but I can't understand why dd needs an extra push to do the job...

Also, I think if you unmount the USB, it will do the same thing.

---

### Post by sudodus on 2016-02-19
Yes, the unmount command calls sync before it performs the unmounting, but dd should be used without anything mounted on the target device, so I recommend using sync after cloning with dd (as recommended by *buzzingrobot*), and I have built it into mkusb and mkusb-nox.

---

### Post by furtom on 2016-02-19
> **sudodus said:**
> Yes, the unmount command calls sync before it performs the unmounting, but dd should be used without anything mounted on the target device, so I recommend using sync after cloning with dd (as recommended by *buzzingrobot*), and I have built it into mkusb and mkusb-nox.

I'm definitely going to try mkusb-nox next time!

Thank you.

---

### Post by poorguy on 2016-02-27
That why I always create a DVD can't argue with reliability.

---

### Post by sudodus on 2016-02-27
> **poorguy said:**
> That why I always create a DVD can't argue with reliability.

If you *clone* the iso file to a USB drive, it will be at least as reliable as a DVD. Tough guys do it with *dd*, nicknamed 'disk destroyer'. Other people use *mkusb*, *Disks* or the new version of *Startup Disk Creator* in Xenial Xerus.

---

### Post by poorguy on 2016-02-29
Thanks sudodus, 

I am always learning something new from the forum.

---

### Post by Delvien on 2016-03-05
I know that unetbootin doesnt work well with recent ubuntu releases, and some arch/manjaro isos. General rule of thumb is that you should use dd if in linux, rufus and sometimes yumi if you are in windows.

---

### Post by vasa1 on 2016-03-05
> **sammiev said:**
> ...
[MKusb]("https://help.ubuntu.com/community/mkusb") has been great and great to recommend to new comers.
Used mksub for the first time. Seems much quicker than unetbootin and no having to mess with missing files.

```
$ apt-cache policy mkusb
mkusb:
  Installed: 10.5.1-1ubuntu1
  Candidate: 10.5.1-1ubuntu1
  Version table:
 *** 10.5.1-1ubuntu1 0
        500 http://ppa.launchpad.net/mkusb/ppa/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
$ 
```

---

### Post by kurt18947 on 2016-03-05
> **sudodus said:**
> If you *clone* the iso file to a USB drive, it will be at least as reliable as a DVD. 
.................


Possibly not on older machines. I have a desktop machine from around 2008-2009 that is fussy about booting from live USB. No problem with DVD. The same is true installing O.S.s in Virtualbox. There is a way to install in VirtualBox using live USBs but it's more involved AFAIK. USB flash drives are certainly quicker and less fragile but optical disks still have a place.

---

### Post by HermanAB on 2016-03-07
Uhmmm... You can install in Virtualbox, using the downloaded ISO file directly.

---

### Post by poorguy on 2016-03-08
I just used unetbootin 585 version from ubuntu repository to install ubuntu mate and it worked like a champ unlike the newer 613 version.

Figured I would pass this along.
Seems older is still better for this install.

---

### Post by kurt18947 on 2016-03-12
> **HermanAB said:**
> Uhmmm... You can install in Virtualbox, using the downloaded ISO file directly.

You can? I'll have to research this. The instructions I'd found involved creating some sort of virtual drive and installing from that.

---

### Post by him610 on 2016-03-17
Unetbootin always was problematic for my puposes in the past until LTS 14xx. I used to always use the dd utility. Recently, I came across a reference to mkusb developed by Sudodus of Ubuntu Forums which I researched and downloaded for future use. By the way, Sudodus has done an excellent job on the man pages and downloadable User Guide which could serve as models on how to write man pages and user guides.

---

### Post by HermanAB on 2016-03-17
Basically, unetbootin is obsolete and mksusb just wraps dd into something less likely to destroy a newby's disk.

For the last few years, the Ubuntu ISO files are bootable, same as ISO files from Fedora, Suse and Slack, but there is so much obsolete old information on the intertubes, that pretty much nobody seems to know this and google searches keep regurgitating the old cruft.

---

