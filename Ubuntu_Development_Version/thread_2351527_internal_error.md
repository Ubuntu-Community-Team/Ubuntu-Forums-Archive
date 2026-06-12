---
title: "internal error"
date: 2017-02-04
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2017-02-04
Every time I boot Zesty up I get one or more of these "internal errors":
:
1030804 Feb  4 02:04 _usr_sbin_smbd.0.crash

This is ever since the first Zesty image came  out and persists through every update and on three of my test pc's different brands

Is there any fix for this or is this how Zesty will ship?

Any way to find what Zesty is complaining about?

Thanks

Is this

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1639962](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1639962)

Been around since November and no fix in sight?

Thanks

---

### Post by dino99 on 2017-02-04
canonical quality is becoming bad again since a while; all the resources are busy with next & next+1  :(
the latest uploader has broken it, and except his excuse, he is not so smart to repair his mistake :o
but the solution is done and should not stop you :D

---

### Post by jerrylamos on 2017-02-04
Doesn't stop me except I cannot print to Win10 pc's like Ubuntu used to.

---

### Post by dino99 on 2017-02-04
Either downgrade libtevent0 as explained into the report, or upgrade samba with the debian package. Then you will find back a working shared printing job.

---

