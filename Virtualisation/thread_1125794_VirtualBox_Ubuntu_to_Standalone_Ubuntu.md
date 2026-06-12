---
title: "VirtualBox Ubuntu to Standalone Ubuntu"
date: 2009-04-14
forum: Virtualisation
---

### Post by wrwarwick on 2009-04-14
I have a question that I have never really heard of being done but I thought I would ask.

I am currently running Vista on my desktop with Ubuntu running in a VirtualBox VM. I want to put Ubuntu on my laptop, but was wondering if there is a way to "transfer" the VM to the laptop and make it the primary OS. 

If there is not a way to do this, is there a way to transfer the files and settings, say, over the network?

Thanks again for any help.

---

### Post by bodhi.zazen on 2009-04-14
You can try making a copy of the hd image with dd and writing to the laptop.

IMO it is likley just as easy to install Ubuntu on the laptop and tx settings.

You can Tx settings with any network protocol, ssh (scp), nfs, samba, ftp, http ... or with a flash drive.

---

