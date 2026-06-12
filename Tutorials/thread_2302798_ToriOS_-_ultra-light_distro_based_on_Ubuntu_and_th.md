---
title: "ToriOS - ultra-light distro based on Ubuntu and the window manager JWM"
date: 2015-11-13
forum: Tutorials
---

### Post by sudodus on 2015-11-13
[SIZE=4]ToriOS - ultra-light, based on Debian Jessie, Ubuntu 12.04 LTS, [COLOR="#696969"]Ubuntu 14.04 LTS[/COLOR] and JWM[/SIZE]

If you want to try a new ultra-light distro, try ToriOS, based on Debian Jessie and Ubuntu 12.04 LTS and the window manager JWM. It uses only ~ 90 MB RAM or less, when running idle after booting (the RAM usage varies depending on the computer hardware). See [this comparison](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage), where Lubuntu Trusty used 123 MB. If you want to run ToriOS in old hardware with a weak processor and low amount of RAM, you need ultra-light application programs too. In a bit more powerful computer and with more RAM, it will be very fast, and you can use the standard linux application programs.

Notice that ToriOS is not yet released. It is still developed, so although it is quite debugged and polished by now, the daily iso file is still developed and there can be hiccups. The installed system is more stable than the live system with the installer. This is why there are alternatives that use alternative install methods.

It is straight-forward to *do-release-upgrade* from Ubuntu Precise alias 12.04 LTS  to Trusty alias 14.04 LTS. A future version of ToriOS may be based on Ubuntu Trusty and an installed system is available now for public testing. This Trusty version is tested less than the other two versions, and it uses too much RAM (a known bug). If you find a bug, please report it (here) :-)


1. Download or zsync a ***ToriOS daily iso file*** (to run ToriOS *live* or *install* ToriOS to an entire drive or alongside previous operating system(s)). This iso file can be installed like other iso files to a CD/DVD disk or USB pendrive, and in the next step ToriOS can be installed into an internal drive or USB drive or eSATA drive. The Debian Jessie iso file is closest to be released (in May 2016). See the first attached *screenshot*. There is also a Precise iso file. Both iso files have non-pae kernels and fit within a CD disk, so they can be used in very old computers. See the following link,

[http://phillw.net/isos/torios/](http://phillw.net/isos/torios/)


2. Download a ***ToriOS OEM tarball*** and the One Button Installer (to *install ToriOS* to an entire drive or alongside previous operating system(s)) The One Button Installer can be installed into a USB pendrive, and the ToriOS tarball can be installed into an internal drive or USB drive or eSATA drive.

[ToriOS gamma tarball](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13385379#post13385379)

[One Button Installer](https://help.ubuntu.com/community/OBI)

The most recent tarballs (made in May 2016) have the following md5sums:
```
ead0f0ad1ecdd12d6ede036eae7f40f5  ToriOS-pae-OEM_prec_use-by-OBI-in-trusty-2016-may.tar.xz  # ToriOS Precise
8dbd99f28cce8d685f7b129641f63ff0  ToriOS-pae-OEM_trus_use-by-OBI-in-trusty-2016-may.tar.xz  # ToriOS Trusty
77efef5266118c784ce0c9f5ec6db3ad  ToriOS-mini_trusty_use-by-OBI-in-trusty-2016-may.tar.xz   # ToriOS Trusty
```


3. Download a ***ToriOS OEM compressed image file*** and install mkusb (to *install ToriOS* to an *entire drive*). mkusb can be installed into an existing linux operating system and the ToriOS compressed image file can be installed into an internal drive or USB drive or eSATA drive. See the following link,

[http://phillw.net/isos/linux-tools/compressed-images/](http://phillw.net/isos/linux-tools/compressed-images/)

```
$ md5sum dd_ToriOS-LubuCore-pae-OEM_precise-nov_7.8GB.img.xz
103d8a3292938fbd211c96916dcca74a  dd_ToriOS-LubuCore-pae-OEM_precise-nov_7.8GB.img.xz
```

The most recent compressed image files (made in May 2016) have the following md5sums:
```
4cadf2e0b6b5ca75cf7d9d20331d2220  dd_ToriOS-LubuCore-pae-OEM_precise-2016-may_7.8GB.img.xz  # ToriOS precise
80baf2342b09ff5554e300d049bb8d78  dd_ToriOS-LubuCore-pae-OEM_trusty-2016-may_7.8GB.img.xz   # ToriOS Trusty
```

Install mkusb via the PPA with the following commands: If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu
```

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

Read more about mkusb at [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

This installation is very simple, the compressed image is extracted and cloned, so ToriOS will be installed to the entire drive (minimum 8 GB). You can expand the partitions afterwards to use the whole drive if you wish, see [GrowIt.pdf](http://phillw.net/isos/linux-tools/9w/GrowIt.pdf), or you can install another operating system afterwards into the unallocated drive space (and create a dual boot or multi boot system).

-o-

From Windows you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) to install

- the ToriOS iso file. (Use Win32 Disk Imager directly and install to a USB pendrive.)

- the ToriOS compressed image. (Extract the compressed iso with a standard Windows tool (for example 7-zip or Winzip), and after that you can use Win32 Disk Imager.)

-o-

Log in to the OEM versions with

[B]user: oem
password: 123456[/B]

and when you are ready click on the desktop icon ***Prepare for shipping to end user***. See the second and third attached *screenshots*.

Log in to the Trusty mini version with

[B]user: guru
password: changeme[/B]

---

### Post by sudodus on 2016-05-02
A version of ToriOS based on Debian Jessie is getting close to be released (in May 2016). Although quite debugged and polished by now, the daily iso file is still developed and there can be hiccups. *The installed system is more stable than the live system with the installer.* This is why there are alternatives that use other install methods.

It is straight-forward to *do-release-upgrade* from Ubuntu *Precise* alias 12.04 LTS  to *Trusty* alias 14.04 LTS. A future version of ToriOS may be based on Ubuntu Trusty and an installed system is available now for public testing. The Trusty version of ToriOS seems to work rather well, but it uses more RAM than the other versions. It is a known issue. The Trusty version is tested less than the other two versions. If you find a bug, please report it (here).

New ToriOS versions, based on Ubuntu Precise and Trusty were made up to date 2016-05-02, 2016-05-05 and uploaded. ***Post #1 is updated*** with a detailed description of the new versions.

---

### Post by sudodus on 2016-05-06
***Another ToriOS Trusty tarball***

This ToriOS Trusty version built from the system in **Trusty-mini-txt7.tar.xz**, using the following commands and some tweaks,

[QUOTE=ToriOS developer Israel Dahl]Do your mini then run
```
wget https://raw.githubusercontent.com/Israel-/torios-from-mini/master/torios-trusty-x86.bash
chmod +x torios-trusty-x86.bash
./torios-trusty-x86.bash
```
[/QUOTE]

The script is old and originally made for Precise. I had to install the package torios-live and then overwrite it with the package torios-desktop and clean it up, but then it works well. The RAM needed should be reduced, and probably there are some bugs to squash before it is ready to be released.

```
$ md5sum ToriOS-mini_trusty_use-by-OBI-in-trusty-2016-may.tar.xz
77efef5266118c784ce0c9f5ec6db3ad  ToriOS-mini_trusty_use-by-OBI-in-trusty-2016-may.tar.xz
```

The version based on Debian Jessie is still most likely to be the first ToriOS version to be released.

[hr][/hr]
You can download these tarballs from within the original One Button Installer or directly from this link [phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs)

user: **guru**
password: **changeme**

---

### Post by sudodus on 2016-09-09
[SIZE=4]ToriOS 1.0 has been released[/SIZE]

This released version, ToriOS 1.0, is built on Debian Jessie, uses the JWM window manager, the pcmanfm file browser and the OBI-installer :-)

The OBI-installer was developed from the [One Button Installer](https://help.ubuntu.com/community/OBI), that is used to install the test versions described in the previous posts in this thread. The installers are different in several ways, and the tarballs are customized to each installer. You cannot expect a tarball for one version of the installer to work for the other one.

You are welcome to start using ToriOS. See the following links at the official ToriOS website:

[http://torios.top](http://torios.top)

[http://torios.top/torios-1-0-has-been-released/](http://torios.top/torios-1-0-has-been-released/)

**[http://torios.top/download/](http://torios.top/download/)**

[http://torios.top/documentation/](http://torios.top/documentation/)

---

