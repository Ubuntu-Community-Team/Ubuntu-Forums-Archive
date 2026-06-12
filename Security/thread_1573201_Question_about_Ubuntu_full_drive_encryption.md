---
title: "Question about Ubuntu full drive encryption"
date: 2010-09-12
forum: Security
---

### Post by Gitanes on 2010-09-12
When I encrypt my entire Ubuntu installation, is the free space also encrypted or just the OS files and, naturally, files created whilst the OS is mounted under the encryption scheme?  I'm asking because I'm wondering if I need to do a free space wipe on my empty partitions prior to installing Ubuntu with system encryption.  If the free space is also encrypted; then I won't bother.  Thanks.

---

### Post by bodhi.zazen on 2010-09-12
> **Gitanes said:**
> When I encrypt my entire Ubuntu installation, is the free space also encrypted or just the OS files and, naturally, files created whilst the OS is mounted under the encryption scheme?  I'm asking because I'm wondering if I need to do a free space wipe on my empty partitions prior to installing Ubuntu with system encryption.  If the free space is also encrypted; then I won't bother.  Thanks.

The free space on the partition you encrypt is formatted and encrypted as a part of the install. Other space is not.

If in doubt, you can zero the drive with dd, but more likely then not you do not need to do that.

---

### Post by DZ* on 2010-09-13
> **Gitanes said:**
> When I encrypt my entire Ubuntu installation, is the free space also encrypted or just the OS files and, naturally, files created whilst the OS is mounted under the encryption scheme?  I'm asking because I'm wondering if I need to do a free space wipe on my empty partitions prior to installing Ubuntu with system encryption.  If the free space is also encrypted; then I won't bother.  Thanks.

The free space in not encrypted. Full disk encryption is supported through LUKS. I have a stick encrypted with LUKS which previously had an Ubuntu install ISO on it. Let's plug it in without mounting and see if the ISO contained the package "firefox"

sudo dd if=/dev/sdb | strings | grep firefox

```
[...]
Package: firefox
Source: firefox-3.5
Depends: firefox-3.5, firefox-3.5-branding
Filename: pool/main/f/firefox-3.5/firefox_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb
 This is a meta package that will point to the latest firefox package in ubuntu.

```

Some people recommend filling the disk with random data prior to encryption so that free space cannot be distinguished from encrypted data, but the wrench exploit ([http://xkcd.com/538/](http://xkcd.com/538/)) probably applies :-)

---

### Post by rookcifer on 2010-09-13
> **Gitanes said:**
> When I encrypt my entire Ubuntu installation, is the free space also encrypted or just the OS files and, naturally, files created whilst the OS is mounted under the encryption scheme?  

As others said, free space is not encrypted, which is why it is imperative to overwrite the drive with random data before encrypting.  This way it is impossible to distinguish encrypted data from random data since they all appear random.

> but the wrench exploit ([http://xkcd.com/538/](http://xkcd.com/538/)) probably applies

Aka [rubber-hose cryptanalysis.]("http://en.wikipedia.org/wiki/Rubber-hose_cryptanalysis")

---

### Post by Gitanes on 2010-09-13
> **rookcifer said:**
> As others said, free space is not encrypted, which is why it is imperative to overwrite the drive with random data before encrypting.  This way it is impossible to distinguish encrypted data from random data since they all appear random.



Aka [rubber-hose cryptanalysis.]("http://en.wikipedia.org/wiki/Rubber-hose_cryptanalysis")

Thank you both for confirming that for me.  I had a suspicion that might be the case.  I've noticed that most of the sites that give instructions for installing linux encryption mention wiping the drive before installing.  I've also noticed that luks encryption seems to go rather faced when compared to installing Truecrypt under windows.  I'm fairly certain that TC encrypts the free space as well as the files already on the computer.

Is there any file wiping that will work on Ext4 file system?  One could wipe the free space after encrypting ubuntu but everything I've read is that wiping doesn't work with Ext3/4.

---

