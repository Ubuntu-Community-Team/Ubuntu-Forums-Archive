---
title: "Please help. I installed Ubuntu server and I need to connect to a wireless network."
date: 2016-08-12
forum: Server Platforms
---

### Post by fromwin2lin on 2016-08-12
What is the easiest way for me to connect to a wireless network. on Ubuntu server 16.04.1?

---

### Post by wildmanne39 on 2016-08-12
*Thread moved to **Server Platforms**.*

---

### Post by Geoffrey_Arndt on 2016-08-13
[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by darkod on 2016-08-13
I don't think there is any plug-n-play wifi adapter for ubuntu server because the network config is done on the command line (and in /etc/network/interfaces).

Assuming your adapter is recognized correctly by the OS, try something like this:
[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal)
[http://askubuntu.com/questions/521188/setting-up-wireless-wpa2-on-ubuntu-server-14-04](http://askubuntu.com/questions/521188/setting-up-wireless-wpa2-on-ubuntu-server-14-04)

You can check if the adapter is recognized by checking all network cards detected (that will also give you the interface name that you need to use):
```
sudo lshw -short | grep network
```

---

### Post by SeijiSensei on 2016-08-13
Is there a reason why you cannot simply use an Ethernet cable and make a wired connection to your router?  "Servers" generally are not mobile and don't rely on wireless connections as a result. Plug in the cable at both ends and give the server a [static IP address]("https://help.ubuntu.com/lts/serverguide/network-configuration.html#ip-addressing").

---

### Post by fromwin2lin on 2016-08-13
Thanks! That helped a lot!

---

