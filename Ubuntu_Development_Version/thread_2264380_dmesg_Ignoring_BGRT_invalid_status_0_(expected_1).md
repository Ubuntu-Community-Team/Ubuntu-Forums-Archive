---
title: "dmesg: Ignoring BGRT: invalid status 0 (expected 1)"
date: 2015-02-07
forum: Ubuntu Development Version
---

### Post by sanderj on 2015-02-07
With vivid (both kernel 3.18 and 3.19), my dmesg says:

```
[    0.036738] Ignoring BGRT: invalid status 0 (expected 1)
```

In it's in red, so apparently something wrong. Tips ... how to solve this ... file this as bug report ... or ignore?


Background:

This line of source code was introduced in kernel 3.18 in arch/x86/platform/efi/efi-bgrt.c:

```
 53         if (bgrt_tab->status != 1) {
 54                 pr_err("Ignoring BGRT: invalid status %u (expected 1)\n",
 55                        bgrt_tab->status);
 56                 return;
 57         }
```

The sequence
```
sudo acpidump > acpi.dat
acpixtract -a acpi.dat
iasl -d bgrt.dat 
cat bgrt.dsl
```
leads to

```
/*
 * Intel ACPI Component Architecture
 * AML/ASL+ Disassembler version 20141107-64 [Dec 17 2014]
 * Copyright (c) 2000 - 2014 Intel Corporation
 * 
 * Disassembling to symbolic ASL+ operators
 *
 * Disassembly of bgrt.dat, Sat Feb  7 10:26:34 2015
 *
 * ACPI Data Table [BGRT]
 *
 * Format: [HexOffset DecimalOffset ByteLength]  FieldName : FieldValue
 */

[000h 0000   4]                    Signature : "BGRT"    [Boot Graphics Resource Table]
[004h 0004   4]                 Table Length : 00000038
[008h 0008   1]                     Revision : 01
[009h 0009   1]                     Checksum : C7
[00Ah 0010   6]                       Oem ID : "HPQOEM"
[010h 0016   8]                 Oem Table ID : "802A    "
[018h 0024   4]                 Oem Revision : 00000001
[01Ch 0028   4]              Asl Compiler ID : "HP  "
[020h 0032   4]        Asl Compiler Revision : 00040000

[024h 0036   2]                      Version : 0001
[026h 0038   1]                       Status : 00
[027h 0039   1]                   Image Type : 00
[028h 0040   8]                Image Address : 0000000077180000
[030h 0048   4]                Image OffsetX : 00000261
[034h 0052   4]                Image OffsetY : 000000DC

Raw Table Data: Length 56 (0x38)

  0000: 42 47 52 54 38 00 00 00 01 C7 48 50 51 4F 45 4D  BGRT8.....HPQOEM
  0010: 38 30 32 41 20 20 20 20 01 00 00 00 48 50 20 20  802A    ....HP  
  0020: 00 00 04 00 01 00 00 00 00 00 18 77 00 00 00 00  ...........w....
  0030: 61 02 00 00 DC 00 00 00                          a.......

```

I thought I had seen something about an incorrect BGRT checksum in my logging, but I can't find that right now.

---

### Post by mc4man on 2015-02-07
I'd ignore as seems to be a new warning about nothing that matters (cosmetic
[http://lkml.iu.edu/hypermail/linux/kernel/1407.3/04597.html](http://lkml.iu.edu/hypermail/linux/kernel/1407.3/04597.html)

[http://www.msfn.org/board/topic/158372-windows-8-and-bgrt/](http://www.msfn.org/board/topic/158372-windows-8-and-bgrt/)
> The Boot Graphics Resource Table (BGRT) is an optional table that provides a mechanism to indicate that an image was drawn on the screen during boot, and some information about the image.
The table is written when the image is drawn on the screen. This should be done after it is expected that any firmware components that may write to the screen are done doing so and it is known that the image is the only thing on the screen. If the boot path is interrupted (e.g. by a key press), the valid bit within the status field should be changed to 0 to indicate to the OS that the current image is invalidated.
This table is only supported on UEFI systems. 

---

### Post by sanderj on 2015-02-07
OK, thanks for the info. So I guess the "pr_err()" (as in: error) is bit over the top.

Thanks.

---

### Post by d-cosner on 2015-02-07
Also thank you! I saw this same error on my laptop with another distro and was trying to figure it out. Now at leas I know what it is all about!

---

### Post by cariboo on 2015-02-07
Seems to be working fine here:

```
dmesg | grep BGRT
[    0.000000] ACPI: BGRT 0x00000000BA7DFB98 000038 (v00 ALASKA A M I    01072009 AMI  00010013)
```

I'm running an Asus M5A97 R2.0 motherboard

---

### Post by micknotten on 2015-07-27
I have the same error message and then it stucks in startup:
[   0.023512] Ignoring BGRT: invalid status 0 (expected 1)
[   0.742970] ACPI PCC probe failed.
starting version 219 
welcome to emergency mode! ....
...
try again to boot into default mode. 
This works, it starts up as usual.
What can I do to get rid of this startup error?
Thanks, Mick

---

### Post by PaulW2U on 2015-07-27
micknotten, this is an old thread that goes back to when Vivid Vervet was the current development release.

Please start a new thread in General Help giving us details of your Ubuntu version and anything else relevant to the problem that you are experiencing.

Thread closed.

---

