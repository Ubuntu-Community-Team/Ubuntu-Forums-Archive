---
title: "Tascam US-122 Installation Error"
date: 2009-06-24
forum: Ubuntu Studio
---

### Post by RyanfromtheShire on 2009-06-24
I searched around and didn't find this specific error in previous threads.

I'm using this guide:

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

I get to step 6, and I get this error:

```

ryan@Ryan:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ryan@Ryan:~$ sudo fxload -s ~ /usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/002/006
EOF without EOF record!
ryan@Ryan:~$ 

```

I've installed everything up to this point, without any errors.

---

