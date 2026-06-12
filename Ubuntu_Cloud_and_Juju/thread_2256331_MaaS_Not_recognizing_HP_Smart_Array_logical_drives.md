---
title: "MaaS Not recognizing HP Smart Array logical drives"
date: 2014-12-11
forum: Ubuntu Cloud and Juju
---

### Post by tyson-c on 2014-12-11
I have a C7000 chassis with six nodes that are being managed by MaaS that has been installed on a separate external node. The blades all get added to MaaS just fine and get commissioned as I would expect. However, once commissioning is complete the disk shows as being 1GB even though all the nodes have two 72GB or two 146GB logical drives defined through the array controller. Both the scsi devices are displayed in the discovery details but it doesn't appear that lvm is provisioning the volumes as only SDA is created and it is only about 1.4GB in size. Anyone have any ideas what could be causing this? Thanks in advance!

---

### Post by xrobau on 2014-12-13
So, after doing some digging through everything, it all comes down to 'lshw'. 'lshw' is a venerable and well used tool to get hardware details.

However, lshw does not, and can't, understand the cciss driver.   After tracking it down inside the source code, the scan_devices() function [for anyone who is reading this from the future] tries to do SCSI IOCTLs on the device (after you've added /dev/cciss/* to the glob), and the disks don't respond as a SCSI device. 

Honestly, I think the best idea would be to code an OVERRIDE for maas, or, a slightly different (and not so complex) way of getting the list of disks from the machine. 

I have, actually, just added a patch for this to curtin, too. 

[https://bugs.launchpad.net/curtin/+bug/1263181?comments=all](https://bugs.launchpad.net/curtin/+bug/1263181?comments=all)

---

### Post by tyson-c on 2014-12-13
That sounds like the way to go. I have opened a bug with the MaaS team and someone, one of the devs I think, added curtin as an affected package. 

By chance do you think that the patch you posted would help MaaS along or does the discovery occur prior to curtin ever being ran?

---

### Post by xrobau on 2014-12-17
I had a quick chat with the MAAS guys on IRC, and we figured out a better way of doing things. Hopefully it'll appear in the public view soon.

For the moment, I'm just using that patch, which is good enough to at least deploy some machines.

---

