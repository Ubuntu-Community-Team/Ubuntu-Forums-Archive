---
title: "problem starting vmware"
date: 2008-05-13
forum: Virtualisation
---

### Post by jman623 on 2008-05-13
hi all,

well first off I'd like to thank bodhi.zazen for his excellent tutorial on installing vmware-server on hardy. Unfortunately I have come across a problem whenever I try to run vmware I get this output:

```
justin@justin-desktop:~/src/vmware/vmware-any-any-update116$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

now I already installed build-essentials, what could be the issue here?:confused:

---

### Post by StOoZ on 2008-05-13
try this:
> sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

---

### Post by jman623 on 2008-05-13
thanks stooz that worked!

---

### Post by scottws on 2008-05-15
I had the same problem and StOoZ's fix worked.  Why did this happen?  VMware Server Console worked fine recently (can't remember if it was working for sure after 8.04 upgrade...).

---

### Post by useResa on 2008-09-03
I encountered  the same issue after upgrading to the latest release of VMware Server (1.0.7 - build 108231). This fix also resolved the issue for me.
Thanks.

---

### Post by moderndrummer on 2008-09-11
> **StOoZ said:**
> try this:


Thanks a million StOoZ.. It worked for me too.. Keep up your good work :)

---

### Post by mrojas73 on 2008-09-14
Thank you as well.

---

### Post by kc2bxn on 2008-09-30
it worked for me :D :guitar:

---

### Post by gishaust on 2009-01-14
thanks for the last two months every time I wanted to start the vmware console I would have to reinstall it.

thank you. If i new where that thank you button was I would press it

---

