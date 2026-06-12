---
title: "Wireless does not enable"
date: 2008-08-06
forum: System76 Support
---

### Post by Controls_Nut on 2008-08-06
Hello all,

Didn't expect to have to post again so quickly, but I have a new unique problem. My wireless does not work (Serval Performance), it simply doesn't find any wireless networks. I right click on the networking icon and "enable wireless" is grayed out, doesn't seem like it is enabled. I have had the wireless turned off over the past couple of days, but when I flipped the switch back over to "on" I get nothing.

---

### Post by Controls_Nut on 2008-08-06
Never mind,

Apparently disabling the wireless in Windows XP (I've dual booted) makes it difficult for the Linux side to enable the wireless. After enabling the wireless in windows and rebooting to linux, it works just fine.

---

### Post by pauper on 2008-08-06
Post the ouput:

```
lshw -C network
lsmod
ifconfig
iwconfig
cat /etc/network/interfaces 
cat /etc/resolv.conf
```

Try connecting manually (change "eth1" to "wlan0" or other to meet wireless
interface on your machine; change linksys to anything "iwlist" finds):

```
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwlist scan
sudo iwconfig eth1 essid "linksys"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
ping -c 5 www.yahoo.com
```

---

### Post by thomasaaron on 2008-08-07
Yes, you are correct. The windows driver for the wireless switch seems to affect the switch's actual firmware.

You gotta love it.

---

