---
title: "Audiobox USB not recognized in fresh 14.04.2 LTS install."
date: 2015-05-21
forum: Ubuntu Studio
---

### Post by smeelkin on 2015-05-21
Hello,

I'm having trouble with the Presonus Audiobox USB. Last time I used it, a year ago or so, it was working perfectly, as in plug and play, but now it is not recognized as an audio device. I'm using a completely fresh install of Ubuntu Studio 14.04.2 LTS 64 bit on an MSI GE60 0NC laptop, no settings have been messed around with. I get this from dmesg when plugging it in:

```

[17210.038753] usb 3-2: new full-speed USB device number 11 using xhci_hcd
[17211.448051] usb 3-2: unable to read config index 0 descriptor/all
[17211.448059] usb 3-2: can't read configurations, error -75
[17211.601570] usb 3-2: new full-speed USB device number 12 using xhci_hcd
[17211.770031] usb 3-2: unable to read config index 0 descriptor/all
[17211.770049] usb 3-2: can't read configurations, error -75
[17211.922932] usb 3-2: new full-speed USB device number 13 using xhci_hcd
[17211.936526] usb 3-2: device descriptor read/all, error -75
[17212.089104] usb 3-2: new full-speed USB device number 14 using xhci_hcd
[17212.105376] usb 3-2: unable to read config index 0 descriptor/all
[17212.105384] usb 3-2: can't read configurations, error -75
[17212.105476] usb usb3-port2: unable to enumerate USB device

```

Any help would be greatly appreciated.

---

### Post by smeelkin on 2015-05-21
I feel so stupid now. It was a faulty cable. Well, to the lone googler in the future, check your cable first.

---

### Post by Vladlenin5000 on 2015-05-21
Please use the thread tools in your original post to mark this one as solved so other will benefit.

---

