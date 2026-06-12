---
title: "ypbind shutdown problems"
date: 2005-02-09
forum: The Cafe
---

### Post by TobyCat on 2005-02-09
hello all,

I've been using ubuntu for a little over a month now and am currently using the unstable tree. Everything works great except for when I shutdown/reboot my station. I work in a corporate environment and have ypbind setup to grab external authentication.


The problem is that when I go to shutdown, the computer will hang on "Deconfiguring network ". It then will sit for ~10 minutes and report back "eth0: network connection down". It did not do this before I installed nis/ypbind, so I think it may have something to do with this.

Could it possibly be a shutdown ordering problem?

Thanks,

-Chris

---

### Post by poofyhairguy on 2005-02-09
[QUOTE=TobyCat]hello all,

I've been using ubuntu for a little over a month now and am currently using the unstable tree. Everything works great except for when I shutdown/reboot my station. I work in a corporate environment and have ypbind setup to grab external authentication.


The problem is that when I go to shutdown, the computer will hang on "Deconfiguring network ". It then will sit for ~10 minutes and report back "eth0: network connection down". It did not do this before I installed nis/ypbind, so I think it may have something to do with this.

Could it possibly be a shutdown ordering problem?

Thanks,

-Chris[/QUOTE]

um....I just turn the damn thing off every time with the button. Does not shutting of cause problems?

---

### Post by TravisNewman on 2005-02-09
Depends on how far along in the shutdown process it is. If it's unmounted and remounted read only it shouldn't, but there's never any guarantee. But you really shouldn't just hit the button unless it's necessary. This was a bigger problem with Windows, but it's still not safe. The shutdown option wouldn't be there if it weren't necessary.

---

