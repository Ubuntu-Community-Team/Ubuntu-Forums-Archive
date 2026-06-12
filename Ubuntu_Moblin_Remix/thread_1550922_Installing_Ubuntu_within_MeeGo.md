---
title: "Installing Ubuntu within MeeGo"
date: 2010-08-11
forum: Ubuntu Moblin Remix
---

### Post by Couto on 2010-08-11
I've got MeeGo installed and due to WiFi not working on my netbook, (even after following slaine's tutorial) I've decided I'm going to go back to Ubuntu.
My problem is: How to make my USB boot Ubuntu? Usually I'd use the program provided with Ubuntu or the Windows program they have on their site, but since I'm on MeeGo (and I know it's based off Fedora) there isn't really a program to use and since MeeGo doesn't use Fedora repository I can't use the Fedora LiveCD Creator.

Any tips?

Thanks.

---

### Post by Couto on 2010-08-17
Bump.

---

### Post by violetv on 2010-08-18
There is a program specially made for creating liveusb's from linux ISO files, its' called "unetbootin".
I've used it myself a few times within linux, and Windows, and it works like a charm.
You can go [here]("http://unetbootin.sourceforge.net/") to get it. 
You don't even need the iso on your hard drive, as it can download it for you too. 

I hope this helped you :D


.violet.

---

### Post by triwave on 2010-08-19
Agree with unetbootin suggestion ... my only tip is that if you have trouble booting after making a bootable USB you might want to try these things: 1) format the USB drive on a windows machine somewhere, and then install the files to it , or 2) use the plain FAT format instead of a fancier file system

I have mixed success with unetbootin but trying one or both of these usually improves my success rate...

---

### Post by spktkpkt on 2010-08-22
Download the Ubuntu-Netbook-Image and do:
```
sudo dd if=<PATH_TO_THE_IMAGEFILE> of=/dev/<USB_STICK> bs=1M
```After this, you should be able to boot the image from the stick. Attention: All data from the stick will be ereased!

---

