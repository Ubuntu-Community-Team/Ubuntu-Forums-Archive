---
title: "Intel Centrino Advanced-N 6205 suddenly stopped working"
date: 2018-02-07
forum: Ubuntu/Debian BASED
---

### Post by asmox79 on 2018-02-07
Hello, today my WiFi card just stopped working. Since I use two OSes, Windows and Linux, I checked if it's down in Windows. Unfortunately it is, which makes me concerned it may be the break down of hardware. I was following this topic about the same WiFi card:
[https://ubuntuforums.org/showthread.php?t=2018477](https://ubuntuforums.org/showthread.php?t=2018477)

My case is quite different, but let me provide the same kind of information to make examination easier:

**1) Machine brand and model:**
Dell Latitude E6520 Core i7 2740QN 2,4 GHz
[B]
2) Wireless brand, model and wireless chipset:[/B]
```
$ lspci -nn | grep -i Net00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)

```

[B]3) Check interface
[/B]```
$ sudo ifconfig wlan0wlan0     Link encap:Ethernet  HWaddr 60:67:20:e0:9e:04  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

**4) Check for modules:**
```
$ lsmod | grep iwlagn
(returns nothing)
```

**5) Kernel boot messages:**
```
$ dmesg | grep -i iwl[    6.322128] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    6.322395] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[    6.331673] iwlwifi 0000:03:00.0: firmware: direct-loading firmware iwlwifi-6000g2a-6.ucode
[    6.331789] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    6.368597] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    6.368600] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS disabled
[    6.368601] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING disabled
[    6.368603] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    6.368728] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    6.368953] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[    6.381855] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```

**6) Network configuration**
```
$ sudo lshw -C network  *-network                                                                                                                                               
       description: Ethernet interface                                                                                                                    
       product: 82579LM Gigabit Network Connection                                                                                                        
       vendor: Intel Corporation                                                                                                                                
       physical id: 19                                                                                                                                          
       bus info: pci@0000:00:19.0                                                                                                                               
       logical name: eth0                                                                                                                                                                               
       version: 04                                                                                                                                                                                                  
       serial: d4:be:d9:6f:60:44                                                                                                                                                                                    
       size: 100Mbit/s                                                                                                                                                                                              
       capacity: 1Gbit/s                                                                                                                                                                                                     
       width: 32 bits                                                                                                                                                                                                             
       clock: 33MHz                                                                                                                                                                                                                                  
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-3 ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:e6700000-e671ffff memory:e6780000-e6780fff ioport:5040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 60:67:20:e0:9e:04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-4-amd64 firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e6600000-e6601fff
```

**7) Scan for networks:**
```
$ sudo iwlist scanlo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


eth0      Interface doesn't support scanning.
```

**8) Debian version:**
```
$ lsb_release -daNo LSB modules are available.
Distributor ID: Debian
Description:    Debian GNU/Linux 8.7 (jessie)
Release:        8.7
Codename:       jessie



```

**9) Kernel / architecture**
```
$ uname -mr3.16.0-4-amd64 x86_64



```

10) rfkill and another informations:
```
$ sudo rfkill list all0: dell-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: yes
2: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes



```

```
$ cat /etc/network/interfaces# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback



```

```
$ cat /etc/NetworkManager/NetworkManager.conf[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false



```

So, is there any chance my WiFi card can work any more?

---

### Post by asmox79 on 2018-02-07
@SOLVED:
I have found I surely must have turned off my card by accident with a switch on my laptop. Please forgive me this silly miseeing and delete this thread

---

### Post by wildmanne39 on 2018-02-07
You have a hardblock and a softblock, for the softblock try:
```
sudo modprobe -rv dell-laptop
```
do not reboot your computer then find the switch or key combination that turns your wifi on because it shows the switch is off.

Check to see if the hardblock says no by running:
```
rfkill list all
```

If it still does not connect please click on the wireless script in my signature and paste thee results here.

What Ubuntu version are using?

---

### Post by wildmanne39 on 2018-02-07
We do not delete threads!

Glad you got it working.

---

