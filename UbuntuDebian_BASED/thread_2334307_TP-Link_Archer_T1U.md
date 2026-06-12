---
title: "TP-Link Archer T1U"
date: 2016-08-18
forum: Ubuntu/Debian BASED
---

### Post by scorpvk on 2016-08-18
Hello.
Please help deal with installing the driver for the Wi-Fi Adapter TP-Link Archer T1U. I'm new to Linux, so I can do something wrong. Download Driver for Linux with TP-Link off-site ([http://www.tp-linkru.com/download/Archer-T1U.html#&#1044;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088;](http://www.tp-linkru.com/download/Archer-T1U.html#&#1044;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088;)). Installation is carried out according to the instructions. After checking the lsmod, modules are loaded. A check via lsusb determined only by PID device. Kernel version 3.13.0-93-generic Help please understand.

---

### Post by chili555 on 2016-08-18
Please run and post:```
lsusb
dmesg | grep mt76
```What is the name of the driver that you compiled and is now loaded?

---

### Post by scorpvk on 2016-08-18
```

root@A7T:/home/ivan# lsusb
Bus 001 Device 004: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 003: ID 2357:0105  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@A7T:/home/ivan# 
root@A7T:/home/ivan# dmesg | grep mt76
root@A7T:/home/ivan#

```

It seems I have the driver is not loaded

---

### Post by chili555 on 2016-08-19
Your very new device hasn't a driver yet. As I see it, there are three possibilities:

# Return the device for a fully supported out of the box item; or

# Email TP-Link and tell them that their driver won't compile* on kernel version 4.4 and ask them for a newer driver; or

# Build the most apparent driver, mt7610u**, and try to force the usb.id into it. It may work, it may partially work or it may not work at all.

What is your choice? I will be happy to assist.

*For compile errors, please see: [http://paste.ubuntu.com/23070523/](http://paste.ubuntu.com/23070523/)

**[https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes) (amend os/linux/mt7610u_sta.mod.c)

---

### Post by scorpvk on 2016-08-19
> **chili555 said:**
> Your very new device hasn't a driver yet. As I see it, there are three possibilities:

# Return the device for a fully supported out of the box item; or

# Email TP-Link and tell them that their driver won't compile* on kernel version 4.4 and ask them for a newer driver; or

# Build the most apparent driver, mt7610u**, and try to force the usb.id into it. It may work, it may partially work or it may not work at all.

What is your choice? I will be happy to assist.

*For compile errors, please see: [http://paste.ubuntu.com/23070523/](http://paste.ubuntu.com/23070523/)

**[https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes) (amend os/linux/mt7610u_sta.mod.c)

My kernel version
```

root@A7T:/home/ivan# uname -a
Linux A7T 3.13.0-93-generic #140-Ubuntu SMP Mon Jul 18 21:20:08 UTC 2016 i686 athlon i686 GNU/Linux
root@A7T:/home/ivan#

```


Maybe try to compile the driver for my kernel

---

### Post by chili555 on 2016-08-19
> **scorpvk said:**
> My kernel version
```

root@A7T:/home/ivan# uname -a
Linux A7T 3.13.0-93-generic #140-Ubuntu SMP Mon Jul 18 21:20:08 UTC 2016 i686 athlon i686 GNU/Linux
root@A7T:/home/ivan#

```


Maybe try to compile the driver for my kernelIn your original post, you said you downloaded and built Archer's driver. Did it not go well? Were there errors?

---

### Post by scorpvk on 2016-08-19
> **chili555 said:**
> In your original post, you said you downloaded and built Archer's driver. Did it not go well? Were there errors?

I do as instructed make and then bash load.sh
[ATTACH]270753[/ATTACH]

---

### Post by chili555 on 2016-08-19
Your attachment shows quite a few warnings but so far no errors. It doesn't continue all the way to the end. Isn't there more?

---

### Post by scorpvk on 2016-08-19
> **chili555 said:**
> Your attachment shows quite a few warnings but so far no errors. It doesn't continue all the way to the end. Isn't there more?

reload

---

### Post by chili555 on 2016-08-19
At the end, we see:> ra0: ERROR while getting interface flags: No such deviceDid the driver actually load?```
lsmod | grep mt7650u_sta 
```Was some other interface created if not ra0?```
iwconfig
```Any clues in the log?```
dmesg | grep mt76
```

---

### Post by scorpvk on 2016-08-19
> **chili555 said:**
> At the end, we see:Did the driver actually load?```
lsmod | grep mt7650u_sta 
```Was some other interface created if not ra0?```
iwconfig
```Any clues in the log?```
dmesg | grep mt76
```

in attach
[ATTACH]270756[/ATTACH]

---

### Post by chili555 on 2016-08-20
That looks awful! I think we are basically at the same point except:

# Return the device for a fully supported out of the box item; or

# Email TP-Link and tell them that ***their driver does compile on your kernel version but throws many warnings and errors and doesn't actually work*** and ask them for a newer driver; or

# Build the most apparent driver, mt7610u, and try to force the usb.id into it. It may work, it may partially work or it may not work at all. It may throw the same or different warnings and errors.

What is your choice? I will be happy to assist.

---

### Post by scorpvk on 2016-08-20
> **chili555 said:**
> That looks awful! I think we are basically at the same point except:

# Return the device for a fully supported out of the box item; or

# Email TP-Link and tell them that ***their driver does compile on your kernel version but throws many warnings and errors and doesn't actually work*** and ask them for a newer driver; or

# Build the most apparent driver, mt7610u, and try to force the usb.id into it. It may work, it may partially work or it may not work at all. It may throw the same or different warnings and errors.

What is your choice? I will be happy to assist.

I have written in support of the TP-Link. I was told that other drivers do not have. Asked to look at the site chipset manufacturer [http://www.mediatek.com/en/downloads1/downloads/](http://www.mediatek.com/en/downloads1/downloads/)
Even suggested that the chipset used Mediatek MT7610U
I downloaded the driver, but I do not know how to install it, could you help me?

---

### Post by scorpvk on 2016-08-20
The instructions found more links, maybe it will help?
[http://www.tp-link.com/en/faq-1076.html](http://www.tp-link.com/en/faq-1076.html)
[https://github.com/lixz789/mt7610u_wifi_sta_v3002_dpo_20130916](https://github.com/lixz789/mt7610u_wifi_sta_v3002_dpo_20130916)

---

### Post by chili555 on 2016-08-20
In my opinion, the method that has the best chance is the github. First, blacklist the other drivers you built:```
sudo -i
echo "blacklist mt7650u_sta_net"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist mt7650u_sta"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot.

Now, with a temporary working internet connection by ethernet, tether or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lixz789/mt7610u_wifi_sta_v3002_dpo_20130916.git
cd mt7610u_wifi_sta_v3002_dpo_20130916
make
```If and only if the 'make' ends without an error (warnings are OK), then proceed:```
sudo make install
sudo modprobe mt7650u_sta
```Post back any errors or problems.

---

### Post by scorpvk on 2016-08-20
> **chili555 said:**
> In my opinion, the method that has the best chance is the github. First, blacklist the other drivers you built:```
sudo -i
echo "blacklist mt7650u_sta_net"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist mt7650u_sta"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot.

Now, with a temporary working internet connection by ethernet, tether or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lixz789/mt7610u_wifi_sta_v3002_dpo_20130916.git
cd mt7610u_wifi_sta_v3002_dpo_20130916
make
```If and only if the 'make' ends without an error (warnings are OK), then proceed:```
sudo make install
sudo modprobe mt7650u_sta
```Post back any errors or problems.

The result of the attachment
[ATTACH]270776[/ATTACH]

---

### Post by scorpvk on 2016-08-21
Bump

---

### Post by chili555 on 2016-08-21
Looks pretty good. Warnings but no errors. Does it connect? Any clues in the log?```
lsmod | grep mt76
dmesg | grep mt76
```

---

### Post by scorpvk on 2016-08-21
> **chili555 said:**
> Looks pretty good. Warnings but no errors. Does it connect? Any clues in the log?```
lsmod | grep mt76
dmesg | grep mt76
```

```

root@A7T:/home/ivan# lsmod | grep mt76
root@A7T:/home/ivan# dmesg | grep mt76
root@A7T:/home/ivan# 

```

---

### Post by chili555 on 2016-08-21
What is the result of:```
sudo modprobe mt7650u_sta
lsmod | grep mt76
dmesg | grep mt76
modinfo mt7650u_sta | grep 0105
```

---

### Post by scorpvk on 2016-08-21
> **chili555 said:**
> What is the result of:```
sudo modprobe mt7650u_sta
lsmod | grep mt76
dmesg | grep mt76
modinfo mt7650u_sta | grep 0105
```

```

root@A7T:/home/ivan# modprobe mt7650u_sta
root@A7T:/home/ivan# lsmod | grep mt76
mt7650u_sta           868387  0 
root@A7T:/home/ivan# dmesg | grep mt76
root@A7T:/home/ivan# modinfo mt7650u_sta | grep 0105
alias:          usb:v2357p0105d*dc*dsc*dp*ic*isc*ip*in*
root@A7T:/home/ivan# 

```

---

### Post by chili555 on 2016-08-21
How about:```
iwconfig
```If there is a wireless interface, wlx-something, then search the log for it:```
dmesg | grep wlx
```...or whatever you found, if not wlx.

---

### Post by scorpvk on 2016-08-21
> **chili555 said:**
> How about:```
iwconfig
```If there is a wireless interface, wlx-something, then search the log for it:```
dmesg | grep wlx
```...or whatever you found, if not wlx.

```

root@A7T:/home/ivan# iwconfig
wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 98:FC:11:EB:C7:51   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:91  Invalid misc:709   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


rename5   Ralink STA  
          
root@A7T:/home/ivan# dmesg | grep rename5
[ 6582.572962] systemd-udevd[7355]: renamed network interface ra0 to rename5



```

---

### Post by chili555 on 2016-08-21
> wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 98:FC:11:EB:C7:51   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:91  Invalid misc:709   Missed beacon:0You seem to have a perfectly good wireless device that's connected and working. Why do you need the Archer?

In any event, I think we have done all we can do. We are unable to find a working driver of any kind.

---

### Post by scorpvk on 2016-08-21
> **chili555 said:**
> You seem to have a perfectly good wireless device that's connected and working. Why do you need the Archer?

In any event, I think we have done all we can do. We are unable to find a working driver of any kind.

I work all the devices on the IEEE 802.11n. I wish that would laptop worked also on the IEEE 802.11n

---

### Post by scorpvk on 2016-08-21
I tried also to install the driver through ndisgtk, but it did not help
The device detected: yes

---

### Post by jeremy31 on 2016-08-21
Please remove anything installed using ndiswrapper and see the wireless script link in my signature, post the results

---

### Post by scorpvk on 2016-08-21
> **jeremy31 said:**
> Please remove anything installed using ndiswrapper and see the wireless script link in my signature, post the results

[ATTACH]270795[/ATTACH]

---

### Post by praseodym on 2016-08-21
Try this linux driver instead (of course, uninstall the wrapper)


[http://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver](http://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver)
From here:

[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

---

### Post by jeremy31 on 2016-08-21
*Thread moved to **Ubuntu/Debian BASED**.*
This is the correct forum for questions concerning Zorin
From what I have seen, praseodyms answer should work if you can find a way to keep the ra0 interface from being renamed to rename?- last time it was rename5 in post 23

---

### Post by scorpvk on 2016-08-22
> **praseodym said:**
> Try this linux driver instead (of course, uninstall the wrapper)


[http://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver](http://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver)
From here:

[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

I installed the driver on the adapter still does not work. The result of the attachment
[ATTACH]270800[/ATTACH]
What's next?

---

### Post by scorpvk on 2016-08-22
> **jeremy31 said:**
> *Thread moved to **Ubuntu/Debian BASED**.*
This is the correct forum for questions concerning Zorin
From what I have seen, praseodyms answer should work if you can find a way to keep the ra0 interface from being renamed to rename?- last time it was rename5 in post 23

I do not know how to rename an interface

---

### Post by jeremy31 on 2016-08-22
That driver doesn't seem to mind the rename but it is receiving a weak signal so you may need to be closer to the router in order to connect

---

### Post by scorpvk on 2016-08-22
> **jeremy31 said:**
> That driver doesn't seem to mind the rename but it is receiving a weak signal so you may need to be closer to the router in order to connect

The adapter does not even lit lamp activity.
How to rename an interface back to ra0?

---

### Post by jeremy31 on 2016-08-22
Use a text editor to edit /etc/default/grub and add
```
net.ifnames=1 biosdevname=0
```
To the line that starts with ```
GRUB_CMDLINE_LINUX_DEFAULT=
```

Mine now is just ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

So if I changed it to stop a rename it would be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=1 biosdevname=0"
```
Save and exit editor then
```
sudo update-grub
```

reboot

---

### Post by scorpvk on 2016-08-22
> **jeremy31 said:**
> Use a text editor to edit /etc/default/grub and add
```
net.ifnames=1 biosdevname=0
```
To the line that starts with ```
GRUB_CMDLINE_LINUX_DEFAULT=
```

Mine now is just ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

So if I changed it to stop a rename it would be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=1 biosdevname=0"
```
Save and exit editor then
```
sudo update-grub
```

reboot

I found.
I just deleted a file from the folder /etc/udev/rules.d

---

