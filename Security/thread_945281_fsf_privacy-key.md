---
title: "fsf privacy-key"
date: 2008-10-12
forum: Security
---

### Post by burlamacco on 2008-10-12
My fsf privacy-key don't run software on hardy 8.04.1, why? There is anyone that have the usb privacy-key and run it succesfully? Help me please... by stefano

---

### Post by cariboo on 2008-10-12
> quote from [http://www.fsf.org/associate/fsf-privacy-key.html](http://www.fsf.org/associate/fsf-privacy-key.html)

To use the FSF Privacy Key (FPK) on a GNU/Linux distribution, that distribution must provide:

    * GNOME Desktop Environment (version 2.8 or later) with libglade2
    * A Python interpreter (version 2.3 or later)
    * A Filesystem Standard Hierarchy 2.3 compliant file tree

**The applications on the FPK expect to be executed from /media/usbdisk** in accordance with the Filesystem Hierarchy Standard (FHS) 2.3 standard. The applications will not work reliably if the key is mounted at any other location.

The live applications expect to find copies of GNU Privacy Guard (including gpg-error) and OpenSSH in the system available in the path.

This product includes software developed by the OpenSSL Project for use in the OpenSSL Toolkit.
This product includes cryptographic software written by Eric Young.

Jim

---

