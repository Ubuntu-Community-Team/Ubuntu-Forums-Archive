---
title: "usb2 in virtualbox"
date: 2009-07-21
forum: Virtualisation
---

### Post by styleruk on 2009-07-21
Hi
I've trawled the user forums at virtualbox and now trying here and can't find a simple solution to my problem.
I'm using ubuntu 9.04 64bit with guest operating system of xp home.  All is good, the usb's connect fine etc...
I want to know how to get usb2 working, has anyone got some simple advice for this?
I'm using virtualbox 3.0.2

---

### Post by andrea000 on 2009-07-21
go to system>administration>group and user then at the
bottom click unlock on the right side click manage group
go down to vbox user properties and make sure there is a
check mark by your login name.this may help

---

### Post by styleruk on 2009-07-22
Yes, there is a check mark there.  So I guess it's not that.  (thanks for quick reply).

Si

---

### Post by andrea000 on 2009-07-25
did you add the USB filters?if not install them and guest additions
that should set usb2 usb2 up.

---

### Post by niteshifter on 2009-07-25
Hi,

usb2 as in USB 2.0? In your VM settings, in the Details tab, click the USB section and enable the EHCI controller.

---

### Post by styleruk on 2009-07-29
Yes, I have checked the EHCI controller.  It still runs very slow compared to when using in Ubuntu.

---

### Post by styleruk on 2009-07-29
I have added the filter and still it is slow.

---

### Post by PatrickVogeli on 2009-07-29
I guess that's what you get.. you are virtualizing, so speed won't be as good.

---

