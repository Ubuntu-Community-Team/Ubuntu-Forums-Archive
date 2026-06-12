---
title: "Deleted named.conf*"
date: 2006-08-14
forum: Server Platforms
---

### Post by lionsnob on 2006-08-14
Hello all,

I installed bind9 yesterday and was stupid and deleted the named.conf* files from /etc/bind/

I tried uninstalling and reinstalling bind9 via apt-get, but the files did not reappear.  Can someone post the default files or tell me how to reinstall them?

Thanks!

---

### Post by mlind on 2006-08-14
> **lionsnob said:**
> Hello all,

I installed bind9 yesterday and was stupid and deleted the named.conf* files from /etc/bind/

I tried uninstalling and reinstalling bind9 via apt-get, but the files did not reappear.  Can someone post the default files or tell me how to reinstall them?

Thanks!

```

sudo aptitude purge bind9
sudo aptitude install bind9

```

If aptitude wants to remove other pacakges too, use *dpkg -P --force-depends*

---

### Post by lionsnob on 2006-08-14
Sweet.  Thanks a million.

---

### Post by gishaust on 2007-10-09
Yes I did the same thing and thankyou for the information
 gishaust

---

