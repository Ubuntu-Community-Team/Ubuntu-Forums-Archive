---
title: "kvm qemu no caps lock in winxp guest OS"
date: 2008-02-07
forum: Virtualisation
---

### Post by aBitLater on 2008-02-07
anyone have the same problem and / or know a fix?

I can't get caps lock on in winxp guest OS.  Host OS is Gutsy.  Using Wireless  Microsoft 6000 mouse and keyboard with USB wireless receiver.

Less importantly, the mouse in guest OS (winxp) doesn't want to move smoothly.  And I sometimes have to reset it when I exit out of guest back to Host.  Any ideas?

Thanks!

---

### Post by aBitLater on 2008-02-08
update:  No fix yet, but I discovered that if I CTRL + ALT to escape out of the qemu / kvm window, I can click again in the window and the caps lock key will work one time.  Subsequent clicks on caps lock will not work - I have to escape out each time to get it to work once.

---

### Post by aBitLater on 2008-02-10
well.. anyone???

I'm trying out virtualbox instead.  While I can't speak for the specs and speed because I don't know those statistics, from an end-user perspective it IS MUCH NICER.

Things I like about VirtualBox over kvm / qemu :

1. Full Screen on my monitor
2. My mouse doesn't stutter in the Guest OS (helps my carpal tunnel syndrome)
3. Caps Lock works (i program in guest OS, this is important)
4. Took WAY less time to set up.  I didn't even have to read a manual.

just my two-cents.  I'm sure some people like kvm because it takes advantage of the virtualization hardware (BIOS setting on newer CPU's).  I have that capability on my CPU, and so far I haven't noticed a difference... maybe just very slightly kvm is faster.  Even so, VirtualBox is much *smoother*, especially with the mouse!

---

