---
title: "liblzma.so no version information available (required by dpkg-deb)"
date: 2012-10-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by masuch on 2012-10-10
Hi,

I have upgraded from 12.04 to 12.10 and within upgrading and now apt-get install/upgrade appeared message:
> dpkg-deb: /usr/local/lib/liblzma.so.5: no version information available (required by dpkg-deb).
Installation process went ok.

Is there any workaround how to get rid of it ?
I have compiled xz 5.0.4 manually but still no luck.

Thank you,
Kind Regards,
Martin

---

### Post by oldos2er on 2012-10-10
Moved to Ubuntu +1 (Quantal Quetzal).

---

### Post by dino99 on 2012-10-10
install then purge lzma, that should remove the old setting left behind

---

### Post by masuch on 2012-10-11
> **dino99 said:**
> install then purge lzma, that should remove the old setting left behind

thanks for tip but I cannot try it because it is going to remove another 100 packages - I would prefered some another way.

Is it possible to remove it and install it without removing other packages safely ?

---

