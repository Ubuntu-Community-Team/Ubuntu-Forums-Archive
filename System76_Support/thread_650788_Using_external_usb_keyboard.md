---
title: "Using external usb keyboard"
date: 2007-12-26
forum: System76 Support
---

### Post by ajlewis2 on 2007-12-26
I tried a usb keyboard with my Darter with Gutsy installed.  The keyboard works for a while and then stops working.  I unplug and replug it in and it works again for a while.

Do I have to have a special udev rule like for persistent storage?  

Here is the syslog when I plug it in:
Dec 26 20:00:27 hopalong kernel: [  948.284000] usb 1-1: new full speed USB device using uhci_hcd and address 4
Dec 26 20:00:27 hopalong kernel: [  948.456000] usb 1-1: configuration #1 chosen from 1 choice
Dec 26 20:00:27 hopalong kernel: [  948.460000] hub 1-1:1.0: USB hub found
Dec 26 20:00:27 hopalong kernel: [  948.464000] hub 1-1:1.0: 3 ports detected
Dec 26 20:00:27 hopalong kernel: [  948.780000] usb 1-1.1: new full speed USB device using uhci_hcd and address 5
Dec 26 20:00:28 hopalong kernel: [  948.916000] usb 1-1.1: configuration #1 chosen from 1 choice
Dec 26 20:00:28 hopalong kernel: [  948.924000] input: NMB Dell USB 7HK Keyboard as /class/input/input9
Dec 26 20:00:28 hopalong kernel: [  948.924000] input: USB HID v1.00 Keyboard [NMB Dell USB 7HK Keyboard] on usb-0000:00:1d.0-1.1
Dec 26 20:00:28 hopalong kernel: [  948.932000] input: NMB Dell USB 7HK Keyboard as /class/input/input10
Dec 26 20:00:28 hopalong kernel: [  948.932000] input,hiddev96: USB HID v1.00 Device [NMB Dell USB 7HK Keyboard] on usb-0000:00:1d.0-1.1
Dec 26 20:00:28 hopalong kernel: [  949.032000] usbcore: registered new interface driver xpad
Dec 26 20:00:28 hopalong kernel: [  949.032000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6

Thanks,
Anita

---

### Post by palintheus on 2007-12-27
Hmm I use a usb keyboard for hours when gaming with no issues on my daru2.

---

### Post by ajlewis2 on 2007-12-27
> **palintheus said:**
> Hmm I use a usb keyboard for hours when gaming with no issues on my daru2.

Are you using Gutsy?  This could be the keyboard is bad, too.  It is one I found at work--a Dell.

---

### Post by palintheus on 2007-12-27
Yes, Im using gutsy.

---

### Post by ajlewis2 on 2007-12-27
Thanks, palintheus.

I found a bug report where others are experiencing this; so I may be in the same situation.  Odd that you don't experience it and that I do.  I'll have to try the keyboard in other scenarios like previous Ubuntu, other machine etc.  Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153468](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153468)

---

### Post by thomasaaron on 2007-12-27
You and Palintheus are using two different Darters. Palintheus' is the daru2, ajlewis2's is the daru1 (white darter). The two machines are quite different in a number of ways.

Looks like that bug report has gone idle.

Can you post relevant output from: cat /var/log/messages after the next freeze?

---

