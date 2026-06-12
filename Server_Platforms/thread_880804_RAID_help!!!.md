---
title: "RAID help!!!"
date: 2008-08-05
forum: Server Platforms
---

### Post by cmpbgl00 on 2008-08-05
I am in the process of installing Zimbra Collabration Suite to provide in-house email for my company. Zimbra is certified on Ububtu 6.06 LTS and this is what we are trying to use. I installed an Areca ARC-1200 RAID Controller but the Ubuntu install disk does not see the array.  How can I add the driver for this controller.

I am under the impression that Ubuntu is based on Debian linux and I have the drivers ( .c and .h files) for the following Debian kernel versions:
kernel-version-2.5.x-2.3.x
kernel-version-higher-2.6.0
kernel-version-lower-2.3.x

Any help that anyone can give me would be greatly appreciated.

---

### Post by Krupski on 2008-08-07
> **cmpbgl00 said:**
> I am in the process of installing Zimbra Collabration Suite to provide in-house email for my company. Zimbra is certified on Ububtu 6.06 LTS and this is what we are trying to use. I installed an Areca ARC-1200 RAID Controller but the Ubuntu install disk does not see the array.  How can I add the driver for this controller.

I am under the impression that Ubuntu is based on Debian linux and I have the drivers ( .c and .h files) for the following Debian kernel versions:
kernel-version-2.5.x-2.3.x
kernel-version-higher-2.6.0
kernel-version-lower-2.3.x

Any help that anyone can give me would be greatly appreciated.

Any reason why you can't just use the Ubuntu raid system (MDADM)?

-- Roger

---

### Post by windependence on 2008-08-08
Zimbra specifically tells you they do NOT recommend installing the product on RAID. Just set up an LVM group.

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

-Tim

---

