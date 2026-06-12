---
title: "trying to get dwa-182 working"
date: 2024-02-16
forum: Ubuntu/Debian BASED
---

### Post by d3vestator on 2024-02-16
my d link dwa-182 does not seem to be working properly on my vm i am running. it shows up, however i think there is something wrong with the linux drivers installed

```



 *-network
       description: Wireless interface
       physical id: 8
       bus info: usb@1:1
       logical name: wlan0
       serial: c6:a7:df:e0:aa:2f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822bu driverversion=6.5.0-kali3-amd64 firmware=N/A link=no multicast=yes wireless=IEEE 802.11





```


for FYI, this is kali, however i assume troubleshooting would be the same because they both use debian

---

### Post by d3vestator on 2024-02-18
my network adapter is being recognized by lsusb, has linux drivers by lshw -C network. it show the available networks and when i click on mine, it will spin and spin and then never work

---

### Post by jeremy31 on 2024-02-20
Please see the wireless script link in my signature and post results

---

### Post by d3vestator on 2024-02-20
just FYI - for this troubleshooting i am using kali, instead ubuntu. not sure if it would really make a big difference since they have the same commands, but im also running on virtualbox with NAT. i can switch to ubuntu if we need to

[https://dpaste.com/EPUD88FYK](https://dpaste.com/EPUD88FYK)

---

### Post by howefield on 2024-02-20
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by d3vestator on 2024-02-20
ok, wasnt sure where to put this question

---

### Post by morrownr on 2024-02-21
Hi d3vestator,

> does not seem to be working properly on my vm i am running

Running usb wifi adapters with a vm can be a challenge and the solution, if there is one, is specific to the vm you are running so seeking help with the forums at the vm may be a good option. I don't do vm's so I can't help much with that but you were not getting many replies so I thought I would help however I can.

> driver=rtw_8822bu driverversion=6.5.0-kali3-amd64

Generally when I see "kali", it is because someone is learning how to or is doing security analysis or pen testing so the first thing I think when I see "rtw_8822bu" is this is not a good match. 

If you are doing security analysis/pen testing or other monitor mode operations, you might want to seek out an adapter that does this well. I have a github site helps folks figure out what adapters may be best for their use case:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

### Post by d3vestator on 2024-02-21
Hey morrownr, thanks you for replying, Greatly appreciated. yea im trying get this to work in kali, and i decided to try this on ubuntu on my host, knowing i know how to remove and install linux drivers, and it does work on my laptop with ubuntu without a vm. so maybe it has something to do with a configuration in the vm or something, because i have the same driver installed for both. unlike ubuntu wifi adapter, my wifi adapter in kali is being recongized and i can see the available networks, but it just keep spinning

do you think it might have something with the actual wifi adapter for the distribution because what you said, kali is more analysis and pen testing. usually for kali you would want a monitor wifi adapter, not a managed but i feel like it should still work regardless

---

