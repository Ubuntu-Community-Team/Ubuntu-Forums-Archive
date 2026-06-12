---
title: "How to fix low-resolution login screen with VirtualBox Guest Additions 5.1"
date: 2017-04-01
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2017-04-01
Internet searching turned up nothing at all about this problem, so posting the solution here to save this community some time and headaches.

I have a Lubuntu 14.04 VM in VirtualBox.  It had VirtualBox Guest Additions version 5.0.2, where the login screen used the same resolution as after logging in.

I recently upgraded VirtualBox to version 5.1.18.  And in my Lubuntu 14.04 VM, when upgrading VirtualBox Guest Additions to the version 5.1.18, the login screen resolution became stuck at like 800x600 or so.  Only after logging in does the proper resolution get restored.

Fortunately, the old behavior can be restored.  Create a file in [FONT=Courier New]/etc/lightdm/lightdm.conf.d[/FONT] named [FONT=Courier New]vboxadd-login-screen-fix.conf[/FONT] and fill it with this -
```

[SeatDefaults]
greeter-setup-script=VBoxClient --display

```

Reboot the VM and the login screen should have the proper resolution again.

---

### Post by Paddy Landau on 2017-04-03
Thanks for this.

In my case, going to full-screen solved the problem all by itself (after a VM restart). But your solution is worth noting.

---

### Post by &amp;KyT$0P# on 2017-04-03
You're welcome. :KS

By the way, this solution might only work on *buntu guests.  It fails weirdly on CentOS 7 (with lightdm) for one.

---

