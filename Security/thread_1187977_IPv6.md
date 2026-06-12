---
title: "IPv6"
date: 2009-06-15
forum: Security
---

### Post by yeleek on 2009-06-15
Hi,

Am running Jaunty and not using IPv6, I am behind a IPv4 router.  Therefore want to disable it not because of any performance issues as per the other threads on the forums but just because best security practice states if not used, disable it.

Anyone know how please?

Thanks

---

### Post by ihatetryingtopickaloginna on 2009-06-15
I did it in Hardy this way... sudo gedit /etc/modprobe.d/blacklist and then add 'blacklist ipv6' to the end of the file.

---

### Post by yeleek on 2009-06-15
Hi,

Have added that - so now the only contents of file are

```
blacklist ipv6
```

rebooted, however ipv6 still showing under ifconfig.

Thansk

---

### Post by cariboo on 2009-06-16
IpV6 is compiled directly into the kernel, the only way I know to stop ipv6 from loading, is to compile a custom kernel.

---

### Post by azc on 2009-06-16
> **yeleek said:**
> Hi,

Have added that - so now the only contents of file are

```
blacklist ipv6
```

rebooted, however ipv6 still showing under ifconfig.

Thansk

Try adding the next line in addition to 'blacklist ipv6':

```

install ipv6 /bin/true

```

---

