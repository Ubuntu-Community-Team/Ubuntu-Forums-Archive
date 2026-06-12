---
title: "Ubuntu 17.04 can't connect to internet wirless or wired"
date: 2017-08-06
forum: Virtualisation
---

### Post by vanquishvictor1998 on 2017-08-06
Hi there.

Just installed Ubuntu. The laptop can see the router but just can't establish connection, everything seems to be in order in the setting yet it can't load anything up in firefox

---

### Post by praseodym on 2017-08-06
Hi,

there is a bug in 17.04. Please run these 2 commands and reboot

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by vanquishvictor1998 on 2017-08-06
HI, thanks for the quick reply.

I placed them into terminal and then rebooted the system and now I have no wifi bar in the top right. Also when I go into system settings then to network I get "The system network services are not compatible with this version". I have the most up to date version :confused:. 

What codes should i have got in return?

---

### Post by praseodym on 2017-08-06
Please follow this guide for the wireless script and show the outputs (c/p into a txt file)

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Bewildered_Bob on 2017-08-10
Will those cmds also correct wired connection failure ?

---

### Post by Bewildered_Bob on 2017-08-10
> **praseodym said:**
> Hi,

there is a bug in 17.04. Please run these 2 commands and reboot

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```


I'm a newbie running Ubuntu 17.04 as a "virtual machine" under Virtual Box (Windows 7). 

(1) how is copy/paste done between Win clipboard and Ubuntu terminal ?
(2) is  ** [device]  ** to be entered as shown or is an existing device to be entered instead ?

Thanx.

Bewildered Bob

---

### Post by wildmanne39 on 2017-08-10
*Thread moved to **Virtualisation**.*

---

### Post by praseodym on 2017-08-12
Yes, entered as shown. Just c/p these commands into a txt file. Normally, virtualbox (if used) now can work with c/p or drag/drop txt files

---

