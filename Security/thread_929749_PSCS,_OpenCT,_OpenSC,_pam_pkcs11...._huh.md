---
title: "PSCS, OpenCT, OpenSC, pam_pkcs11.... huh?"
date: 2008-09-25
forum: Security
---

### Post by redgsturbo on 2008-09-25
Ok... So I work for DoD and have a CAC card, which seems to only be seen by the pcsc driver... I followed the guides for getting that to work.  Next I'd like to have pam_pkcs11 log me in with my CAC card, OR I'd like to use my own Schlumberger E-Gate USB stick/card.  Here is the output of some commands so you know where I'm at

```
root@hel:/home/hunter# opensc-tool -l
Readers known about:
Nr.    Driver     Name
0      pcsc       Dell smart card reader keyboard 00 00
1      openct     Schlumberger E-Gate
2      openct     OpenCT reader (detached)
root@hel:/home/hunter# opensc-tool -D
Configured card drivers:
  cardos           Siemens CardOS
  cardos           Siemens CardOS
  flex             Schlumberger Multiflex/Cryptoflex
  cyberflex        Schlumberger Cyberflex
  gpk              Gemplus GPK
  miocos           MioCOS 1.1
  mcrd             MICARDO 2.1
  asepcos          Athena ASEPCOS
  setcos           Setec cards
  starcos          STARCOS SPK 2.3/2.4
  tcos             TCOS 2.0
  openpgp          OpenPGP card
  jcop             JCOP cards with BlueZ PKCS#15 applet
  oberthur         Oberthur AuthentIC.v2/CosmopolIC.v4
  belpic           Belpic cards
  atrust-acos      A-Trust ACOS cards
  muscle           Muscle Card Driver
  emv              EMV compatible cards
  incrypto34       Incard Incripto34
  piv              PIV-II  for multiple cards
  acos5            ACS ACOS5 card
  akis             TUBITAK UEKAE AKIS
  default          Default driver for unknown cards
root@hel:/home/hunter# opensc-tool -R
Configured reader drivers:
  pcsc             PC/SC reader
  ctapi            CT-API module
  openct           OpenCT reader
root@hel:/home/hunter# opensc-tool -f -r 1
root@hel:/home/hunter# openct-tool list
  0 Schlumberger E-Gate

```

pkcs15-tool doesn't see anything, while pkcs11-tool sees the E-Gate.  I noticed /etc/readers.conf.d/openct contains:
# This file allows pcscd to use OpenCT as an ifd-handler. It is
# commented out by default. To enable it, uncomment the lines below
# and run update-reader.conf
```

FRIENDLYNAME     "OpenCT"
DEVICENAME       /dev/null
LIBPATH          /usr/lib/openct-ifd.so
CHANNELID        0
```


I'm a little confused about how this is all supposed to work, but I understand openct SHOULD be able to handle both the ccid CAC reader in my keyboard as well as my egate reader, and opensc should identify both actual smartcards. 

When I have both a CAC and my E-Gate inserted I get this:
```
root@hel:/home/hunter# pkcs11-tool -L -r 1
[opensc-pkcs11] pkcs15.c:532:sc_pkcs15_bind_internal: unable to enumerate apps: Unsupported INS byte in APDU
[opensc-pkcs11] pkcs15.c:761:sc_pkcs15_bind: returning with: Unsupported card
[opensc-pkcs11] pkcs15.c:761:sc_pkcs15_bind: returning with: Unsupported card
[opensc-pkcs11] pkcs15.c:761:sc_pkcs15_bind: returning with: Unsupported card
Available slots:
[opensc-pkcs11] pkcs15.c:761:sc_pkcs15_bind: returning with: Unsupported card
Slot 0           (empty)
Slot 1           (empty)
Slot 2           (empty)
Slot 3           (empty)
Slot 4           Schlumberger E-Gate
  token label:   OpenSC Card (Hunter)
  token manuf:   OpenSC Project
  token model:   PKCS #15 SCard
  token flags:   rng, login required, PIN initialized, token initialized
  serial num  :  <blahblah>
Slot 5           (empty)
Slot 6           (empty)
Slot 7           (empty)
[opensc-pkcs11] pkcs15.c:761:sc_pkcs15_bind: returning with: Unsupported card
error: PKCS11 function C_OpenSession failed: rv = CKR_TOKEN_NOT_PRESENT (0xe0)

Aborting.
```

When I remove the CAC I get this
```
root@hel:/home/hunter# pkcs11-tool -L -r 1
Available slots:
Slot 0           (empty)
Slot 1           (empty)
Slot 2           (empty)
Slot 3           (empty)
Slot 4           Schlumberger E-Gate
  token label:   OpenSC Card (Hunter)
  token manuf:   OpenSC Project
  token model:   PKCS #15 SCard
  token flags:   rng, login required, PIN initialized, token initialized
  serial num  :  <blahblah>
Slot 5           (empty)
Slot 6           (empty)
Slot 7           (empty)
error: PKCS11 function C_OpenSession failed: rv = CKR_TOKEN_NOT_PRESENT (0xe0)

Aborting.
```

So it appears OpenSC does not support the CAC, which pcsc_scan seems to think is an Axalto Cyberflex 64k

On a side note, Why do I get the CRK_TOKEN_NOT_PRESENT error... I get this even when I attempt to generate a token for the card

All thoughts, comments, help, flames, etc will be entertained :confused:

---

### Post by redgsturbo on 2008-09-25
Also, I just put an EOF at the end of /etc/reader.conf.d/openct, ```
restarted pcscd, and now I get this:
root@hel:/home/hunter# pcsc_scan 
PC/SC device scanner
V 1.4.11 (c) 2001-2007, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.4
Scanning present readers
0: OpenCT 00 00
1: Dell smart card reader keyboard 00 00

Thu Sep 25 10:26:14 2008
 Reader 0: OpenCT 00 00
  Card state: Card inserted, 
  ATR: 3B 95 18 40 FF 62 01 02 01 04

ATR: 3B 95 18 40 FF 62 01 02 01 04
+ TS = 3B --> Direct Convention
+ T0 = 95, Y(1): 1001, K: 5 (historical bytes)
  TA(1) = 18 --> Fi=372, Di=12, 31 cycles/ETU (115200 bits/s at 3.57 MHz)
  TD(1) = 40 --> Y(i+1) = 0100, Protocol T = 0 
-----
  TC(2) = FF --> Work waiting time: 960 x 255 x (Fi/F)
+ Historical bytes: 62 01 02 01 04
  Category indicator byte: 62 (proprietary format)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B 95 18 40 FF 62 01 02 01 04
	Schlumberger Cryptoflex 32K e-gate

Thu Sep 25 10:26:14 2008
 Reader 1: Dell smart card reader keyboard 00 00
  Card state: Card removed, 

Thu Sep 25 10:26:34 2008
 Reader 1: Dell smart card reader keyboard 00 00
  Card state: Card inserted, 
  ATR: 3B 95 95 40 FF AE 01 03 00 00

ATR: 3B 95 95 40 FF AE 01 03 00 00
+ TS = 3B --> Direct Convention
+ T0 = 95, Y(1): 1001, K: 5 (historical bytes)
  TA(1) = 95 --> Fi=512, Di=16, 32 cycles/ETU (111600 bits/s at 3.57 MHz)
  TD(1) = 40 --> Y(i+1) = 0100, Protocol T = 0 
-----
  TC(2) = FF --> Work waiting time: 960 x 255 x (Fi/F)
+ Historical bytes: AE 01 03 00 00
  Category indicator byte: AE (proprietary format)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B 95 95 40 FF AE 01 03 00 00
	Axalto - Cyberflex 64K

Thu Sep 25 10:26:44 2008
 Reader 1: Dell smart card reader keyboard 00 00
  Card state: Card removed, 

Thu Sep 25 10:26:51 2008
 Reader 0: OpenCT 00 00
  Card state: Card removed, 
```

---

