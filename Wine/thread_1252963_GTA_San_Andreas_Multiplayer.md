---
title: "GTA San Andreas Multiplayer?"
date: 2009-08-29
forum: Wine
---

### Post by DanPaulCiocan on 2009-08-29
Hi, I was wandering if any Multiplayer Mod for San Andreas works with wine? I tried SA-MP, and I get this error when I want to enter in a server:
```
err:seh:setup_exception_record stack overflow 1840 bytes in thread 0024 eip 7ed3c7de esp 01580c00 stack 0x1580000-0x1581000-0x1780000
```I also tried MTA, and it should work: [http://mtavc.com/71.html](http://mtavc.com/71.html)
But I get this errors when I try to start it:
```
fixme:advapi:SetEntriesInAclA 1 0x32ed5c (nil) 0x32ed58
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x197e6cc (nil) 0x197e6c8
fixme:advapi:SetSecurityInfo stub
```I'm running the latest version of wine. I use the proprietary drivers for my Nvidia Geforce 8600 GT. Does anyone know what this errors means, and how can I play on of these Multiplayer Games?
PS: San Andreas is working very well, and it's rated as Gold in wine's database.
Thanks.

EDIT: Debug from SAMP:
```
Exception At Address: 0x7B844673

Registers:
EAX: 0x7B82EE71    EBX: 0x7B8B8FF4    ECX: 0x00000000    EDX: 0x0177FA74
ESI: 0x0177FA74    EDI: 0x01A80478    EBP: 0x0177FA50    ESP: 0x0177F9EC
EFLAGS: 0x00200246

Stack:
+0000: 0x0177FA74   0x00000008   0x0000003C   0x80000100
+0010: 0x00000001   0x00000000   0x7B844673   0x00000002
+0020: 0x7E9C8E20   0x7E9C96B3   0x0177FA24   0x0177FA28
+0030: 0x0177FA2C   0x0177FAB0   0x00000002   0x00000002
+0040: 0x7DB98FF4   0x0177FAC0   0x0177FAE4   0x7DAC59D5
+0050: 0x00000001   0x00138F7C   0x7B84460A   0x01A80478
+0060: 0x0177FA74   0x0177FA80   0x7E9C8D88   0x80000100
+0070: 0x00000001   0x00000002   0x0177FA74   0x7BC94FF4
+0080: 0x077EEF28   0x00000188   0x7E9C8E20   0x7E9C96B3
+0090: 0x01B330A8   0x01B330A8   0x7E9BCB10   0x7E9C8E20
+00A0: 0x7E9C96B3   0x00000000   0x017BE859   0x00138CC0
+00B0: 0x0177FAF4   0xFFFFFFFF   0xFFFFFFFF   0xFFFFFFFF
+00C0: 0x00000000   0x00000000   0x00000001   0xFFFFFFFF
+00D0: 0xFFFFFFFF   0x00000000   0x0177FAD8   0x00000000
+00E0: 0x01B331AC   0x0000001A   0x00000000   0x7BC44701
+00F0: 0x0005CE00   0x000C0000   0x01B33210   0x7BC3474F
+0100: 0x00000040   0x7BC94FF4   0x74757864   0x2E697567
+0110: 0x00676E70   0x0177FB60   0x7BC45BF6   0x01B331C8
+0120: 0x01A80014   0x01B40000   0x00000001   0x7BC94FF4
+0130: 0x00000110   0x01B330A0   0x0177FB44   0x01B331C0

SCM Op: 0x0, L: 0, Dump:
+0000: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0010: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0020: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0030: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0040: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0050: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0060: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0070: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0080: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+0090: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+00A0: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+00B0: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+00C0: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00
+00D0: 00 00 00 00   00 00 00 00   00 00 00 00   00 00 00 00

Game Version: US 1.0
```

---

