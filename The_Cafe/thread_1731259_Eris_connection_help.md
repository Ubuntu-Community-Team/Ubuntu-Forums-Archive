---
title: "Eris connection help"
date: 2011-04-16
forum: The Cafe
---

### Post by Super_Dork_42 on 2011-04-16
I have a problem. I have a htc droid eris that won't connect. My mom's computer runs kubuntu 10.10 my HTC Droid Eris won't connect to it at all. I don't know what to do. I have even tried going into recovery mode ant using the USB-Ms toggle and the computer won't recognise it and the phone will not recognise that it is plugged into the computer at all either. Before my computer died, it was able to connect and I was running ubuntu 10.10. Any ideas?

---

### Post by pi3.1415926535... on 2011-04-16
Is it recognized as a drive in Nautilus?

---

### Post by Super_Dork_42 on 2011-04-16
Nope, not at all.

---

### Post by cariboo on 2011-04-17
What does:

```
dmesg | tail -n10
```

tell you when you plug your device in?

---

### Post by Super_Dork_42 on 2011-04-17
> **cariboo907 said:**
> What does:

```
dmesg | tail -n10
```tell you when you plug your device in?

Do I put that in on the device or the computer?
EDIT : I tried it on the computer first and got the following :
```
[183241.440048] usb 4-2: device descriptor read/64, error -71
[183241.668042] usb 4-2: device descriptor read/64, error -71
[183241.884047] usb 4-2: new full speed USB device using uhci_hcd and address 3
[183242.004281] usb 4-2: device descriptor read/64, error -71
[183242.172064] hub 4-0:1.0: unable to enumerate USB device on port 2
[183242.412092] usb 1-8: new high speed USB device using ehci_hcd and address 15
[183242.562254] scsi12 : usb-storage 1-8:1.0
[183243.563351] scsi 12:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[183243.569430] sd 12:0:0:0: Attached scsi generic sg3 type 0
[183243.584684] sd 12:0:0:0: [sdc] Attached SCSI removable disk
```But in the device notifier it still doesn't show up or anything.
EDIT 2 : grr, I had a little hunch and tried it in another port and it works. I guess that particular port hates my phone for some reason.

---

