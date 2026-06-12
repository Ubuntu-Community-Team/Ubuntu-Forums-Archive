---
title: "Unable to install Ubuntu Server 18.04LTS alongside Windows 10."
date: 2019-05-11
forum: Server Platforms
---

### Post by charles75 on 2019-05-11
Hi,

I have Windows 10 installed and attempted to install Ubunutu Server 18.04 for dual boot.

My hard drive was partitioned as follows.
C: 200GB
Recovery partition 400MB which was located to the right of C:.

I shrunk the C: volume by 100GB, leaving 100GB of unused allocation.

I then inserted a USB stick loaded with Ubuntu Server.

During booting and after the first few steps I was presented with install Ubuntu Server and no option to try.

I chose to install and after a few more steps was asked to choose from available devices.

There was the whole hard drive for selection and an 'unused' section below.

However I could not choose this partition and the installer only gave me the option to install on the current drive which would overwrite Windows 10 partition.

There was no option to install Ubuntu Server alongside Windows 10.

The Bios is legacy and no UEFI support.

What am I doing wrong?

Thanks in advance for any help.

---

### Post by Rubi1200 on 2019-05-11
Hi,

To my knowledge the Server edition has no Install Alongside option, this is reserved for the Desktop edition.

However, you should have the option to manually partition and install using the Something Else option; was that not available?

It might help if you boot again and choose the Try option and then from a terminal post the output of this:

```
sudo fdisk -l
```

Thanks.

---

### Post by ajgreeny on 2019-05-11
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

