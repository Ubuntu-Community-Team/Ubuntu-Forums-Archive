---
title: "Can not write on NFC Tag with libnfc 1.7.1. Command nfc-mfclassic does not work"
date: 2019-10-14
forum: Ubuntu/Debian BASED
---

### Post by hassoya on 2019-10-14
[COLOR=#242729][FONT=Arial]I used the tools mfoc and mfcuk to clone my fitness access-card. I tried to write the informations into the dump card with the command nfc-mfclassic. But every time I get this warning:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][I]
Warning: Unlock command [1/2]: failed / not acknowledged. Writing 64 blocks |Failure to write to data block 4[/I][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I changed the original cards und tried to write on other dump cards but still the same message.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I looked into the source code but could not figure out what to do. Does anyone had the same message ?

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]hassoya@hassoya-iMac:~/mfoc/src$ nfc-mfclassic W a file.dmp dummy.dmp[/FONT][/COLOR]
NFC reader: ACS / ACR122U PICC Interface opened
Found MIFARE Classic card:
ISO/IEC 14443A (106 kbps) target:
    ATQA (SENS_RES): 00  04  
       UID (NFCID1): 0a  5e  dd  c4  
      SAK (SEL_RES): 08  
Guessing size: seems to be a 1024-byte card
Sent bits:     50  00  57  cd  
Sent bits:     40 (7 bits)
Warning: Unlock command [1/2]: failed / not acknowledged. [COLOR=#242729][FONT=Consolas]Writing 64 blocks |Failure to write to data block 4[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]&#8203;[COLOR=#242729][FONT=Arial]I am using Ubuntu 18.04 and the reader [/FONT][/COLOR]**ACS ACR122U**

---

### Post by uRock on 2019-10-14
Hello and welcome to the forums.

We cannot help you create illegal reproductions of your gym card. Please take the time to read our [Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules").

Thread Closed.

---

