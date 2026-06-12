---
title: "Snorting suspicous traffic?"
date: 2010-05-01
forum: Security
---

### Post by uRock on 2010-05-01
Snort is pulling out an alert that is bothering me. Does this look like a false positive? I ran a whois on the 131.216.136.11 and it is a local university(see screenshot) 
Is it possible my system is being used in the attack against UNLV? UFW is enabled and so is NAT on my router.
```
[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-16:55:51.776378 131.216.136.100:80 -> 192.168.1.9:42208
TCP TTL:243 TOS:0x0 ID:47625 IpLen:20 DgmLen:1420 DF
***A**** Seq: 0xBD9E7869  Ack: 0x959CAA06  Win: 0x265C  TcpLen: 32
TCP Options (3) => NOP NOP TS: 721060438 3086816 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-16:55:52.506327 192.168.1.9:42207 -> 131.216.136.100:80
TCP TTL:64 TOS:0x0 ID:29166 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x96158423  Ack: 0xBD009E35  Win: 0x1F5  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3086892 721061160 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-17:21:06.697623 131.216.136.100:80 -> 192.168.1.9:32916
TCP TTL:243 TOS:0x0 ID:28924 IpLen:20 DgmLen:444 DF
***AP*** Seq: 0x1B44BAF9  Ack: 0x1B7E227E  Win: 0x1C8D  TcpLen: 32
TCP Options (3) => NOP NOP TS: 722575356 3238268 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-17:21:06.880653 192.168.1.9:32919 -> 131.216.136.100:80
TCP TTL:64 TOS:0x0 ID:5538 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x1E1F810E  Ack: 0x3BC6CD25  Win: 0x84  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3238329 722575539 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-17:30:26.998783 131.216.136.100:80 -> 192.168.1.9:46334
TCP TTL:243 TOS:0x0 ID:62547 IpLen:20 DgmLen:1420 DF
***A**** Seq: 0xA78D33F4  Ack: 0xF439CFC8  Win: 0x8000  TcpLen: 32
TCP Options (3) => NOP NOP TS: 723135658 3294333 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-17:38:14.206363 192.168.1.9:55092 -> 91.189.94.12:80
TCP TTL:64 TOS:0x0 ID:6611 IpLen:20 DgmLen:52 DF
***A**** Seq: 0xC18235FF  Ack: 0xF35999B9  Win: 0x27D  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3341061 3291891744 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-17:39:37.818013 192.168.1.9:56867 -> 131.216.152.250:80
TCP TTL:64 TOS:0x0 ID:55577 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x2CA2C798  Ack: 0x740EEA0  Win: 0xB7  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3349423 15074093 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-17:53:06.125403 192.168.1.9:54344 -> 91.189.94.12:80
TCP TTL:64 TOS:0x0 ID:2114 IpLen:20 DgmLen:52 DF
***A**** Seq: 0xFE071B2  Ack: 0x421A7B30  Win: 0x1F5  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3430253 3291980932 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-18:01:03.462006 192.168.1.9:52071 -> 91.189.94.12:80
TCP TTL:64 TOS:0x0 ID:54251 IpLen:20 DgmLen:52 DF
***A**** Seq: 0xC889FC33  Ack: 0xFBBB3F14  Win: 0x1F5  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3477987 3292028670 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-18:03:11.758453 192.168.1.9:44195 -> 69.176.111.137:80
TCP TTL:64 TOS:0x0 ID:25362 IpLen:20 DgmLen:60 DF
******S* Seq: 0x56E22713  Ack: 0x0  Win: 0x16D0  TcpLen: 40
TCP Options (5) => MSS: 1460 SackOK TS: 3490817 0 NOP WS: 7 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-18:06:39.275471 192.168.1.9:56249 -> 65.54.87.81:80
TCP TTL:64 TOS:0x0 ID:3776 IpLen:20 DgmLen:52 DF
***A***F Seq: 0x13349F60  Ack: 0x92A21C80  Win: 0x2E  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3511569 577415030 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-18:17:14.288121 192.168.1.9:38394 -> 78.40.125.4:8001
TCP TTL:64 TOS:0x0 ID:56467 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x584C8C0B  Ack: 0x23EDBD07  Win: 0xCD  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3575070 1412694996 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-18:21:37.837384 192.168.1.9:38247 -> 91.189.94.12:80
TCP TTL:64 TOS:0x0 ID:24890 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x46A8A22E  Ack: 0x79EB6289  Win: 0x1F5  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3601424 3292152107 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-18:46:53.774915 192.168.1.9:34789 -> 91.189.94.12:80
TCP TTL:64 TOS:0x0 ID:47809 IpLen:20 DgmLen:52 DF
***A**** Seq: 0xD7D69C0B  Ack: 0xA6F5548  Win: 0x1F5  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3753018 3292303701 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-19:00:24.541508 192.168.1.9:40936 -> 91.189.90.19:443
TCP TTL:64 TOS:0x0 ID:20062 IpLen:20 DgmLen:60 DF
******S* Seq: 0xDF51CEB1  Ack: 0x0  Win: 0x16D0  TcpLen: 40
TCP Options (5) => MSS: 1460 SackOK TS: 3834095 0 NOP WS: 7 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-19:10:09.875183 192.168.1.9:41832 -> 66.102.7.100:80
TCP TTL:64 TOS:0x0 ID:24040 IpLen:20 DgmLen:52 DF
***A**** Seq: 0xF9C54703  Ack: 0xA33309F  Win: 0x3F  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3892628 1041930750 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-19:18:51.981750 192.168.1.9:38394 -> 78.40.125.4:8001
TCP TTL:64 TOS:0x0 ID:58382 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x584C98C6  Ack: 0x24034DE3  Win: 0x499  TcpLen: 32
TCP Options (3) => NOP NOP TS: 3944839 1413619411 
 
```

---

### Post by uRock on 2010-05-01
So I am starting to think it is just a bad rule in Snort. I just installed it on my netbook and now the netbook is having the same traffic after checking out the snort alerts.

I am seeing packets for Canonical's site int there to.

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-19:49:52.934703 192.168.1.15:33404 -> 91.189.94.12:80
TCP TTL:64 TOS:0x0 ID:13972 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x7B9CA8D1  Ack: 0xD976FE77  Win: 0x504  TcpLen: 32
TCP Options (3) => NOP NOP TS: 7122921 3292681621 

[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
05/01-19:37:35.033297 192.168.1.15:39941 -> 131.216.136.100:1027
TCP TTL:40 TOS:0x0 ID:8679 IpLen:20 DgmLen:44
******S* Seq: 0x211FC85  Ack: 0x0  Win: 0x400  TcpLen: 24
TCP Options (1) => MSS: 1460

---

### Post by uRock on 2010-05-02
False positive. Turned off signature in Snort.

---

### Post by Kleenux on 2010-12-22
Thanks uRock for your investigation.

Amazing how this problem appears on so many forums, always with **no explanation** and **no solution**.

The *snort* guys should stop snorting and start answering :-)

---

### Post by bodhi.zazen on 2010-12-23
> **Kleenux said:**
> Thanks uRock for your investigation.

Amazing how this problem appears on so many forums, always with **no explanation** and **no solution**.

The *snort* guys should stop snorting and start answering :-)

This is by design.

NIDS, snort, is designed to sort through the thousands of packets on your network and alert you to activity you should investigate.

It is rules or signature based.

So, when designing rules, what is worse, false positives or not detecting suspicious activity ? The developers / maintainers will always err on the side of too many false positives.

When using these tools you, the sys admin, need to be willing to investigate these things, otherwise do not use them.

One method of attack on NIDS is to send a ton of traffic, sys admin investigates, finds a false positive -> turn off monitoring =).

You can also tune these rules. I do not know how to tune this rule off the top of my head.

---

