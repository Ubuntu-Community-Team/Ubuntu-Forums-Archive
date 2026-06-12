---
title: "Repeating error message MySQL Server - broken memory module?"
date: 2010-08-04
forum: Server Platforms
---

### Post by scout76 on 2010-08-04
Hello!

On our server (Ubuntu 10.04 LTS (x86_64) I have noticed the following error message (see below) which even appears in the shell. 
Does anyone know how to deal with it? Could a broken memory module causing this? And if so, can it be seen from the error message which
of them is broken?

Cheers,

scout76

Aug  1 13:38:02 durthang kernel: [771510.780050]  Northbridge Error, node 0
Aug  1 13:38:02 durthang kernel: [771510.780057] ECC/ChipKill ECC error.
Aug  1 13:38:02 durthang kernel: [771510.780063] EDAC amd64 MC0: CE ERROR_ADDRESS= 0x3c7d2dc00
Aug  1 13:38:02 durthang kernel: [771510.780074] EDAC MC0: CE page 0x3c7d2d, offset 0xc00, grain 0, syndrome 0xa4f4, row 3, channel 0, label "": amd64_edac
Aug  1 14:06:03 durthang kernel: [773191.930065]  Northbridge Error, node 0
Aug  1 14:06:03 durthang kernel: [773191.966161] ECC/ChipKill ECC error.
Aug  1 14:06:03 durthang kernel: [773191.984337] EDAC amd64 MC0: CE ERROR_ADDRESS= 0x346d70310
Aug  1 14:06:03 durthang kernel: [773191.984349] EDAC MC0: CE page 0x346d70, offset 0x310, grain 0, syndrome 0xa4f4, row 3, channel 0, label "": amd64_edac
Aug  1 23:04:22 durthang kernel: [805490.610059]  Northbridge Error, node 0
Aug  1 23:04:22 durthang kernel: [805490.647030] ECC/ChipKill ECC error.
Aug  1 23:04:22 durthang kernel: [805490.647041] EDAC amd64 MC0: CE ERROR_ADDRESS= 0x34ad72110
Aug  1 23:04:22 durthang kernel: [805490.647053] EDAC MC0: CE page 0x34ad72, offset 0x110, grain 0, syndrome 0x83c1, row 3, channel 0, label "": amd64_edac
Aug  2 01:04:38 durthang kernel: [812707.320062]  Northbridge Error, node 0
Aug  2 01:04:38 durthang kernel: [812707.356886] ECC/ChipKill ECC error.
Aug  2 01:04:39 durthang kernel: [812707.356892] EDAC amd64 MC0: CE ERROR_ADDRESS= 0x3c7d2dc00
Aug  2 01:04:39 durthang kernel: [812707.356906] EDAC MC0: CE page 0x3c7d2d, offset 0xc00, grain 0, syndrome 0xa4f4, row 3, channel 0, label "": amd64_edac
Aug  2 01:38:48 durthang kernel: [814757.030065]  Northbridge Error, node 0
Aug  2 01:38:48 durthang kernel: [814757.066295] ECC/ChipKill ECC error.
Aug  2 01:38:48 durthang kernel: [814757.066301] EDAC amd64 MC0: CE ERROR_ADDRESS= 0x29f2007b0
Aug  2 01:38:48 durthang kernel: [814757.066315] EDAC MC0: CE page 0x29f200, offset 0x7b0, grain 0, syndrome 0x83c1, row 2, channel 0, label "": amd64_edac

---

### Post by Fafler on 2010-08-04
Reboot and choose memtest86+ from the GRUB menu.

If it isn't installed by default (can't remember, but i'm not even sure Ubuntu have a boot menu in the default configuration), open a terminal and type sudo apt-get install memtest86+ and try again.

---

### Post by scout76 on 2010-08-04
Hello Fafler!

Thanks for your answer! I thought about the memtest too. However, wouldnt using the memtest mean that the server won't work for the whole day? I would really like to avoid this. 
Is there any alternative?

Cheers,

scout76

---

### Post by ruffEdgz on 2010-08-04
Without further diagnosing the memory issue with the memtest, you can only assume that all the RAM on your system needs to be replaced. At least if you run the memtest, it might be able to detect the problem and tell you more about this RAM issue.

I would like to say there is an 'online' solution but if there was, it would slow down your system to complete the tests so it don't help whatever service you are running on it (in this case its mysql).

The two options I see for this are:
 
 1. Do a memtest and further diagnosing of the problem. If testing shows which DIMM slot is having the issue, then schedule a time to replace the RAM.

 2. Assume that that you need to replace all the memory and schedule a downtime to replace it.

---

### Post by cmjohnson on 2011-11-28
I have this same error.  I did run memtest 86 and the results came back clean with no errors.  I am now officially confused.   Is it possible for mysql to be causing a false memory error?  I am thinking that the server does not have enough memory but not sure.  Any help is appreciated

---

### Post by 2WheelPenguin on 2011-11-28
> **cmjohnson said:**
> I have this same error.  I did run memtest 86 and the results came back clean with no errors.  I am now officially confused.   Is it possible for mysql to be causing a false memory error?  I am thinking that the server does not have enough memory but not sure.  Any help is appreciated

The error says "ECC/ChipKill ECC error".
If the system does indeed have ECC memory, make sure that ECC is enabled when running memtest.

---

