---
title: "10-2018 No-description 1.6Mb update?"
date: 2018-10-04
forum: Security
---

### Post by BlueAZ on 2018-10-04
I see this has happened in the past, but what is the update Software Updater is currently offering me?  There's no description or tech info, only that it's 1.6 Mb.  Should I trust it and install it?
Thanks.

---

### Post by westie457 on 2018-10-04
Usually updates can be trusted. If you want to be sure open a terminal and [sudo apt update
sudo apt upgrade[/code]
Unfortunately there will be no description or technical details shown in the terminal, however you do get to see what is available.

---

### Post by DuckHook on 2018-10-07
```
apt list --upgradable
```…will give you a short summary of what will be updated. If you are concerned about exactly what is being installed and want a chance to parse the details prior to allowing the update to proceed, then try installing:```
sudo apt install apt-listchanges
```This utility changes the way *apt* works so that it downloads the changelogs along with the updates, displays them, then pauses apt and asks you if you want to proceed. Note that it only works if you update using *apt* on the CLI. Use of the GUI Software Updater will bypass it. An example of its output on my latest update looks as follows:```
apt-listchanges: Changelogs
---------------------------

apparmor (2.12-4ubuntu5.1) bionic-security; urgency=medium

  * lp1788929+1794848.patch:
    - disallow writes to thumbnailer dir (LP: #1788929)
    - disallow access to the dirs of private files (LP: #1794848)

 -- Jamie Strandboge <jamie@ubuntu.com>  Thu, 27 Sep 2018 18:20:54 +0000

imagemagick (8:6.9.7.4+dfsg-16ubuntu6.4) bionic-security; urgency=medium

  * SECURITY UPDATE: code execution vulnerabilities in ghostscript as
    invoked by imagemagick
    - debian/patches/200-disable-ghostscript-formats.patch: disable
      ghostscript handled types by default in policy.xml
  * SECURITY UPDATE: information leak in ReadXBMImage
    - debian/patches/CVE-2018-16323.patch: don't leave data
      uninitialized with negative pixels
    - CVE-2018-16323
  * SECURITY UPDATE: uninitialized variable usage in ReadMATImageV4
    - debian/patches/CVE-2018-14551.patch: initialize variable
    - CVE-2018-14551
  * SECURITY UPDATE: memory leak of colormap in WriteMPCImage
    - debian/patches/CVE-2018-14434.patch: free colormap on bad
      color depth
    - CVE-2018-14434
  * SECURITY UPDATE: memory leak in DecodeImage
    - debian/patches/CVE-2018-14435.patch: free memory when given a
      bad plane
    - CVE-2018-14435
  * SECURITY UPDATE: memory leak in ReadMIFFImage
    - debian/patches/CVE-2018-14436.patch: free memory when given a
      bad depth
    - CVE-2018-14436
  * SECURITY UPDATE: memory leak in parse8BIM
    - debian/patches/CVE-2018-14437.patch: free strings in error
      conditions
    - CVE-2018-14437
  * SECURITY UPDATE: memory leak in ReadOneJNGImage
    - debian/patches/CVE-2018-16640.patch: free memory on error
    - CVE-2018-16640
  * SECURITY UPDATE: denial of service due to out-of-bounds write
    in InsertRow
    - debian/patches/CVE-2018-16642.patch: improve checking for errors
    - CVE-2018-16642
  * SECURITY UPDATE: denial of service due to missing fputc checks
    - debian/patches/CVE-2018-16643.patch: check fputc calls for error
    - CVE-2018-16643
  * SECURITY UPDATE: denial of service in ReadDCMImage and
    ReadPICTImage
    - debian/patches/CVE-2018-16644-prereq-1.patch: define
      ThrowPICTException() macro and use it
    - debian/patches/CVE-2018-16644-1.patch,
      debian/patches/CVE-2018-16644-2.patch: check for invalid length
    - CVE-2018-16644
  * SECURITY UPDATE: excessive memory allocation issue in ReadBMPImage
    - debian/patches/CVE-2018-16645.patch: ensure number_colors is
      not too large
    - CVE-2018-16645
  * SECURITY UPDATE: denial of service in ReadOneJNGImage
    - debian/patches/CVE-2018-16749.patch; check for NULL color_image
    - CVE-2018-16749
  * SECURITY UPDATE: memory leak in formatIPTCfromBuffer
    - debian/patches/CVE-2018-16750.patch: free memory on error
    - CVE-2018-16750

 -- Steve Beattie <sbeattie@ubuntu.com>  Fri, 28 Sep 2018 11:19:24 -0700

initramfs-tools (0.130ubuntu3.5) bionic; urgency=medium

  * debian/initramfs-tools.postinst: fix version comparison and
    so it will run for any version earlier than 0.130ubuntu3.5.

 -- Tiago Stürmer Daitx <tiago.daitx@ubuntu.com>  Thu, 27 Sep 2018 16:21:37 +0000

initramfs-tools (0.130ubuntu3.4) bionic; urgency=medium

  [ Colin Watson ]
  * [b4804dd] Only sync the filesystem containing the initramfs
    (Closes: #882380) (LP: #1667512)

  [ Tiago Stürmer Daitx ]
  * debian/initramfs-tools.postinst: remove orphaned old-dkms initrd files
    in /boot. (LP: #1791959)

 -- Tiago Stürmer Daitx <tiago.daitx@ubuntu.com>  Tue, 18 Sep 2018 09:18:47 +0000

(press q to quit)

```

---

### Post by BlueAZ on 2018-10-08
Thank you for the great tips!  Solved!!

---

### Post by DuckHook on 2018-10-08
You're welcome and Happy Ubuntu-ing.

---

