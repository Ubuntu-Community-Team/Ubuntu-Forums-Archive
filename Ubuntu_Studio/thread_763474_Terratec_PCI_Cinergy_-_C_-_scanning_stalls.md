---
title: "Terratec PCI Cinergy - C - scanning stalls"
date: 2008-04-23
forum: Ubuntu Studio
---

### Post by Boexli on 2008-04-23
Hi,

I have installed the manits driver for the terratec cinergy pci - c DVB card. everything seems to work fine - card is being detected without any issues. however if I start the scanning in kaffeine or w_scan both applications stop after the found the first transponder as per the message below:

not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Using DVB device 0:0 "Philips TDA10023 DVB-C"
tuning DVB-C to 506000000
inv:2 sr:6900000 fecH:0 mod:3
. LOCKED.
Transponders: 8/28


I got it working about three weeks ago but now I get stuck. Does anyone know what the root cause this could be? Could it be that the card is broken? Thanks Nick

---

### Post by walopower on 2008-05-03
Had been Same problem, but now working. Newest (and mayby previously mantis drivers is buggy). So install mantis drivers from archive history.

---

### Post by Boexli on 2008-05-04
Thanks did do the same -works fine now. Thanks Nick

---

