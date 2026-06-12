---
title: "How 2 SMTP only"
date: 2006-05-30
forum: Server Platforms
---

### Post by henkdeswardt on 2006-05-30
Please help.

I'm in trouble!
I had our Telkom ADSL (through Datapro luckily) changed to the un-capped ADSL with fixed IP address from Is (also through Datapro).

BUT now Datapro says that they will no longer relay our SMTP, i.e. outgoing e-mail trhough their SMTP servers.

My server (domain controller) runs Win 2003 Server since I do not know enought about Linux to run a server yet.

HOW can I setup a Ubuntu box to only do SMTP via MX Lookups (DNS)????
Or mail server (Proxy+ is the Windows software's name) works excellent, but can only send "soft SMTP", i.e. it cannot relay via MX Lookups or DNS.

I thus like to setup a text-based SMTP server ASAP.
I do not need the server to do anything else!

My Windows server IP:
192.168.0.150
My router IP (internally)
192.168.0.222
My router IP (externally)
196.xxx.xxx.xxx -- Don't think I should give this out on a forum....

PLEASE help.

We're using a temprory account from Datapro to send e-mail, but is is very slow and very un-reliable!!!!

HHHEEEELLLPPPPPPP

I really-really-really do not want to use Windows Server 2003's SMTP functions!

Thank you.

Henk de Swardt
[email]henkdeswardt@702mail.co.za[/email]

---

### Post by garyng on 2006-05-30
dpkg-reconfigure postfix

and tell it to be "internet" site rather than using smarthost. It will then become your relay host for other local machines(if you choose to) and connect directly to your receipient's mx host when needed, through DNS search.

---

### Post by henkdeswardt on 2006-05-31
Thank you.

I'm making progress.

Just two other questions.
1) How do I change the Linux machine's IP address?
2) How do I change the Linux machine's default gateway to my router's address?

Thank you.

Henk de Swardt

---

### Post by garyng on 2006-05-31
it is controlled under :

/etc/network/interfaces

if you use DHCP(the default I assume), you don't need to change anything, just like the router do it. Or you can modify your router to give out static ip to this particular machine based on say MAC of the network card.

---

