---
title: "Can not run an OS in VB"
date: 2013-12-29
forum: Virtualisation
---

### Post by uwe-bungto on 2013-12-29
I have a new to me Lenovo Thinkpad X201 with an i5 M540 cpu which is a 64 bit 2 core 4 thread running at 2.53 GHz . I have tired to install Windoze 7 64 from my dell box I get a warning that I am trying to install a 64bit OS on a 32 bit CPU. I get the same warning with FreeBSD and linux mint

Any suggestions??
Paul

---

### Post by QIII on 2013-12-29
Hello!

Is VT-x enabled in your BIOS/EFI?  Does your BIOS/EFI have settings for 32/64bit in VT-x?

When you set up the machines, were you sure to make them 64 bit?

---

### Post by KillerKelvUK on 2013-12-30
The host OS is 64bit right?

---

### Post by uwe-bungto on 2013-12-30
> **QIII said:**
> Hello!

Is VT-x enabled in your BIOS/EFI?  Does your BIOS/EFI have settings for 32/64bit in VT-x?

When you set up the machines, were you sure to make them 64 bit?

Thanks
That was it. Enabled VT-x ready to windoze.;)

---

