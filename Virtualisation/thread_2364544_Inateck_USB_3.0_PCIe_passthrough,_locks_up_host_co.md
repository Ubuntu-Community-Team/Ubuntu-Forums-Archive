---
title: "Inateck USB 3.0 PCIe passthrough, locks up host completely?"
date: 2017-06-24
forum: Virtualisation
---

### Post by KillerKelvUK on 2017-06-24
So I decided to by an Oculus Rift to complement my GTX 1070 which runs in a Win10 KVM/Qemu guest.  I'm at the point where VR works fine but the audio cuts out (actually pauses) for a couple of seconds and does this regularly, reading around this seems likely to be because of USB congestion (am using my ASRock Z97 onboard which is 6x Intel and 2x Asmedia 3.0's and 2x Intel 2.0s).  I've tried every combination of moving the Oculus connections around to try and balance the bandwidth but wasn't satisfied so went and bought an Inateck USB 3.0 PCIe card.

The card passes through to the guest, windows grabs it and loads the drivers and I can happily hotplug usb devices and windows responds.  However when I shutdown the guest one of two scenarios plays out, either the host picks back up the USB card and I continue without incident or the entire host locks and I have no other recourse than a hard power off.  Once I've recovered the host I see nothing in the logs anywhere either host os or libvirt that even hints at a root cause, I do see lots of "^@^@^@^@^@^@^" in syslog which I believe is the point the host dies but then recovery is normal.  On the host the Inateck card works fine so I'm struggling to put this down to a defective PCIe card.

Anyone got any similar stories or recommendations as to how I can attack this problem?

Thanks,

K

---

### Post by KillerKelvUK on 2017-06-26
So directly from Inateck...

> 
[FONT=arial]With regard to your problem, we normally don’t recommend Linux or dual system users to use our card since there might exist compatibility issue. [/FONT]
[FONT=arial] [/FONT]
[FONT=arial]We sincerely apologize for the inconvenience caused. If you need any further assistance from us at Inateck, please feel free to contact us.[/FONT]


RMA'd the card.

---

