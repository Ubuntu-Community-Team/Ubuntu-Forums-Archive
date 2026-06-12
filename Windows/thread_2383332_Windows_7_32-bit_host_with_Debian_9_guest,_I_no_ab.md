---
title: "Windows 7 32-bit host with Debian 9 guest, I no able to open in putty 0.6/07"
date: 2018-01-23
forum: Windows
---

### Post by nandi.debian on 2018-01-23
I have try several different option/setting in network settings (NAT, bridged...) for **virtualbox.** I have try ping all the IP adress i find in cmd and got respons also on typical **192.168x** adress and [B]127.0.0.1

[/B]Everytime i try login via the putty I get no respons until I close sessions or get the message of [B]network error:permission denied

[/B]For internet I have mobile phone **wifi connectet hotspot **which I now cannot access the internet through chrome or other browser, but I have internet because I can download software through Debian and cmd ping google.com and such website.

Also, do I need to have internet/wifi on to connect bridged?

---

### Post by QIII on 2018-01-23
Moved to Windows.

---

### Post by mastablasta on 2018-01-25
in vbox set networking to bridged.

then when in linux run
 ```
ifconfig
```

to see the assigned IP of debian virtual machine

then you can connect to that IP. you might need to add a port when connecting to it. you might also need to open the port to listen to outside connection. for example if you are trying to use SSH, you need to open port for SSH (default 22) in iptables firewall. then you connect by typing propperly setting up the the connection in putty.

from your description it is impossible to know where exactly you got stuck.

also make sure on windows firewall that putty has full access as well as that virtual network in windows if properly configured.

---

### Post by nandi.debian on 2018-01-26
Not sure why, maybe it was old firewall I not knew was install on system. :popcorn:

---

