---
title: "Update Manager and weird mouse behavior"
date: 2009-11-06
forum: The Cafe
---

### Post by vaxman- on 2009-11-06
Three issues I can't seem to resolve.

1.  The update manager no longer seems to put up an icon in the panel when there are updates.  This was working quite well in 8.10 but seem to have done missing with 9.10.

2.  The mouse.  I often plug an external USB mouse into my laptop instead of using the trackpad.  I used to be able to have it disable the trackpad when the external mouse was present.  This no longer functions.  Also, from time to time, if I unplug the USB mouse and then install it again, it will not move the cursor.  A restart seems to be the only solution.

3. Grub stalls on restart.  This occurred under 8.10 as well.  I have also installed Grub2 with the same results.  If I restart, the system stops displaying GRUB...  The system boots just fine from a cold start.  If there was some way to force a hard reset in the laptop, it might correct this issue.  I'm not TOO concerned save for those times when I MIGHT be out on the road with this laptop at home and something causes it to reboot... it won't come back up cleanly.

---

### Post by hal10000 on 2009-11-06
> 3. Grub stalls on restart. This occurred under 8.10 as well. I have also installed Grub2 with the same results. If I restart, the system stops displaying GRUB... The system boots just fine from a cold start. If there was some way to force a hard reset in the laptop, it might correct this issue. I'm not TOO concerned save for those times when I MIGHT be out on the road with this laptop at home and something causes it to reboot... it won't come back up cleanly

In grub2 the boot menu is hidden by default. You can change this behaviour by editing the file **/etc/default/grub** and comment out the GRUB_HIDDEN_TIMEOUT line (just put a # at the begining of the line)
and make sure the timeout line looks like this
```

GRUB_TIMEOUT=10

```
this puts a timeout of 10 seconds berfore booting the default system

---

### Post by vaxman- on 2009-11-06
> **hal10000 said:**
> In grub2 the boot menu is hidden by default. You can change this behaviour by editing the file **/etc/default/grub** and comment out the GRUB_HIDDEN_TIMEOUT line (just put a # at the begining of the line)
and make sure the timeout line looks like this
```

GRUB_TIMEOUT=10

```
this puts a timeout of 10 seconds berfore booting the default system
How does enabling the boot menu going to help if GRUB won't load either way on restart boot?

I get:
**GRUB**
then after a brief wait...
**GRUB loading**
then after another brief wait...
[B]loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
loading
[/B]

The only way to get Ubuntu booted is to start from a powered-off state.

---

### Post by hal10000 on 2009-11-06
Sorry, i guess i misunderstood you.

This looks as if it has something to do with BIOS or ACPI settings, but i have no idea to help you out.

---

