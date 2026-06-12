---
title: "Firestarter"
date: 2008-04-22
forum: Security
---

### Post by burunji on 2008-04-22
Hello does anyone knows what this means
because I really dont know and i have been getting Hit from this same iP number as long as I can remember even when i was on windows, it's also when of the reasons why I am using ubuntu I have been told its very safe unlikely MS windows. please if someone would tell me what this is i would very much apperciate it. here below you can see the firestarter-events


Time:Apr 21 18:23:25 Direction: Unknown In:eth1 Out: Port:1026 Source:24.64.197.166 Destination:86.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:23:25 Direction: Unknown In:eth1 Out: Port:1028 Source:24.64.197.166 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:23:25 Direction: Unknown In:eth1 Out: Port:1027 Source:24.64.197.166 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:25:46 Direction: Unknown In:eth1 Out: Port:1027 Source:24.65.2.41 Destination:86.0.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:25:46 Direction: Unknown In:eth1 Out: Port:1026 Source:24.65.2.41 Destination:86.0.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:25:46 Direction: Unknown In:eth1 Out: Port:1028 Source:24.65.2.41 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:26:58 Direction: Unknown In:eth1 Out: Port:1027 Source:24.64.246.213 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:26:58 Direction: Unknown In:eth1 Out: Port:1026 Source:24.64.246.213 Destination:86.0.*** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:26:58 Direction: Unknown In:eth1 Out: Port:1028 Source:24.64.246.213 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:37:42 Direction: Unknown In:eth1 Out: Port:1028 Source:24.64.65.164 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:37:42 Direction: Unknown In:eth1 Out: Port:1026 Source:24.64.65.164 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:37:42 Direction: Unknown In:eth1 Out: Port:1027 Source:24.64.65.164 Destination:86.0.****Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:42:17 Direction: Unknown In:eth1 Out: Port:1028 Source:24.64.169.253 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:42:17 Direction: Unknown In:eth1 Out: Port:1026 Source:24.64.169.253 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:42:17 Direction: Unknown In:eth1 Out: Port:1027 Source:24.64.169.253 Destination:86.0.**** Length:512 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 21 18:44:01 Direction: Unknown In:eth1 Out: Port:2967 Source:86.0.3.207 Destination:86.0.**** Length:64 TOS:0x00 Protocol:TCP Service:Unknown

---

### Post by Kirce on 2008-04-22
first i would check you're internet ip address ( [http://www.myipaddress.com](http://www.myipaddress.com) ) and make sure its not actually you or another comp on you're network

---

### Post by PetePete on 2008-04-22
its spam scans. In windows if you have the messenger protocol running a popup would display with some spam message.

Nothing to worry about in linux, and not much to worry about in windows if you disable the service.

here's a link for more info if you want.
[http://www.linklogger.com/messenger_spam.htm](http://www.linklogger.com/messenger_spam.htm)

---

### Post by 3rdalbum on 2008-04-22
```

chris@chris-desktop:~$ whois 24.65.2.41

OrgName:    Shaw Communications Inc. 
OrgID:      SHAWC
Address:    Suite 800
Address:    630 - 3rd Ave. SW
City:       Calgary
StateProv:  AB
PostalCode: T2P-4L4
Country:    CA

ReferralServer: rwhois://rwhois.shawcable.net:4321/

NetRange:   24.64.0.0 - 24.71.255.255 
CIDR:       24.64.0.0/13 
NetName:    SHAW-COMM
NetHandle:  NET-24-64-0-0-1
Parent:     NET-24-0-0-0-0
NetType:    Direct Allocation
NameServer: NS7.NO.CG.SHAWCABLE.NET
NameServer: NS8.SO.CG.SHAWCABLE.NET
Comment:    
RegDate:    1996-06-03
Updated:    2006-02-08

OrgAbuseHandle: SHAWA-ARIN
OrgAbuseName:   SHAW ABUSE 
OrgAbusePhone:  +1-403-750-7420
OrgAbuseEmail:  internet.abuse@sjrb.ca

OrgTechHandle: ZS178-ARIN
OrgTechName:   Shaw High-Speed Internet 
OrgTechPhone:  +1-403-750-7428
OrgTechEmail:  ipadmin@sjrb.ca

# ARIN WHOIS database, last updated 2008-04-21 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.


Found a referral to rwhois.shawcable.net:4321.

%rwhois V-1.5:003fff:00 rs1so.cg.shawcable.net (by Network Solutions, Inc. V-1.5.9.5)
%referral rwhois://root.rwhois.net:4321/auth-area=.
%ok

```

That's some information about the IP addresses that are listed as the "source". Maybe get in touch with the e-mail address mentioned, and tell them that there appears to be some heavy port scanning going on from one of their customers.

---

### Post by burunji on 2008-04-22
hi i'm sorry about my later reply and my poor english.
Yeah i checked it's not my ip or another computer on my network.
they have been scanning me as long as i can remember and it appears to be these particular ip's 24.65.2.41-24.64.65.164 
and as (petepete) suggested and i did sent email i am waiting for their reply and i will let you know.
I don't use windows anymore so no need to to worry about spammer,adaware,spyware or viruses.
Thank you so much all of you for your quick reply now i know i made good decision switching to linux it's great community,

---

### Post by burunji on 2008-04-22
hi i'm sorry about my late reply and my poor english.
Yeah i checked it's not my ip or another computer on my network.
they have been scanning me as long as i can remember and it appears to be these particular ip's 24.65.2.41-24.64.65.164 
and as (petepete) suggested and i did sent email i am waiting for their reply and i will let you know.
I don't use windows anymore so no need to to worry about spammer,adaware,spyware or viruses.
Thank you so much all of you for your quick reply now i know i made good decision switching to linux it's great community,

---

### Post by burunji on 2008-04-22
hello it's me again i do have another question and it's not related to the previous problem and i do apologise it.
 i upgrade ubuntu 710 to ubuntu LTS 8.04 which version is best for my hardware this is my computer details

    *  Intel Core 2 Duo Processor T5450
    * (1.6 GHz, 667 MHz FSB, 2 MB Cache)
    * Genuine Windows Vista (R) Home Premium
    * 2 GB Memory
    * 160 GB hard drive
now i am using ubuntu LTS 8.04 version x86
please let me know if it's correct version for my hardware before i damage laptop.

thank you

Regards

---

### Post by dperfors on 2008-04-23
Normaly it shouldn't be a problem. If you want to be sure if everything is working, just bootup the live cd and try it out. The only thing you could damage is the Vista installation, but that shouldn't be a problem :P

---

### Post by burunji on 2008-04-23
i did what you told me and use the live cd everything seem to be working.
thank you

---

### Post by burunji on 2008-04-23
hi i was wondering since now i am using ubuntu 8.04 candidate release.
will i be able to upgrade to final release or am i gonna have to do whole new installation.
sorry about beginner questions,  I am honestly using linux about now 2 weeks i am completely new.

regards

---

