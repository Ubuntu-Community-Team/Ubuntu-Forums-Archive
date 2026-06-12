---
title: "Intel igb network driver not working with xen kernel"
date: 2008-06-23
forum: Virtualisation
---

### Post by mueller on 2008-06-23
Hi there,

please see this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/236268](https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/236268)

Intel cards which need the igb driver just won't work with the Ubuntu xen kernels.
According to the launchpad site, the project doesn't seem to be very active in fixing bugs.
What are the chances to get this fixed soon?

---

### Post by mueller on 2008-06-24
Ok, got it working.

You need to get the newest igb drivers from here: [http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=237808](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=237808)
You need, at least, version 1.2.44.3.

Version 1.2.24 (which is linked as the newest version on the Intel Homepage *sigh* [http://downloadcenter.intel.com/detail_desc.aspx?agr=Y&DwnldID=13663](http://downloadcenter.intel.com/detail_desc.aspx?agr=Y&DwnldID=13663))
still has a bug, because of which the nic's will only work after ```
ethtool -K <if> tx off
```.
See: [http://www.mail-archive.com/e1000-devel@lists.sourceforge.net/msg00101.html](http://www.mail-archive.com/e1000-devel@lists.sourceforge.net/msg00101.html)

Now, this version "only" has to make it into the Ubuntu packages.[-o<

---

