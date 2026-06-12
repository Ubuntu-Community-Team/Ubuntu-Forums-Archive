---
title: "Log as root only with a USB key."
date: 2008-07-11
forum: Security
---

### Post by MadGr286 on 2008-07-11
Hello everyone.

Sorry if my question has already been asked, I was searching for many hours and I couldnt find anything.
I want to know if there is a way to log as root only when a USB flash drive is pluged in on my pc with Ubuntu 8.04. I mean when I am asked for my password, I want to just plug the USB flash and work as root but if the USB flash is not pluged in to be imposible for someone to log as root.
Sorry for my English.

Thank you for your time.

---

### Post by cdenley on 2008-07-11
[http://pamusb.org/doc/quickstart](http://pamusb.org/doc/quickstart)

---

### Post by unutbu on 2008-07-11
Does pam_usb alter a user's membership in the admin group, cdenley? If it does not, then the user will be able to use sudo even if the USB key is not plugged in. Or am I wrong?

---

### Post by cdenley on 2008-07-11
> **unutbu said:**
> Does pam_usb alter a user's membership in the admin group, cdenley? If it does not, then the user will be able to use sudo even if the USB key is not plugged in. Or am I wrong?

No, I don't think you're wrong. I think one of us misunderstood what the OP meant. It will allow you to authenticate as a particular user without a password if a specific usb drive is connected. The OP would configure the root account. They can then login as root without being prompted for a password when the usb drive is plugged in. When the usb drive isn't plugged in, they will be prompted for a password, but by default there is no valid password.

---

### Post by MadGr286 on 2008-07-12
> **cdenley said:**
> [http://pamusb.org/doc/quickstart](http://pamusb.org/doc/quickstart)

Thank you for quick answer :)

---

### Post by mriedel on 2008-07-12
You might want to have a look at [this thread](http://ubuntuforums.org/showthread.php?t=17571) and [this post](http://ubuntuforums.org/showpost.php?p=5370126&postcount=21). Note that the instructions in first few posts of that HOWTO don't apply any more.

---

### Post by SnappyU on 2009-03-15
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

### Post by johnymucks on 2009-07-23
Hi! been trying this with Ubuntu 9.04 I managed to make it work with USB drive, but I can not make it work with mmc/sd cards.. any help ?

---

