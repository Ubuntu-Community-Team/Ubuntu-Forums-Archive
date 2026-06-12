---
title: "Creating Ubuntu Gutsy chroot on Mint 17.1 fails to download Packages.bz2"
date: 2015-11-11
forum: Virtualisation
---

### Post by ndixit26 on 2015-11-11
I am trying to create a chroot to Ubuntu 7.10 on host running Linux Mint 17.1 64-bit. For that, I first created an entry in /etc/chroot/chroot.conf
```

[gutsy]
description=Ubuntu Gutsy
location=/genera
priority=3
users=naman
groups=sbuild
root-groups=root

```
and then entered the command:
```

sudo debootstrap --variant=buildd gutsy /genera http://old-releases.ubuntu.com/ubuntu

```
However, this is the output I get:
```

I: Retrieving Release 
I: Retrieving Release.gpg 
I: Checking Release signature
I: Valid Release signature (key id 630239CC130E1A7FD81A27B140976EAF437D05B5)
I: Retrieving Packages 
I: Validating Packages 
W: Retrying failed download of http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.bz2
I: Retrieving Packages 
I: Validating Packages 
W: Retrying failed download of http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.bz2
I: Retrieving Packages 

```
and so on. I visited [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/) by my browser and sure enough, the file Packages.bz2 is there. My internet connection is working too.

The file gets downloaded by the name of debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2 in /genera/var/lib/apt/lists/partial/ and as soon as the download is finished, it gives that "Retrying failed download..." message and start downloading it all over again.


Do I need to enter a different mirror? Or is something else wrong?

---

### Post by matt_symes on 2015-11-11
Hi

I just been trying to replicate your problem with 100% success :D

I also cannot create a debootstrap of Gusty however i can from Hardy.

Looking at Packages.bz2 file for Gusty, it seems to be corrupted.

Try downloading it with wget and then unzipping with

```
bzip2 -d <file_name>
```

Here's what i get.

From the debootstrap logs.
```

--2015-11-11 21:33:47--  http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.bz2
Resolving old-releases.ubuntu.com (old-releases.ubuntu.com)... 91.189.88.17
Connecting to old-releases.ubuntu.com (old-releases.ubuntu.com)|91.189.88.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1070422 (1.0M) [application/x-bzip2]
Saving to: '/gusty/var/lib/apt/lists/partial/debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2'
```

and the file it downloaded.

```

matthew-laptop:/gusty/var/lib/apt/lists/partial:1 % ls                                                                     
debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2
matthew-laptop:/gusty/var/lib/apt/lists/partial:1 % file debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2    
debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2: bzip2 compressed data, block size = 900k
matthew-laptop:/gusty/var/lib/apt/lists/partial:1 % sudo bzip2 -d debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: No such file or directory
        Input file = debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2, output file = debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

bzip2: Deleting output file debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages, if it exists.
matthew-laptop:/gusty/var/lib/apt/lists/partial:1 % 
```

I haven't tried an earlier version than Gusty; only Hardy. 

It may be worth trying to see if an earlier version than Gusty also fails such as Feisty. If that also fails, it may suggest file compression or some such. I disabled gpg and certificate checking in my test on Gusty so it's not that.

**EDIT:**

Forgot to post this.

```
matthew-laptop:/gusty/var/lib/apt/lists/partial:1 % bzip2 -tvv debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2
  debootstrap.invalid_dists_gutsy_main_binary-amd64_Packages.bz2: 
    [1: huff+mtf rt+rld]
    [2: huff+mtf rt+rld]
    [3: huff+mtf rt+rld]
    [4: huff+mtf rt+rld]
    [5: huff+mtf rt+rld]
    [6: huff+mtf rt+rld]
    [7: huff+mtf file ends unexpectedly

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

matthew-laptop:/gusty/var/lib/apt/lists/partial:1 % 
```


Kind regards

---

### Post by ndixit26 on 2015-11-11
Thanks. (And why didn't I think of that?!).

Do you know of some alternate mirror of old-releases.ubuntu.com? I have been unable to find one; although seems to me that in this age, there should be at least a few.

---

### Post by matt_symes on 2015-11-11
Hi

> **ndixit26 said:**
> Do you know of some alternate mirror of old-releases.ubuntu.com? I have been unable to find one; although seems to me that in this age, there should be at least a few.

The only one i know of is old-releases.ubuntu.com. Maybe you could fire off an e-mail to a mailing list or ask in an IRC channel.

Kind regards

---

