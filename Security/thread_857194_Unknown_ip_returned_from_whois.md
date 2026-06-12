---
title: "Unknown ip returned from whois"
date: 2008-07-12
forum: Security
---

### Post by jmore9 on 2008-07-12
Anyone ever have this problem - i am getting the following and my internet has slowed down to nothing and the following is in the firestarter log :

Time:Jul 12 08:13:08 Direction: Unknown In-ppp0 Out: Port:1732 Source:209.202.228.169 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:11 Direction: Unknown In-ppp0 Out: Port:2904 Source:209.202.228.123 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:12 Direction: Unknown In-ppp0 Out: Port:1945 Source:209.202.228.170 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:14 Direction: Unknown In-ppp0 Out: Port:55871 Source:209.202.228.119 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:23 Direction: Unknown In-ppp0 Out: Port:34041 Source:209.202.228.119 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:24 Direction: Unknown In-ppp0 Out: Port:48644 Source:209.202.228.171 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:25 Direction: Unknown In-ppp0 Out: Port:45746 Source:209.202.228.168 Destination:69.39.93.31 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 12 08:13:33 Direction: Unknown In:ppp0 Out: Port:50899 Source:209.202.228.168 Destination:69.39.93.31 Length:873 TOS:0x00 Protocol:TCP Service:Unknown

Also what does the little yellow icons mean that are between In:ppp0 ?


that is just a part of it.  Anyone have any idea about it ?
When i whois 209.202.228.168 i got the unknown ip.  I am using kubuntu 8.04.  My buddy says it is uncle sam sping on me.

---

### Post by simonapnic on 2008-07-12
OrgName:    Lycos, Inc.
OrgID:      LYCOSI-1
Address:    100 Fifth Avenue
City:       Waltham
StateProv:  MA
PostalCode: 02451
Country:    US

NetRange:   209.202.192.0 - 209.202.255.255
CIDR:       209.202.192.0/18
NetName:    NETBLK-LYCOS-1
NetHandle:  NET-209-202-192-0-1
Parent:     NET-209-0-0-0-0
NetType:    Direct Assignment
NameServer: NS1.LYCOS.COM
NameServer: NS2.LYCOS.COM
NameServer: NS3.LYCOS.COM
NameServer: NS4.LYCOS.COM
Comment:
RegDate:    2000-05-22
Updated:    2008-05-07

RTechHandle: VY7-ARIN
RTechName:   Yelsangikar, Vish
RTechPhone:  +1-781-370-2700
RTechEmail:  [email]nic-tech@lycos-inc.com[/email]

OrgTechHandle: NETWO1939-ARIN
OrgTechName:   Network Operations
OrgTechPhone:  +1-781-370-2700
OrgTechEmail:  [email]nic-tech@lycos-inc.com[/email]

That's your "unknown" IP.

---

### Post by jmore9 on 2008-07-12
Thanks when i did it from this box whois returned the unknown ip statement.

Thanks a lot for the info.  Also i still have not figured out where the thanks button is or has that been done away with ?

---

