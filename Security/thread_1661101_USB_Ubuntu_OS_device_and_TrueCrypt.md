---
title: "USB Ubuntu OS device and TrueCrypt"
date: 2011-01-06
forum: Security
---

### Post by gb210461 on 2011-01-06
Hi All

My aim is to encrypt a USB device that has Ubuntu 10:10 installed onto it.

Normally I'd expect to encrypt the USB device first which seems quite straight forward. I'd then copy from a master USB device which has the installed OS on to the previously encrypted device. I'd expect to authenticate to the encrypted USB device as I was copying the files over.

The copy process that I'm currently using is: sudo dd if=/dev/sdc of=/dev/sdd where sdc is the master and sdd is the receiving device. The thing is that the dd command effectively reformats the drive as it copies bit by bit. The very fact that the USB device is encrypted has no effect as its operating at another level.

So the encryption I get but how do I then copy all the required Ubuntu OS files from the master to the receiving device whilst maintaining its boot function. 

Any ideas?

Regards, Gary

---

### Post by rookcifer on 2011-01-06
Truecrypt does not support whole disk encryption for Linux.  Therefore, you cannot boot an encrypted Linux drive (assuming the whole drive is encrypted).

---

### Post by dgw on 2011-01-07
You can use the alternate install CD to set up an encrypted install. It'll treat the flash drive like a regular hard drive that you can install Ubuntu onto. As the person above said, you can't use Truecrypt for full disk encryption with Ubuntu.

---

