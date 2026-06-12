---
title: "Support for Xen"
date: 2009-08-25
forum: Virtualisation
---

### Post by tuxsg on 2009-08-25
This thread is uncomplete, at least for me.

I'm running at the job two pools with xenserver enterprise 5.5, and I tested 8.04 with no complications except follow this steps [http://community.citrix.com/blogs/citrite/anilma/2008/07/02/Installing+Ubuntu+on+XenServer](http://community.citrix.com/blogs/citrite/anilma/2008/07/02/Installing+Ubuntu+on+XenServer) but I really want to use jaunty, but since it is unsupported I cannot run it at full speed.

I read about is an issue in the kernel, but I can't remember where, I can try to compile one, but I just forget what is the exact issue or what modules it must include.

Please, if someone can help!

Thanks.

---

### Post by bodhi.zazen on 2009-08-25
> **tuxsg said:**
> This thread is uncomplete, at least for me.

I'm running at the job two pools with xenserver enterprise 5.5, and I tested 8.04 with no complications except follow this steps [http://community.citrix.com/blogs/citrite/anilma/2008/07/02/Installing+Ubuntu+on+XenServer](http://community.citrix.com/blogs/citrite/anilma/2008/07/02/Installing+Ubuntu+on+XenServer) but I really want to use jaunty, but since it is unsupported I cannot run it at full speed.

I read about is an issue in the kernel, but I can't remember where, I can try to compile one, but I just forget what is the exact issue or what modules it must include.

Please, if someone can help!

Thanks.

If you wish to use Xen use a supported host. Currently that means Ubuntu 8.04

Just because jaunty does not support Dom 0 does not make this thread incomplete.

---

### Post by gk_manutd on 2009-09-07
So... does that mean that I cannot use Jaunty as a dom0 host for Xen?

---

### Post by bodhi.zazen on 2009-09-08
> **gk_manutd said:**
> So... does that mean that I cannot use Jaunty as a dom0 host for Xen?

It will be difficult if you try that yes. dom0 is supported in 8.04

---

