---
title: "Can't boot Beta version"
date: 2016-09-22
forum: Ubuntu Development Version
---

### Post by simonsaysthis on 2016-09-22
Hi all

I really don't know what I am doing wrong. I downloaded an image file to test the Beta twice but everytime I try to boot from USB I get a black screen. I tried various tools write the image but the problem is consistent. Is there a different process of installing the beta? I have no problem with other Linux iso's

---

### Post by VMC on 2016-09-22
How did you install it on the USB device? What method?

---

### Post by simonsaysthis on 2016-09-23
> **VMC said:**
> How did you install it on the USB device? What method?

Really a bit baffled

- donwloaded ISO twice (different daily builds)
- burnt onto USB trying Gnome Image wirter, Opensuse Image Writer and the Fedora media writer
- trying to do all this on Fedora 24

---

### Post by VMC on 2016-09-23
You don't have to keep downloading iso, if you check md5sum.

Is the usb a flash dive of hard drive? If flash drive you could use the [isohybrid]("https://www.turnkeylinux.org/blog/iso2usb") method or use [unetbootin]("https://sourceforge.net/projects/unetbootin/").

---

### Post by fthx on 2016-09-23
? :

linux (4.8.0-15.16) yakkety; urgency=low

  [ Tim Gardner ]

  * Release Tracking Bug
    - LP: [#1626239]("https://launchpad.net/bugs/1626239")

  * image won't boot after upgrading to yakkety's 4.8 kernel because efi
    (LP: [#1626158]("https://launchpad.net/bugs/1626158"))
    - [Config] CONFIG_FAT_DEFAULT_IOCHARSET=iso8859-1
    - [Config] CONFIG_NLS_CODEPAGE_437=y
    - [Config] CONFIG_VFAT_FS=y

  * Miscellaneous Ubuntu changes
    - SAUCE: seccomp: log actions even when audit is disabled

 -- Tim Gardner <email address hidden>  Wed, 21 Sep 2016 06:41:03 -0600

---

### Post by simonsaysthis on 2016-09-23
> **fthx said:**
> ? :

linux (4.8.0-15.16) yakkety; urgency=low

  [ Tim Gardner ]

  * Release Tracking Bug
    - LP: [#1626239]("https://launchpad.net/bugs/1626239")

  * image won't boot after upgrading to yakkety's 4.8 kernel because efi
    (LP: [#1626158]("https://launchpad.net/bugs/1626158"))
    - [Config] CONFIG_FAT_DEFAULT_IOCHARSET=iso8859-1
    - [Config] CONFIG_NLS_CODEPAGE_437=y
    - [Config] CONFIG_VFAT_FS=y

  * Miscellaneous Ubuntu changes
    - SAUCE: seccomp: log actions even when audit is disabled

 -- Tim Gardner <email address hidden>  Wed, 21 Sep 2016 06:41:03 -0600

Sorry, just trying to understand. Does this essentially mean it's a known bug that the image doesn't boot? What is one to do in this case?

---

### Post by fthx on 2016-09-23
It means that this bug *could* be related.
Simply download the daily ISO, this new kernel *-15.16 is now in main repos but AFAIK not in the beta.

---

### Post by simonsaysthis on 2016-09-24
So I the issue is indeed that the current daily build does not boot via USB on a Lenovo Thinkpad in UEFI Bios mode. I managed to install it using Legacy mode but later on reinstalled 16.04 as I need my OS as UEFI installation. Looking forward to see when this is fixed. Otherwise the daily build has been running very well from a lay person's perspective.

---

