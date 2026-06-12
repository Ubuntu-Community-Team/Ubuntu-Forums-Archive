---
title: "Wireless Access Point?"
date: 2009-01-26
forum: Server Platforms
---

### Post by Lemons on 2009-01-26
During the past few days, I have have been setting up a firewall from an old computer. My plan is to have one input (for wan) and two outputs (for lan and wlan). I have thus far got the firewall to work, DNS, and DHCP (along with the firewall ofcourse). Now, I have been having problems making the wireless card into a access point. I want to know if anybody knows how to do this with the madwifi drivers. _I do not require secuirity_. I live out in the middle of the woods so theres noone going to be stealing my internet. I just want a access point that broadcast and allows usage of the internet.

Its meant for us with a Wii and DS, and ofcourse anything else down the line.

Oh, and some info:

Thanks!
~Kris

---

### Post by Lemons on 2009-01-26
Opps, forgot some info:

iwconfig:
```

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Master  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci:
```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
00:0e.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 10)
_**00:0f.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)**_
00:10.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
00:11.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I tried the basic ath0 with a bridge (br0) and that did not work. I failed at compiling hostapd from source (Though madwifi is compiled from source to work with the server edition). I just need something that makes an access point and connects to the internet!

Any more needed info just ask. I am using **ubuntu server 8.04.2**

---

### Post by Lemons on 2009-01-27
Well, like most problems this was solved with a little more googling... Now the wireless access point is connectable.

Other words, this thread cna be closed/deleted/whatever.

---

