---
title: "restore ipod errors in VB?"
date: 2012-03-04
forum: Virtualisation
---

### Post by qwertyjjj on 2012-03-04
I am trying to restore my iPod in VB but even though the USB disconnects and I remount it, it still fails after with "the ipod could not be restored error 14".
Is it not possible to do this via VB?

---

### Post by An Sanct on 2012-03-04
Shut down your guest machine and from inside the VirtualBox settings select "USB" and add a filter, defining the affinity of a device to the host, once plugged in. This should solve your problem - it has mine, similar problems with my Blackberry 9000.

---

### Post by qwertyjjj on 2012-03-04
> **An Sanct said:**
> Shut down your guest machine and from inside the VirtualBox settings select "USB" and add a filter, defining the affinity of a device to the host, once plugged in. This should solve your problem - it has mine, similar problems with my Blackberry 9000.

How does adding a filter permanently attach the device? Also, when the ipod switches between recovery mode and normal, won;t the filter change?

it goes through resroe then disconnects the usb, then I have to manually reconnect it on  the bottom right, but then it fails.

---

### Post by qwertyjjj on 2012-03-04
seemed to work, thanks!

---

