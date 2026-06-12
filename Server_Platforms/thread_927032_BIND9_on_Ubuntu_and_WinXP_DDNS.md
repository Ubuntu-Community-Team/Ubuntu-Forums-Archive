---
title: "BIND9 on Ubuntu and WinXP DDNS"
date: 2008-09-22
forum: Server Platforms
---

### Post by ktiger on 2008-09-22
Greetings;

I am unable to get my Windows XP clients to dynamically update their A records.
I am not using DHCP, IP addresses and DNS settings are statically assigned. Insecure (update from any, no keys, etc.) for the sake of simplicity.
Nsupdate DOES work, but I expected WIndows XP to also update the zone. I have Samba configured (same PC as BIND) as a domain controller and the XP clients are a part of that domain. Dns client and DHCP client services are running on XP machines, as I understand that these services need to be running for dynamic updates to occur. Here are my versions:

Ubuntu Hardy 8.04 Server (with desktop installed)
Bind 9.4.2-P1
Linux Kernel 2.6.24-19-Server #1 SMP
Samba 3.0.28a-1ubuntu4.5
Windows XP SP3

If you require any additional information, please let me know.
Thank you for your assistance.

---

### Post by HermanAB on 2008-09-22
It is a security hole.  Only the modified Microsoft BSD DNS will allow that, since they don't care much about security.

---

### Post by ktiger on 2008-09-23
Hi Herman,

Thanks for the reply.
So, I can only dynamically update if I use DHCP, or use Microsoft's implementation of DNS? :(
The following link is a bit ambiguous, but I would be curious what your interpretation would be:
[http://support.microsoft.com/kb/275866/en-us](http://support.microsoft.com/kb/275866/en-us)
Does this mean I'm missing SRV records that XP expects to get when it first queries BIND, or yes it's possible but use nsupdate, or....? :confused:

Thanks Again!

---

### Post by ktiger on 2008-09-30
*BUMP*

Hey, anyone else trying this?
Can anyone clarify what Herman said?
Is this possible with this configuration (no DHCP)?

Thanks.
Keith

---

