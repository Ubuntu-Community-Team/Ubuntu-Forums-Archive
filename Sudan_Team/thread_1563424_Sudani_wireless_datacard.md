---
title: "Sudani wireless datacard"
date: 2010-08-29
forum: Sudan Team
---

### Post by Altahir23 on 2010-08-29
Hi guys
I'm a new user, and I'm asking for help with using sudani mDSL Wireless Data Card. NOT the usb one. I inserted my zte wireless data card and then i typed lspci command and this is wht i got:
 
 
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:00.0 USB Controller: NEC Corporation USB (rev 43)
06:00.1 USB Controller: NEC Corporation USB (rev 43)
 
so pleeeeeeeeeeeeez help

---

### Post by zero-n on 2010-08-31
Alslam 3lekom, [Altahir23]("http://ubuntuforums.org/member.php?u=1137802")

insert your zte data card & then run this command
```
sudo lspcmcia
```

& paste you ouput here

---

