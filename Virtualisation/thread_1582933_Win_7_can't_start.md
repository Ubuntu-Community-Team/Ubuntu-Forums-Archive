---
title: "Win 7 can't start"
date: 2010-09-27
forum: Virtualisation
---

### Post by satimis on 2010-09-27
Hi folks,

Host - Ubuntu 10.04 64 bit
VM - Win 7 64 bit (copied from the old HD)
VBox - Version 3.2.8 r64453

SATA Port 0

I install a new HD on the virtural machine and copy a win7.vdi to this machine.  Create a new VM on Win7.  But Win7 can't start complaining
```

The virtual machine window is optimized to work in 32 bit color mode but the virtual display is currently set to 24 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color mode to see if this message disappears or you can simply disable the message now if you are sure the required color mode (32 bit) is not available in the guest OS.

```

I already select 32 bit color on settings.  Then I run "Repair Mode".  After finish Win 7 still can't start

The old HD also running Ubuntu 10.04 64 bit as host.  The only difference is;
old HD - system ext3
new HD - system ext4

Please help

TIA

B.R.
satimis

---

### Post by Hoopz on 2010-09-27
I was able to click ok past this error and keep installing w7.

---

### Post by satimis on 2010-09-27
Hi folks,

Problem solved as follow;

Settings -> Storage 
Storage Tree;
Put .vdi image under IDE Controller NOT SATA Controller.

Now Win7 starts

Thanks

B.R.
satimis

---

