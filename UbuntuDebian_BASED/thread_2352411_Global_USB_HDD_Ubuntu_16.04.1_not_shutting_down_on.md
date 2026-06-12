---
title: "Global USB HDD Ubuntu 16.04.1 not shutting down on Desktop?"
date: 2017-02-12
forum: Ubuntu/Debian BASED
---

### Post by themacmeister on 2017-02-12
Hi All,

I recently decided to create a UEFI boot ultimate multi-machine live 2TB USB HDD running Ubuntu 16.04.1, booting and running via USB3.0 on my laptop (15" 2012 Retina MacBook Pro) and my Desktop PC (Core i7 2600, Gigabyte B75M-D3H mobo). With the (unexpected) install of Grub into my Apple EFI (sigh), the live HDD works flawlessly on the Macbook Pro (including WiFi now). There are some minor errors at startup, but I put this down to non-standard Apple motherboard design.

Here is where the problem starts... The HDD boots and runs superbly on my Desktop PC, but my USB 3.0 front panel does not turn off USB3.0 on shutdown (during shutdown?), leaving the USB still active, and a flashing underscore, with the computer still ON.

I may need to add a hard poweroff command after a timeout into the shutdown script?

If anyone can help, please post a reply. I have had to hold the power button in to shutdown, and I am worried about corrupting data on the HDD.

Oh, it is a Seagate Expansion Portable Drive, which has EPIC USB3.0 read/write speeds :-)

NOTE: The drive has shutdown successfully before (first boot/trial), so it may be an upgrade run since then...

---

### Post by themacmeister on 2017-02-15
Never mind, the live external has died, I have reformatted and removed GRUB from Apple-EFI :-(

---

