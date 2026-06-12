---
title: "No suspend when lid closed with kernel 3.8"
date: 2013-01-12
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-01-12
hi,

since 3.8, I get a lock screen instead of a suspend when I close my laptop's lid. ThinkPad X220, intel graphics.
(Was ok in 3.7.)

Anyone is having the same issue ?
Thanks.

---

### Post by pqwoerituytrueiwoq on 2013-01-12
works for me on my xubuntu qunatal with 3.8.0-030800rc3-generic (my laptop; see signature)

---

### Post by ft_ on 2013-01-12
OK !
I got it.

It was caused by a script which avoid suspend-bug with usb 3, located in **/etc/pm/sleep.d** .
I removed this well-known script and my comp went suspended without any trouble.

Sorry for the non-existing issue.


(Note that this script never caused issue before, ie with kernels 3.5 and 3.7.)

---

### Post by cariboo on 2013-01-12
> **ft_ said:**
> OK !
I got it.

It was caused by a script which avoid suspend-bug with usb 3, located in **/etc/pm/sleep.d** .
I removed this well-known script and my comp went suspended without any trouble.

Sorry for the non-existing issue.


(Note that this script never caused issue before, ie with kernels 3.5 and 3.7.)

This is why we are here, even though there are plenty of automated test done, they can't test every thing. This is a corner case that testing missed. Hopefully you created a bug report, and included your work-a-round.

---

### Post by ft_ on 2013-01-12
Since it is absolutely not an official script I deleted, I did not create any bug report. Nonetheless, it may be useful to know this workaround for updaters. I did find that with some flair, absolutely not reading any error log... :mrgreen: So I damn do not know why now this script avoid suspend.

---

### Post by pqwoerituytrueiwoq on 2013-01-12
what was the script? care to share the name of this "well known" script

---

### Post by ft_ on 2013-01-13
I do not think that an user who has created this script in /etc/pm/sleep.d will have any doubt, but if you care about it :

```
#!/bin/sh

EHCI_BUSES="0000:00:1a.0 0000:00:1d.0"
case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $EHCI_BUSES; do
            echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $EHCI_BUSES; do
            echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/bind
        done
        ;;
esac
```

It was designed for an Asus K43SA but I migrated my hard disk to a ThinkPad X220 without USB 3. I forgot to delete it, without any consequence before kernel 3.8.

---

### Post by jbicha on 2013-01-13
By the way, I don't believe automatic suspend on screen closing works with the GNOME3 Staging PPA. The GNOME developers really want us to use systemd.

---

### Post by cariboo on 2013-01-13
> **jbicha said:**
> By the way, I don't believe automatic suspend on screen closing works with the GNOME3 Staging PPA. The GNOME developers really want us to use systemd.

It does work on my Compaq netbook, but there isn't any way to enter a password on my system to unlock it. I'm currently using auto-login to access the desktop from a cold boot.

---

### Post by ft_ on 2013-01-13
Since I removed the script, the suspend works perfectly : quick + password back from suspend.

---

