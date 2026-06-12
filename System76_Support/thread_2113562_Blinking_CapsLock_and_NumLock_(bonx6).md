---
title: "Blinking CapsLock and NumLock (bonx6)"
date: 2013-02-07
forum: System76 Support
---

### Post by Ayanzo on 2013-02-07
So This has happened to me three times in the span of 2 weeks since receiving my bonobo extreme. The symptoms where the same in all three cases in that the system essentially refuses to respond, and the numlock and capslock lights pulse in unison. From what I've heard, this is a hardware problem, or a software problem depending on who you asked. Since I didn't change any driver or kernel settings, I'd like to wonder what the cause could this given I had a good amount of code loss for half a day and I'm pretty unhappy.

---

### Post by kurt18947 on 2013-02-07
Others will respond if I'm incorrect but I think that indicates a kernel panic.  Cause?  I don't really know.  I've seen it on an old machine and a reboot fixed it.  A new machine, especially from System76 certainly should not do that.

---

### Post by tgalati4 on 2013-02-07
New machines that have been shipped tend to have loose connections.  Although a pain, it's helpful to reseat connections that are easy to access.  Some connections require pulling the machine apart.  So, pull the panels that are easy to access and reseat whatever components that you can reach.  Check /var/log/syslog for any messages.

Kernel panics tend to happen when something on the PCI bus gets disconnected.  It's also possible that you have a defective motherboard.  Because of the hotplug nature of USB, you just loose functionality, rather than crash the kernel if it's a loose USB device.

---

### Post by Ayanzo on 2013-02-07
A hard K-panic? I'd expect some kind of indicator on the syslog but there is none. I'm unaware that by default the numlock and capskey lights would blink since I've never seen that on other hardware.

I'm still thinking it might be a hardware issue. I was forced to open it up at work to re-seat the hard-drives which already looked quite secure.

---

### Post by CharlesA on 2013-02-07
> **kurt18947 said:**
> Others will respond if I'm incorrect but I think that indicates a kernel panic.  Cause?  I don't really know.  I've seen it on an old machine and a reboot fixed it.  A new machine, especially from System76 certainly should not do that.

+1. If you haven't contacted System76 support yet, it would be a good idea to get in contact with them.

---

### Post by tgalati4 on 2013-02-07
I'm not familiar with the exact code that causes the caps lock/num lock key to flash, but I've experienced it with a laptop and a bad (bent) wireless pcmcia card.  If you hold the card, the wireless worked OK.  If you put downward pressure on it, it would crash the PCI bus (since the pcmcia is directly connected to the pci bus) causing a kernel panic and flashing lights.

So I would expect a syslog entry if any other peripheral devices, such as a hard disk had failed, but then you would get a software traceback and more details about the kernel panic.  For a serious hardware problem, you will only get flashing lights.

The upside of working on a computer that freezes randomly is that it forces you to back up your work frequently.  It's an important life lesson--your situation can change in an instant, so be ready for it.

---

### Post by Edward_G_Prentice on 2013-08-29
When a kernel panic happens, does it log any information that can be useful in diagnosing why the kernel panic occurred? If so, where? Since I've had four of these on my bonx7, I'd like to get to the bottom of this issue.

---

