---
title: "TI-89 Titanium help, software"
date: 2006-12-26
forum: The Cafe
---

### Post by angryfirelord on 2006-12-26
Just got a TI-89 Titanium for X-Mas! Obviously, the first thing I wanted to do was hook it up to the computer.

However, I don't know what software works for it. It appears that Ubuntu does detect its presence.

dmesg:
```
[17183339.312000] usb 4-1: new full speed USB device using uhci_hcd and address 2

```

I unplugged it and plugged it back in to make that it was the calculator and not some other device.

```
[17183540.168000] usb 4-1: USB disconnect, address 2
[17183547.464000] usb 4-1: new full speed USB device using uhci_hcd and address 3

```

I'm mainly interested in just uploading games and other goodies to its ROM.

---

### Post by Jeff250 on 2006-12-26
Your next goal will be to get tilp2 working with it.  I tried this a while ago but didn't have much luck.

---

### Post by angryfirelord on 2006-12-26
The regular tilp in the Ubuntu repos doesn't work with the Titanium

So, I got the tarball for tilp2, but it wasn't able to find its own makefile.

Instead, I went and got the rpm (using google and rpm.pbone.net) files and converted them using alien (including dependencies).

So far, alien was very successful until I ran *tilp* and got the error message:
```
master@xubuntu:~$ tilp
tilp: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by tilp)
tilp: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libticalcs2.so.2)
tilp: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libticables2.so.1)
tilp: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libtifiles2.so.3)

```

Apparently, tilp2 needs version 2.4 of libc6, which is not in the dapper repos. Because libc6 (or glibc) is a crucial component, is there another deb build of it around somewhere?

---

