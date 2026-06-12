---
title: "Snort rules not working?"
date: 2007-08-13
forum: Server Platforms
---

### Post by sedition on 2007-08-13
Hi all,

Just installed 6.06 on my poweredge 1550. Pulled down snort, ran it and then cat /var/log/snort/alert. Saw TONS of alerts for:

[**] [1:1384:8] MISC UPnP malformed advertisement [**]
[Classification: Misc Attack] [Priority: 2] 
08/13-22:20:19.729660 192.168.0.1:1900 -> 239.255.255.250:1900
UDP TTL:127 TOS:0x0 ID:19178 IpLen:20 DgmLen:340
Len: 312
[Xref => [http://www.microsoft.com/technet/security/bulletin/MS01-059.mspx]](http://www.microsoft.com/technet/security/bulletin/MS01-059.mspx])[Xref => [http://cve.mitre.org/cgi-bin/cvename.cgi?name=2001-0877]](http://cve.mitre.org/cgi-bin/cvename.cgi?name=2001-0877])[Xref => [http://cve.mitre.org/cgi-bin/cvename.cgi?name=2001-0876]](http://cve.mitre.org/cgi-bin/cvename.cgi?name=2001-0876])[Xref => [http://www.securityfocus.com/bid/3723]](http://www.securityfocus.com/bid/3723])


Decided to try and put a rule in after reading some howto's and with no rules being affective, I just put in some all encompassing rules. According to the following rules (I restarted snort after adding), it would seem that NO alerts should be generated. Am I missing something? Any pointers? Thanks in advance!

pass udp any any -> any any
pass tcp any any -> any any
pass icmp any any -> any any  

----- EDIT ----- Still don't know why my rules are being bypassed, but: grepped the originating rule in /etc/snort/rules/misc.rules and commented it out. No more of those pesky errors.

---

### Post by fabianp on 2008-05-19
Hi, I just started playing with Snort and have the same alert. Did you figure it out what it means? What to do with it?

Thanks for any advice.

---

