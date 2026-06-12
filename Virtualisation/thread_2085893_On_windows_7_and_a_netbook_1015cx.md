---
title: "On windows 7 and a netbook 1015cx"
date: 2012-11-19
forum: Virtualisation
---

### Post by helen2 on 2012-11-19
I have an asus 1015cx (2 gb ddr3) and widnows 7 (i have a loader i like free software as linux :) ) and i ws planing to installa wubi but my question is...
Do u know if having the loader with wondows 7 i will get some problems with it if i instlla ubuntu useing wubi?
Thank's
Helen

---

### Post by Cheesemill on 2012-11-19
What's a loader?

---

### Post by helen2 on 2012-11-19
> **Cheesemill said:**
> What's a loader?
 humm...dont know if i can explain me bettar on this forum...is "something" taht keeps genuine windows 7
Take care
Helen

---

### Post by mlentink on 2012-11-19
Hi Helen, 

Installing ubuntu with wubi has nothing to do with 'virtualization'. Basically you would install a full blown ubuntu, but not on its own patition or disk, but in a virtual disk which is basically one big windows(ntfs)-file.


But I would strongly advise you to try out Ubuntu first with a Live-CD or Live-USB, so you can see whether your hardware is compatible. You can try it out without any change to your current system.

---

### Post by helen2 on 2012-11-19
> **mlentink said:**
> Hi Helen, 
 
Installing ubuntu with wubi has nothing to do with 'virtualization'. Basically you would install a full blown ubuntu, but not on its own patition or disk, but in a virtual disk which is basically one big windows(ntfs)-file.
 
 
But I would strongly advise you to try out Ubuntu first with a Live-CD or Live-USB, so you can see whether your hardware is compatible. You can try it out without any change to your current system.
 
Than'ks so...Let me understand..With Wubi i will have a ubuntu installed on my hdd (and before the hhd will be partitioned) or i will have a file and inside that file i will have the ubuntu (as an vmware hhd or a virtualpc hhd file)?
About your question if my netbook suèpports ubuntu the answer is yes.I have a Asus 1015CX witch cost (230 euro) very good price because there was on ubuntu,the first think i did is to delate everything and install on it a Windows 7 olso becauise as u maybe will see the hardware is not as a notebook but is a quite good netbook.
Take care
Helen

---

### Post by mlentink on 2012-11-19
Okay, then it will be safe to install. 
There are really not many differences between installing ubuntu through wubi versus native. 
The main differences are the speed of disk-access and the fact that (if I remember correctly) a wubi-install is limited in size. 
Since Wubi will install ubuntu in a container, a virtual disk if you like, normal disk-access will need to be translated to 'virtual disk access' and therefore be a bit slower. I doubt however that you will notice this on modern hardware.
The second may not be a big problem on a netbook.

The main purpose of Wubi seems to be to make it easy for Windows users to install ubuntu alongside of Windows, and make it easy to use the Windows method of installing and removing software for installing/uninstalling ubuntu.

Please see also: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

But you could install a true dual-boot situation on your netbook just as easily. I did it recently on a HP-mini 1010 and it works like a breeze.

---

