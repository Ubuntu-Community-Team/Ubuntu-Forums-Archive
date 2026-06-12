---
title: "Trying to restore, hopeless for wireless drivers"
date: 2010-03-10
forum: System76 Support
---

### Post by Piggah on 2010-03-10
Hi there. I recently got completely fed up with ubuntu 9.10 and the newer versions. Was having terrible times with wireless etc after my first upgrade from what came on my system.

I have a panp4n.

I just downgraded back to 8.10 in an effort to get back to what came on my computer and when everything worked *perfectly* and i was in love with my system. Ive followed all of the instructions properly on the knowledge base for a restore and driver installation, however i simply /cannot/ get my notebook to recognize wifi networks. im pretty sure the wireless driver is not being installed at all. Ive searched the forums through and through and still cant get it. 

Wireless is the last thing I need to get everything "perfect" again, any thoughts? I really love my system76, but I want to get everything out of it. (at least everything that was working when it came i mean)

---

### Post by Fxy on 2010-03-10
If you load up terminal and then type  **lshw -C network** you can see if your device has been recognized...

If your device has not shown up on the output of the above command you can try **sudo pccardctl ident** to hopefully get some output about the device...

These commands will be able to tell you if your driver/device has been recognized ;)

For more info take a look at this page as it might be of some help to you [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check") ...

---

### Post by thomasaaron on 2010-03-10
> im pretty sure the wireless driver is not being installed at all.

Please run this command from a terminal and let me know the results...

lsmod | grep iwlagn

This will tell us if your driver is loading. Your wireless card is supported by UBUNTU out of the box. If the above command returns output, your driver is being loaded. If not, we can fix that.

Please also right-click your network manager icon and ensure "Enable Wireless Networking" is selected.

You may also have a faulty wireless card. If that turns out to be the case, we need to move this to email.

support...at...system76...dot...com

---

### Post by Piggah on 2010-03-10
it appears the card is recognized...

```
nick@laptop:~$ lsmod | grep iwlagn
iwlagn                113540  0 
iwlcore               107844  1 iwlagn
mac80211              253440  2 iwlagn,iwlcore
cfg80211               37136  3 iwlagn,iwlcore,mac80211
```

```
nick@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:9f:db:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8a:2e:a3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.101 latency=0 module=r8169 multicast=yes

```

whats happening though is that whenever im in the presence of a wireless network its not recognized and i am unable to log on to it.

---

### Post by thomasaaron on 2010-03-11
OK, so your wireless driver is being loaded.

Did you do this?
> Please also right-click your network manager icon and ensure "Enable Wireless Networking" is selected.

What does this mean? Can you *see* the wireless network?
> whats happening though is that whenever im in the presence of a wireless network its not recognized and i am unable to log on to it.

Have you tried other wireless access points?

Please try booting from an Ubuntu 9.10 64-bit live CD and tell me if you have the same problem.

---

### Post by Piggah on 2010-03-11
> **thomasaaron said:**
> OK, so your wireless driver is being loaded.

Did you do this?


What does this mean? Can you *see* the wireless network?


Have you tried other wireless access points?

Please try booting from an Ubuntu 9.10 64-bit live CD and tell me if you have the same problem.

To the former: yes, "enable wireless" is checked. 

to the latter: I just mean that when I'm at known wifi hotspots (coffee shops, etc) or friend's homes with wireless networks, they arent automatically recognized and im not prompted for a password. 

I will burn a 9.10 livecd later today and try that. I'm headed to a friends house with a wireless network where I can test this. 

thanks for much for your help, i really appreciate it.

---

