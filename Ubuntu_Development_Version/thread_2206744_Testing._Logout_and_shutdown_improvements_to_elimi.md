---
title: "Testing. Logout and shutdown improvements to eliminate text messages."
date: 2014-02-20
forum: Ubuntu Development Version
---

### Post by philinux on 2014-02-20
As part of*[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/967229](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/967229)

recently a number of uploads were done to improve shutdown ordering,
such that there is a smoother transition between lightdm shutting down
and plymouth shutdown splash animation appearing. Ideally, upon
shutting down, one shouldn't see intermittently any console messages.

If you in the past, upon shutdown, used to see some white messages on
black background between desktop session tear-down and plymouth
shutdown splash appearing, please consider testing latest trusty
packages of upstart, lightdm and plymouth. And please report back if
things improved (no more messages seen), stayed the same (some
messages are still seen), or got worse (i had no reports of those so
far).

If there are positive improvement reports, we will consider
back-porting this set of changes to precise.

--*
Regards,

Dimitri.

---

### Post by ventrical on 2014-02-20
@ Dimitri,

 That aspect is working really good.  Nearly none to mention on shutdown.

---

### Post by philinux on 2014-02-20
> **ventrical said:**
> @ Dimitri,

 That aspect is working really good.  Nearly none to mention on shutdown.

@ventrical. I forgot to put quotes on. That above from the devel discuss mailing list.

---

