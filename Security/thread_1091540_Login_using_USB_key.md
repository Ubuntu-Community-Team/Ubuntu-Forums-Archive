---
title: "Login using USB key"
date: 2009-03-09
forum: Security
---

### Post by spartanx86 on 2009-03-09
I'm running Ubuntu 8.04.2, is there a method of logging into the OS using a USB drive?

Basically I want the USB drive to act as a key to login instead of a username and password.

---

### Post by cdenley on 2009-03-09
```

sudo apt-get install libpam-usb
zcat /usr/share/doc/libpam-usb/QUICKSTART.gz|less

```

---

### Post by hacker07.gbh on 2009-03-12
> **cdenley said:**
> ```

sudo apt-get install libpam-usb
zcat /usr/share/doc/libpam-usb/QUICKSTART.gz|less

```

what does that code do really

---

### Post by cdenley on 2009-03-13
It installs the PAM module for USB authentication, then it displays a compressed text file installed from the package containing instructions for how to configure and use the module.

---

### Post by bodhi.zazen on 2009-03-13
> **cdenley said:**
> ```

sudo apt-get install libpam-usb
zcat /usr/share/doc/libpam-usb/QUICKSTART.gz|less

```

Very interesting, thank you for that information.

---

### Post by SnappyU on 2009-03-15
Great! Just what I was looking for ... :D

EDIT:

Everything is working fine ... but note the following.
Tested on Ubuntu 8.10

PAM Module ***IMPORTANT***
According to the site above:
Locate the following line on /etc/pam.d/common-auth or /etc/pam.d/system-auth:
> auth    required        pam_unix.so nullok_secure

And change it to look something like that:
> auth    sufficient      pam_usb.so
auth    required        pam_unix.so nullok_secure


For Ubuntu 8.10, the above would cause strange behaviour, instead change it to the following:

> auth    sufficient      pam_usb.so
auth	[success=1 default=ignore]	pam_unix.so nullok_secure


---

### Post by Betty1978 on 2009-03-16
I too wanted answer to this problem. Now I cleared of it. Thanks

---

### Post by Kobalt on 2009-03-16
Great tip indeed, I did not know of a libpam-usb package.
I'll look into it tonight, thanks :)

---

