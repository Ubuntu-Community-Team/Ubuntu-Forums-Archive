---
title: "usbip sharing a usb device over network"
date: 2010-10-11
forum: Server Platforms
---

### Post by chrisbay90 on 2010-10-11
Hi,

I am trying to share a usb device over a LAN. I'v found the tool that I think should achieve this for me usbip and im assuming it is at least somewhat supported by ubuntu as it is in the repo's.

I'v installed it on the server and run usbipd -D and thats about as far as I get as im presented with
usbip err: stub_driver.c:  33 (open_sysfs_stub_driver) usbip_common_mod.ko and usbip.ko must be loaded

Now I don't know much about the Linux kernel and modules so that's really a stopping point for me. Could anyone shed some light on how to get this to work? I haven't found anything else on this forum relating to it yet.

More to the point of what i would like to acheive. I have a printer, Brother DCP 130C,  that needs to be shared amoung a group of windows machines. I have available an ubuntu 10.04 server. Now printer sharing via cups works however I have had no luck with scaner sharing as it seems this model is not supported under linux. So i think my only solution is raw USB sharing. Can anyone sujjest how i might achieve this either way?

---

### Post by chrisbay90 on 2010-10-21
bump

---

### Post by bigpapapump on 2011-06-30
you need to run as root.  Either change to root user or run: ```
sudo usbipd -D
```

---

### Post by bigpapapump on 2011-06-30
1. load usbip driver
```
sudo modprobe usbip
```

2. list devices to bind driver
```
sudo usbip_bind_driver --list
```

3. Another way to see list of usb devices:
```
lsusb
```

4. bind driver to usb device:
```
sudo usbip_bind_driver --usbip 2-1
```

---

