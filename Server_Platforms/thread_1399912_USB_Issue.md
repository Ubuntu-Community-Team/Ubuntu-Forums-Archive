---
title: "USB Issue"
date: 2010-02-06
forum: Server Platforms
---

### Post by marco45 on 2010-02-06
I Just upgraded unbuntu server from 8.4 to 9.10 and now USB device are not recognized I got this error msg

Feb  6 09:04:20 atlantis kernel: [   31.952052] usb 2-1: device descriptor read/64, error -110
Feb  6 09:04:21 atlantis kernel: [   32.168052] usb 2-1: new full speed USB device using uhci_hcd and address 3
Feb  6 09:04:36 atlantis kernel: [   47.280050] usb 2-1: device descriptor read/64, error -110
Feb  6 09:04:51 atlantis kernel: [   62.496051] usb 2-1: device descriptor read/64, error -110
Feb  6 09:04:51 atlantis kernel: [   62.712048] usb 2-1: new full speed USB device using uhci_hcd and address 4
Feb  6 09:04:56 atlantis kernel: [   67.733581] usb 2-1: device descriptor read/8, error -110
Feb  6 09:05:01 atlantis kernel: [   72.853542] usb 2-1: device descriptor read/8, error -110
Feb  6 09:05:01 atlantis kernel: [   73.068056] usb 2-1: new full speed USB device using uhci_hcd and address 5
Feb  6 09:05:06 atlantis kernel: [   78.089483] usb 2-1: device descriptor read/8, error -110
Feb  6 09:05:12 atlantis kernel: [   83.209449] usb 2-1: device descriptor read/8, error -110
Feb  6 09:05:12 atlantis kernel: [   83.312073] hub 2-0:1.0: unable to enumerate USB device on port 1


Thank for helping

---

### Post by marco45 on 2010-02-07
This is my Kernel:

2.6.31-19-generic

---

