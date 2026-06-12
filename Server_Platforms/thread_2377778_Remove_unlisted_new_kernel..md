---
title: "Remove unlisted new kernel."
date: 2017-11-16
forum: Server Platforms
---

### Post by meerektee on 2017-11-16
Hello. I'm running Ubuntu 16.04 server. Recently I upgraded my kernel to 4.14.0-041400 but my NIC drivers wouldn't work, so I reverted to the old kernel and I'm struggling to remove 4.14.0-041400, when I run sudo dpkg --list | grep linux-image the 4.14.0-041400 is not listed thus I can't use apt-get purge linux-image-4.14.0-041400, how do I get rid of 4.14.0-041400? Thanks.

---

### Post by jeremy31 on 2017-11-16
Any results for ```
ls ~/Downloads | grep linux
```
```
ls ~/ | grep linux
```

---

### Post by howefield on 2017-11-16
Thread moved to the "*Server Platforms*" forum.

---

### Post by meerektee on 2017-11-16
Nothig, but I can see it in /boot though just wondering if I could just rm all [COLOR=#000000]4.14.0-041400 entries from there and should I be fine?[/COLOR]

---

### Post by ian-weisser on 2017-11-16
Any idea *how* you upgraded your kernel?
That version number does not look like stock Ubuntu. Do you download kernel upgrades from someplace else?

---

### Post by meerektee on 2017-11-16
Yes, I followed this: [https://www.tecmint.com/upgrade-kernel-in-ubuntu/?utm_content=buffera80f2&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer](https://www.tecmint.com/upgrade-kernel-in-ubuntu/?utm_content=buffera80f2&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer),
 then I tried to restore system from snapshot but turned out kernel in snapshot been updated as well and had to revert to old kernel.

---

### Post by darkod on 2017-11-16
Well, if you used dpkg -i filename.deb to install it, then you should be able to remove it by 'dpkg --purge filename.deb'.

Ubuntu 16.04 supports up to 4.10 at the moment. I don't know if you really need 4.14 but note that kernels installed like this can often bring you more problems than they solve. Like you saw yourself.

I would stick to kernels supplied by Ubuntu repositories, unless you really, really need something else. And in that case make sure you know what you are doing... The internet is big, just because someone posted some tutorial it doesn't mean you should follow it. Why didn't they post how you can get out of this situation now for example...

---

### Post by ian-weisser on 2017-11-16
> **meerektee said:**
> Yes, I followed this: [https://www.tecmint.com/upgrade-kernel-in-ubuntu/?utm_content=buffera80f2&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer](https://www.tecmint.com/upgrade-kernel-in-ubuntu/?utm_content=buffera80f2&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer),

Egad, those instructions are horrifying.
If those instructions appeared on this forum, targeting unskilled users and without the essential warnings, I would flag it as malicious.
For most users, the automatic kernel upgrades from the Ubuntu are adequate.

---

### Post by meerektee on 2017-11-27
Just wanted you guys to let you know that I solved it by reinstalling 4.14.0-041400 and then I was able to list it and uninstall it. Problem was caused because after installing 4.14.0-041400 I restored system from snapshot but that snapshot already had included new kernel but not all the entries which would allow me to uninstall it. Thanks for your replies.

---

