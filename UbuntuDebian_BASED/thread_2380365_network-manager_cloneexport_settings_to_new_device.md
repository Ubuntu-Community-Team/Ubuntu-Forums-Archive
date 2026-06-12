---
title: "network-manager clone/export settings to new device (MAC-address!)"
date: 2017-12-16
forum: Ubuntu/Debian BASED
---

### Post by jkstar1337 on 2017-12-16
Hello,

I am using ubuntu (armbian) 16.04 LTS with network-manager.

I have two Wifi modules on my ASUS tinkerboard and **would like to clone my SD card** and use my configured network settings inside other tinkerboards.

I see that network-manager is writing mac-addresses into the **conf** files, so that means **a new board will not be able to use the settings**. 

How can I change this? (I cannot change the internal wifi mac with macchanger for some reason)

Is there a way to somehow tell network-manager to use wlan0 wlan1 instead of mac-addresses or clone my settings?

Thank you.

---

### Post by chili555 on 2017-12-17
I'd think the far easier way is to simply:```
nmcli dev wifi con "myssid" password "myssidpassword"
```You could put it in /etc/rc.local and it will run at every boot.

---

### Post by DuckHook on 2017-12-17
*Thread moved to **Ubuntu/Debian BASED** as the more appropriate forum.*

---

