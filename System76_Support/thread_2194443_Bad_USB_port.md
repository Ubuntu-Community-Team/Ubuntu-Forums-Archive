---
title: "Bad USB port?"
date: 2013-12-18
forum: System76 Support
---

### Post by chirpis7 on 2013-12-18
Hi everyone,
I have a Galago UltraPro (galu1) running Ubuntu 13.04. When I plug my Nexus 4 into one of the USB ports (the one next to the card reader), I get a couple dozen instances of Nautilus trying to open its internal storage, and several dialog boxes telling me that it was unable to mount it. If the phone shows up at all after this, its internal storage doesn't show up. It behaves normally with the other ports. Sometimes it behaves normally with the port in question after a restart. Any ideas?

---

### Post by varunendra on 2013-12-20
chirpis7,

Sharing just a guess here -

Many usb chip vendors use mixed hubs (e.g. UCHI+EHCI) in their chips, probably to save money, probably for backwards compatibility, I'm not sure. However, they also implement some sort of 'internal Smart switching' to connect the 'used port' to the fastest available hub. To do so, they obviously use additional circuitry inside the chip to switch the paths of the data lines.

However, this switching is often not as 'smart' as it should be. The 'additional circuitry to rotate the data lines may degrade the quality of link, add unwanted delays etc. Sometimes it even fails to switch the lines within tolerable time limits, causing the connected device fail to be detected or handled correctly. Although this kind of poor handling of USB ports at hardware level is usually found in old systems only, the possibility of something similar happening in your case can't be denied.

You can run "lsusb" to see how many internal 'hubs' you have, and if you see a mixture of different versions (EHCI/OHCI/UHCI/XHCI etc.), it may be what I mentioned above. It can be usually confirmed by making all the ports occupied and observing "lsusb" to see which device gets connected to which hub.

---

### Post by chirpis7 on 2013-12-21
Hi all,
I found a fix for this problem [here]("https://class.coursera.org/androidapps101-001/forum/thread?thread_id=5342"):
```
sudo apt-get install mtp-tools mtpfs
```

---

