---
title: "Encrypted directory on external hard drive."
date: 2010-04-09
forum: Security
---

### Post by darkshadow on 2010-04-09
I would like to make a single ecryptfs directory on a external hard drive to place a backup copy of my home directory. What would be the best way of going about this?

Some prerequisites:
1. Use ecryptfs so that if I try and access it on a different computer I don't need to install extra software. Also it is scalable and only uses the space needed and does not allocate extra.

2. When connected to my computer it should unlock from the keyring but on other computers allow me to mount it manually.

3. Be a basic directory when mounted so I can run rsync to keep it up to date. But not the whole partition since I need some unencrypted stuff on the drive and refuse to multi partition.

4. If possible have it easy to mount the directory but not automatically when the drive is mounted since I plan on making backups far less often then accessing the unencrypted files.

---

### Post by HermanAB on 2010-04-10
Here is another method:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

### Post by darkshadow on 2010-04-10
Unfortunately that method encrypts the whole partition which I don't want.

---

### Post by HermanAB on 2010-04-10
Make multiple partitions.

---

### Post by darkshadow on 2010-04-10
I can't because I don't want to try allocating the right space since I never do that right. But I think I figured it out anyway. I will create a "backup" user then as soon as I have the skeleton framework I will put the home directory on the drive and mount it using the unwrapped phrase when needed.

I would just copy my current .ecryptfs/$USER but it is to big do to some stuff I plan on using --exclude to bypass (a few hundred GB)

---

### Post by HermanAB on 2010-04-10
I have a collection of memory sticks.  One smaller 4GB device is plaintext VFAT, one 16GB device is plaintext NTFS and the others are encrypted LUKS NTFS.  All my USB hard disks are completely encrypted with LUKS. 

When I have to exchange sensitive data on plaintext devices, I use Zip with a password - better than nothing and cross platform - it works on Linux, Windows and Mac.

That seems to do it for me in terms of keeping my critical data safe, while still being able to exchange data with other machines that are not configured with encryption.

---

### Post by darkshadow on 2010-04-10
That sounds like a good setup for some people but I work with bigger files and from experience I know that I hate when I partition up a drive then end up with lets say about 75GB free on each partition (total of 150GB) and need to make a 120GB file (Yes I do that and bigger) suddenly because I chose wrong I have to split the file up which causes problems if it was a dd image of a partition that I need to be able to mount as a loop back device.

---

### Post by Sporkman on 2010-04-13
Re encrypting single files, look into ccrypt - it's a quick & easy (and strong) command-line file encrypter. It can also recursively encrypt files in subdirectories, or you can just zip up a directory & encrypt the zip file.

---

