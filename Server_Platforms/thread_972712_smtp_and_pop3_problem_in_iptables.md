---
title: "smtp and pop3 problem in iptables"
date: 2008-11-06
forum: Server Platforms
---

### Post by jennifer.ayag on 2008-11-06
hello! can anybody please help me in my problem?

It's almost a month since i started doing this.i made a dekstop firewall with ubuntu hardy server, webmin, squid and iptables. i'm able to connect to the internet but the only problem is our email.

we are using pop3 and smtp with the following details

POP SERVER = pop3.mrm.net
SMTP SERVER = smtp.mrm.net
POP3 PORT = 995 (ssl)
SMTP PORT = 465 (ssl)

i've read a lot in the net re how to do this but nothing happens....

i read that i need to masquerade  and make a prerouting/postrouting rules. i also did that but again no results..

Note: i'm using webmin module in configuring my iptables....

when i tried to check the POSTROUTING/PREROUTING rules in the command prompt in firewall itself.....there's an error "no chain/target/match by that name"

PLEASE HELP!!!

---

