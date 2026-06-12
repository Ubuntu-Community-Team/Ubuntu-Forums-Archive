---
title: "Virtualization question"
date: 2008-04-19
forum: Virtualisation
---

### Post by StOoZ on 2008-04-19
I was just wondering, is is possible to create 3 virtual machines on a single system, and them connect that system/computer physically to 3 other computers(real ones :) ),without H.D.D's and make those 3 computers remotely use those virtual machines over the network?

---

### Post by fjgaude on 2008-04-19
From what little I know, yes I think it is possible. I've never tried it though.

---

### Post by StOoZ on 2008-04-19
I tried googling it somehow, but to no avail.

if its possible, it could solve me a lot of headache and money.. :guitar:

thanks for you reply, I'll wait a little bit more , maybe more replies will follow.

---

### Post by ryanhaigh on 2008-04-19
Perhaps you should provide a little more detail on what you want to do here, are you wanting to run windows or linux for these remote clients? Could you use ltsp [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto) rather than setting up VMs. 

If you want to run windows all you need is thin clients that are rdesktop capable and windows server/pro (these are the only ones with RDP) VMs with bridge networking. You could set them up to use vnc also.

If you want to run ubuntu you should be able to use ltsp/vnc/xdmcp/NX for the protocol again with bridged networking.

I have done thin client setup with simple xdmcp although I used low spec systems with hd's as it was just easier to setup.

---

### Post by ericy on 2008-04-20
Maybe you can try this:

[http://en.wikipedia.org/wiki/DRBL](http://en.wikipedia.org/wiki/DRBL)

---

