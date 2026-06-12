---
title: "MaaS Limitation? Customized LVM Layout in MaaS for Dell R620 Installations"
date: 2017-10-27
forum: Ubuntu Cloud and Juju
---

### Post by traiano on 2017-10-27
Hi

Ubuntu MaaS seems quite limited in that it only offers a standard LVM layout on a given storage device.
I can't seem to find any detailed documentation on how to fully customise the LVM layout.
I think this should be in the preseed configuration documentation, but there are no examples I can find on the net which match my very basic requirement of a custom LVM partitoning scheme.

Please could someone point me to some working examples of Ubuntu MaaS configuration preeseeds  or a method to customise my LVM layout from the UI or cli?

Many thanks in advance!
Traiano

---

### Post by DLGandalf on 2017-12-31
Are you sure that you´ve installed the lastest version? I can create any disk partition layout I want, including advanced stuff like bcache and RAID.

---

