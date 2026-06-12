---
title: "GRUB install on server raid 1 dell poweredge 1900"
date: 2009-11-15
forum: Server Platforms
---

### Post by bertmanphx on 2009-11-15
Hello,
I want to install Ubuntu on a Dell 1900 Poweredge Server with a Perc5 controller, using two SATA drives in a raid 1 configuration.

Will GRUB configure itself on both drives for redundancy?  I think the old GRUB version had difficulty with this, but I'm not sure about the new one.

Any help or thoughts is appreciated.

Thanks,

bertmanphx

---

### Post by bertmanphx on 2009-11-26
Hello,
I was hoping somebody would chime in before I have to perform this task..... I'll report back my results.  I'm flying blind!

bertmanphx

---

### Post by trundlenut on 2009-11-27
Assuming that that us a proper hardware raid card then unbuntu won't see individual disks just the raid arrays.

I have a PE2800 with an older perc card in it and before installing ubuntu I set up a single raid 1 array and then installed the OS.  The card handles all the array to disk issues and ubuntu/grub is none the wiser.

I think there are potential issues with GRUB when using software raid but not hardware.

---

### Post by bertmanphx on 2009-11-27
Trudlenut,
That is what I am hoping for.  I'll find out today :)

Thank you for the reply.

bertmanphx

---

### Post by nknk on 2010-02-02
hi bertmanphx, do you have any feedback? I'm planning to install Ubuntu Server on the same machine (Poweredge 1900 feat. Raid controller card). did you encounter any problem?

---

### Post by bertmanphx on 2010-02-02
nknk,
I did not have any trouble at all.  Because the Perc5 raid controller is a hardware raid, Grub, and the OS see it as a single entity.  Partition as you like.  One thing I had not done before, was to re-build the array from within the Perc5 software.  It took quite a while to complete.  If you are starting with new drives, don't expect it to be an early day.. :)

bertmanphx

---

