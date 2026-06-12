---
title: "Network Controller Qualcoom Atheros QCA6174 not working"
date: 2019-01-21
forum: Ubuntu/Debian BASED
---

### Post by yanisdb on 2019-01-21
Hi, 
I am not so knew to Linux and I used many Linux distribution, but last week, for my new computer (Samsung Galaxy Book 12), I chose to install Ubuntu and I faced a few problems but I could fixed them all. Expect this one : the WiFi isn't working. I've made some digging and found a few solutions which didn't work. So here are some information and feel free to ask for anything, I really need to get this working, thank you everyone.

First, it found that I have no wireless network interface :
```

root@kali:/# ifconfig
enx9cebe81da102: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.174  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::e359:2bf6:75f5:436a  prefixlen 64  scopeid 0x20<link>
        ether 9c:eb:e8:1d:a1:02  txqueuelen 1000  (Ethernet)
        RX packets 10409  bytes 4585133 (4.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6367  bytes 966555 (966.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 886  bytes 70087 (70.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 886  bytes 70087 (70.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
```

root@kali:/# iwconfig
lo        no wireless extensions.

enx9cebe81da102  no wireless extensions.

```

So then, i thought that the problem was coming from the drivers for the network card :

```

root@user:/# lspci | grep Net
01:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

```

And running this next command gave me lots of errors, I have no idea what they mean but I think they might be the solutions to all my problems :

```

root@kali:/# dmesg | grep ath
[    6.093310] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    6.095275] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    6.493128] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[    6.493140] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    6.522632] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    6.522635] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    6.523059] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00079-QCARMSWPZ-1 api 6 features wowlan,ignore-otp crc32 fd869beb
[    6.597589] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 20d869c3
[    7.180970] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    7.183964] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    7.184722] ath10k_pci 0000:01:00.0: htt-ver 3.47 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    7.269982] ath: EEPROM regdomain: 0x5f
[    7.269984] ath: EEPROM indicates we should expect a direct regpair map
[    7.269984] ath: invalid regulatory domain/country code 0x5f
[    7.269985] ath: Invalid EEPROM contents
[    7.269990] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[    7.269992] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)

```

Thank you very much to everyone who tries to help, and I'm here to learn so next time I can solve my problems on my own and maybe even help others, so if you feel like explaining in depth the problem and solution I would appreciate it. In any case, thank you again.

---

### Post by jeremy31 on 2019-01-21
What kernel are you using? ```
uname -r
```

---

### Post by yanisdb on 2019-01-21
Wow such a quick answer thank you so much. 
And yeah of course, I just forgot to put it, here you go :
```

root@kali:/home/kali# uname -r
4.15.0-43-generic

```

And, also, just to know, did you find what could be the problems with the dmesg command ? Like would I have been able to found out ?

---

### Post by jeremy31 on 2019-01-21
Moved to Debian/Ubuntu based, if you search google for "ath: invalid regulatory domain/country code 0x5f" you should find a fix from this forum

---

### Post by yanisdb on 2019-01-21
I did everything that was in there and I don't think it is working, or do I need to do something else to set-up the network interface ?
Edit: Wait, I might have missed something, sorry

---

### Post by yanisdb on 2019-01-21
Well thank you, it did indeed work.
But it don't quite understand what was the problem, was is just a forgotten country code like said in the other thread ?

---

