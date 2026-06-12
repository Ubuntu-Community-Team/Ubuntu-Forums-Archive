---
title: "Does this BIOS have a backdoor password?"
date: 2012-09-12
forum: Security
---

### Post by Stonecold1995 on 2012-09-12
I have a MainGear ex-L 15 laptop with an AMI BIOS, and I'm wondering if it has a backdoor password for the power-on/administrator BIOS passwords that can be set.  I'm not sure if this information is relevant, but here is the output of "sudo biosdecode":
```
alex@kubuntu:~$ sudo biosdecode
[sudo] password for alex: 
# biosdecode 2.11
ACPI 2.0 present.
        OEM Identifier: MIDERN
        RSD Table 32-bit Address: 0xCA61C028
        XSD Table 64-bit Address: 0x00000000CA61C080
SMBIOS 2.7 present.
        Structure Table Length: 2005 bytes
        Structure Table Address: 0xC9EC6018
        Number Of Structures: 31
        Maximum Structure Size: 210 bytes
PNP BIOS 1.0 present.
        Event Notification: Not Supported
        Real Mode 16-bit Code Address: F000:BC16
        Real Mode 16-bit Data Address: F000:0000
        16-bit Protected Mode Code Address: 0x000FBC3E
        16-bit Protected Mode Data Address: 0x000F0000
PCI Interrupt Routing 1.0 present.
        Router ID: 00:1f.0
        Exclusive IRQs: None
        Compatible Router: 8086:27b8
        Slot Entry 1: ID 00:1f, on-board
        Slot Entry 2: ID 00:14, on-board
        Slot Entry 3: ID 00:1d, on-board
        Slot Entry 4: ID 00:1a, on-board
        Slot Entry 5: ID 00:1b, on-board
        Slot Entry 6: ID 00:16, on-board
        Slot Entry 7: ID 00:1c, on-board
        Slot Entry 8: ID 02:00, slot number 33
        Slot Entry 9: ID 03:00, slot number 34
        Slot Entry 10: ID 04:00, slot number 8
        Slot Entry 11: ID 05:00, slot number 9
        Slot Entry 12: ID 00:01, on-board
        Slot Entry 13: ID 00:06, on-board
        Slot Entry 14: ID 01:00, slot number 16
        Slot Entry 15: ID 00:04, on-board
        Slot Entry 16: ID 00:02, on-board
```

So does this a BIOS with a backdoor password?  Or where can I find out?

---

### Post by cbanakis on 2012-09-12
Are you talking about a second password to bypass the password that can be set in bios?

I do not believe so.

The only purpose would be to get in if the password was forgotten.

In which case, there is a universal workaround.

Desktops have a jumper on the motherboard that resets the bios (including the password)

With laptops, all you need to do is unplug, and remove the battery.  (Usually)

---

### Post by Hungry Man on 2012-09-12
Probably. Even if there isn't if they have physical access and enough time they can open up the system and get around it.

---

