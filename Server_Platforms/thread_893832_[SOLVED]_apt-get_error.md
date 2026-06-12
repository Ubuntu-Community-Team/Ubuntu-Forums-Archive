---
title: "[SOLVED] apt-get error"
date: 2008-08-18
forum: Server Platforms
---

### Post by gishaust on 2008-08-18
Hi tried to apt-get update one of my servers but it will not let me do it I keep getting this error

```

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-virtual
Errors were encountered while processing:
 courier-pop
 courier-pop-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anyone know how to fix it?

---

### Post by Titan8990 on 2008-08-18
try:

sudo dpkg configure -a

---

### Post by gishaust on 2008-08-18
thanks

---

