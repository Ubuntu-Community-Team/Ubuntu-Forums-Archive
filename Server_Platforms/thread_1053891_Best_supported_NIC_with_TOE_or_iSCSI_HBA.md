---
title: "Best supported NIC with TOE or iSCSI HBA"
date: 2009-01-29
forum: Server Platforms
---

### Post by Hark on 2009-01-29
Hi,

I am planning to set up a iSCSI environment. I'm testing with the iSCSI enterprise target (package iscsitarget) and the open-iscsi initiator. Works fine, but for performance reasons I think I should use a NICs with TOE or iSCSI HBAs on my hosts. What would be the best supported NICs with TOE or iSCSI HBAs? They should be supported out-of-the-box under Ubuntu 8.04. I found the QLogic QLA4050C, that looks quite OK (although their site only talks about SuSE/Red hat).
For the target I think I'd like to continue the use of the iSCSI enterprise target, because that will probably be the easiest way to create/remove iSCSI targets using some script. But I'd like to buy a 10Gbit NIC with TOE for this target, which ones are supported the best?

I hope some of you can push me in the right direction. It wouldn't be the first time I buy something from a manufacturer that doesn't give a sh*t about Ubuntu/Debian support. Of course I prefer a manufacturer that actively supports the development of open source Linux drivers.

---

### Post by redroad55 on 2009-01-29
Hi I have had good luck with adaptec read this [http://www.adaptec.com/en-US/_common/linux/#1]("http://www.adaptec.com/en-US/_common/linux/#1")
wish you the best

---

