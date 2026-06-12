---
title: "Asterisk and DAHDI"
date: 2009-10-21
forum: Server Platforms
---

### Post by cbox on 2009-10-21
Hi,

I just installed a new server with asterisk 1.6.1, libpri 1.4.10.1 and dahdi 2.2.0.

Everything seems ok, but i cannot recieve og send calls on my E1.

I compiled all the packages, and i'm able to startup asterisk.
Also i can see the E1 when i type dahdi show status in asterisk.
Description                              Alarms  IRQ    bpviol CRC4   Fra Codi Options  LBO
Wildcard TE121 Card 0                    OK      1      0      0      CCS HDB3 CRC4     0 db (CSU)/0-133 feet (DSX-1)


When i check the dahdi i get this
### Span  1: WCT1/0 "Wildcard TE121 Card 0" (MASTER) HDB3/CCS/CRC4 ClockSource
  1 PRI        Clear       (SWEC: MG2)
  2 PRI        Clear       (SWEC: MG2)
  3 PRI        Clear       (SWEC: MG2)
  4 PRI        Clear       (SWEC: MG2)
  5 PRI        Clear       (SWEC: MG2)
  6 PRI        Clear       (SWEC: MG2)
  7 PRI        Clear       (SWEC: MG2)
  8 PRI        Clear       (SWEC: MG2)
  9 PRI        Clear       (SWEC: MG2)
 10 PRI        Clear       (SWEC: MG2)
 11 PRI        Clear       (SWEC: MG2)
 12 PRI        Clear       (SWEC: MG2)
 13 PRI        Clear       (SWEC: MG2)
 14 PRI        Clear       (SWEC: MG2)
 15 PRI        Clear       (SWEC: MG2)
 16 PRI        HDLCFCS
 17 PRI        Clear       (SWEC: MG2)
 18 PRI        Clear       (SWEC: MG2)
 19 PRI        Clear       (SWEC: MG2)
 20 PRI        Clear       (SWEC: MG2)
 21 PRI        Clear       (SWEC: MG2)
 22 PRI        Clear       (SWEC: MG2)
 23 PRI        Clear       (SWEC: MG2)
 24 PRI        Clear       (SWEC: MG2)
 25 PRI        Clear       (SWEC: MG2)
 26 PRI        Clear       (SWEC: MG2)
 27 PRI        Clear       (SWEC: MG2)
 28 PRI        Clear       (SWEC: MG2)
 29 PRI        Clear       (SWEC: MG2)
 30 PRI        Clear       (SWEC: MG2)
 31 PRI        Clear       (SWEC: MG2)


When i write pri show spans i get no result back. What can cause this issue?

Best regards
Sylvester Nielsen

---

