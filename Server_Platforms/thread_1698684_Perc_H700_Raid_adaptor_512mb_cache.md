---
title: "Perc H700 Raid adaptor 512mb cache"
date: 2011-03-02
forum: Server Platforms
---

### Post by dodgyphil on 2011-03-02
Hi,

I am looking at buying a Dell T310 Server. Want to upgrade from the "Embeded software Raid" to a Perc H700 RAID adapter.

Has anyone installed Ubuntu using this RAID set up before? Are there any known compatability issues or pitfalls, I should be aware of?

Just want a simple mirrored hard drive array.

Want to make sure it is the right way to go before making the purchase.

Cheers
Phil D

---

### Post by ramasan on 2011-07-06
I have the H700 in an R310 and cannot boot 11.04 or 10.04 out of the box.

After a successful installation, upon reboot I get, 

Out of disk
grub rescue

Other links seem to indicate that it doesn't work well with the megaraid driver. Other search results seem to indicate people have it working.

I would like to know how other people are getting it working.

---

### Post by dodgyphil on 2011-07-07
Ok,

Have had the server up and running for a while. I have installed ESXi and am running Ubuntu 10,04 as a virtual server. It all works well under this set up. Running as Windows PDC.

So cant say if it would work as a physical installation, but works well as a virtual machine.

Cheers
Phil D

---

