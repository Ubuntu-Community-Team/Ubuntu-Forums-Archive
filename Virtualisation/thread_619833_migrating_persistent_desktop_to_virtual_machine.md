---
title: "migrating persistent desktop to virtual machine"
date: 2007-11-21
forum: Virtualisation
---

### Post by aglatzer on 2007-11-21
Hello,

I've been using ubuntu 6.06 for some months now, booting from live CD
and using a USB stick for persistent desktop.  However I find it perilous with a USB stick protruding from my laptop.  Therefore I'd like to migrate my persistent desktop to a hard drive installation.  I would also like to switch quickly between vista and ubuntu.  Installing ubuntu in a virtual machine would meet this need nicely.  I have used ubuntu with VirtualBox numerous times but have not been able to use my persistent data in the way that I want.

I have tried several things:

1.  I have successfully booted the live CD within the virtual machine using my USB stick for persistent data.  Of course this doesn't really meet my need since the USB stick is still protruding from my laptop, but at least I know the method works.

2.  I have done a full install of ubuntu on a virtual hard drive, and copied my persistent data there (the /home/ubuntu directory).  My recollection of what happened is vague (it was a while ago) but this is what I think happened: I could not access many of the files even after adding a user named ubuntu.  I also decided to abandon this strategy since many other items in the persistent desktop would not be copied over.

3.  I copied my persistent desktop data to a virtual hard drive labeled casper-rw and tried to boot the live CD.  The boot seemed to hang as if it was unable to find a persistent data drive.

4.  I abandoned my USB stick data altogether and simply tried to get a persistent data loopback file to work on a virtual hard drive (see the live CD persistent data web page [https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence) where it discusses point in loopback file on a hard drive).  This boot also seemed to hang as if it was unable to find a persistent data drive.

Does anyone have any idea how to make this work?  I know I have been short on details but I am not even sure which strategy to use let alone exactly how to implement it.  Again I am trying to run ubuntu in a virtual machine using VirtualBox while including my old persistent data without using a USB stick.

Thanks in advance for any help you can offer.  

aglatzer

---

