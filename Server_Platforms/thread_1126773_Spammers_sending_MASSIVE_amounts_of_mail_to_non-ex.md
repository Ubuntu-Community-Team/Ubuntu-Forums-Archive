---
title: "Spammers sending MASSIVE amounts of mail to non-existant addresses"
date: 2009-04-15
forum: Server Platforms
---

### Post by infecticide on 2009-04-15
For two days now I have be besieged by spammers attempting to send email to mailboxes that don't exist on my server.

```


Apr 15 17:08:25 infecticide postfix/smtpd[15543]: setting up TLS connection from unknown[195.53.62.68]
Apr 15 17:08:25 infecticide postfix/smtpd[15595]: Anonymous TLS connection established from unknown[69.39.36.246]: TLSv1 with cipher RC4-MD5 (128/128 bits)
Apr 15 17:08:25 infecticide postfix/smtpd[15543]: Anonymous TLS connection established from unknown[195.53.62.68]: TLSv1 with cipher RC4-MD5 (128/128 bits)
Apr 15 17:08:25 infecticide postfix/smtpd[15595]: NOQUEUE: reject: RCPT from unknown[69.39.36.246]: 450 4.1.1 <iteal_1978@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<iteal_1978@jortosh.com> proto=ESMTP helo=<mail.coafcu.org>
Apr 15 17:08:25 infecticide postfix/smtpd[15595]: disconnect from unknown[69.39.36.246]
Apr 15 17:08:26 infecticide postfix/smtpd[15543]: NOQUEUE: reject: RCPT from unknown[195.53.62.68]: 450 4.1.1 <itsanarb@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<itsanarb@jortosh.com> proto=ESMTP helo=<correo.teldat.com>
Apr 15 17:08:26 infecticide postfix/smtpd[15543]: disconnect from unknown[195.53.62.68]
Apr 15 17:08:26 infecticide postfix/smtpd[14988]: connect from corpmail4.seamlessdev.com[72.82.236.16]
Apr 15 17:08:26 infecticide postfix/smtpd[14988]: setting up TLS connection from corpmail4.seamlessdev.com[72.82.236.16]
Apr 15 17:08:27 infecticide postfix/smtpd[14988]: Anonymous TLS connection established from corpmail4.seamlessdev.com[72.82.236.16]: TLSv1 with cipher RC4-MD5 (128/128 bits)
Apr 15 17:08:27 infecticide postfix/smtpd[15574]: connect from 65-121-139-242.dia.static.qwest.net[65.121.139.242]
Apr 15 17:08:27 infecticide postfix/smtpd[14988]: NOQUEUE: reject: RCPT from corpmail4.seamlessdev.com[72.82.236.16]: 450 4.1.1 <+._-itsamerc_1974@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<+._-itsamerc_1974@jortosh.com> proto=ESMTP helo=<corpmail4.seamlessdev.com>
Apr 15 17:08:27 infecticide postfix/smtpd[15597]: connect from mail.fflawoffice.com[199.34.27.146]
Apr 15 17:08:27 infecticide postfix/smtpd[15319]: connect from 65-114-116-70.dia.static.qwest.net[65.114.116.70]
Apr 15 17:08:27 infecticide postfix/smtpd[15574]: setting up TLS connection from 65-121-139-242.dia.static.qwest.net[65.121.139.242]
Apr 15 17:08:27 infecticide postfix/smtpd[14988]: disconnect from corpmail4.seamlessdev.com[72.82.236.16]
Apr 15 17:08:27 infecticide postfix/smtpd[15597]: setting up TLS connection from mail.fflawoffice.com[199.34.27.146]
Apr 15 17:08:27 infecticide postfix/smtpd[15319]: NOQUEUE: reject: RCPT from 65-114-116-70.dia.static.qwest.net[65.114.116.70]: 450 4.1.1 <itizituk1982@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<itizituk1982@jortosh.com> proto=ESMTP helo=<rmtisa.NHCHI.LAN>
Apr 15 17:08:27 infecticide postfix/smtpd[15574]: Anonymous TLS connection established from 65-121-139-242.dia.static.qwest.net[65.121.139.242]: TLSv1 with cipher RC4-MD5 (128/128 bits)
Apr 15 17:08:27 infecticide postfix/smtpd[15597]: Anonymous TLS connection established from mail.fflawoffice.com[199.34.27.146]: TLSv1 with cipher RC4-MD5 (128/128 bits)
Apr 15 17:08:27 infecticide postfix/smtpd[15597]: NOQUEUE: reject: RCPT from mail.fflawoffice.com[199.34.27.146]: 450 4.1.1 <Morris-itsiuqca@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<Morris-itsiuqca@jortosh.com> proto=ESMTP helo=<ffmail1.fflawoffice.com>
Apr 15 17:08:28 infecticide postfix/smtpd[15319]: disconnect from 65-114-116-70.dia.static.qwest.net[65.114.116.70]
Apr 15 17:08:28 infecticide postfix/smtpd[15574]: NOQUEUE: reject: RCPT from 65-121-139-242.dia.static.qwest.net[65.121.139.242]: 450 4.1.1 <Celia-itsigami@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<Celia-itsigami@jortosh.com> proto=ESMTP helo=<dsm-server2.first-state-bank.net>
Apr 15 17:08:28 infecticide postfix/smtpd[15597]: disconnect from mail.fflawoffice.com[199.34.27.146]
Apr 15 17:08:28 infecticide postfix/smtpd[15574]: disconnect from 65-121-139-242.dia.static.qwest.net[65.121.139.242]
Apr 15 17:08:28 infecticide postfix/smtpd[15546]: connect from 216-64-161-214.static.twtelecom.net[216.64.161.214]
Apr 15 17:08:28 infecticide postfix/smtpd[15546]: setting up TLS connection from 216-64-161-214.static.twtelecom.net[216.64.161.214]
Apr 15 17:08:28 infecticide postfix/smtpd[15546]: Anonymous TLS connection established from 216-64-161-214.static.twtelecom.net[216.64.161.214]: TLSv1 with cipher AES128-SHA (128/128 bits)
Apr 15 17:08:28 infecticide postfix/smtpd[15546]: NOQUEUE: reject: RCPT from 216-64-161-214.static.twtelecom.net[216.64.161.214]: 450 4.1.1 <itnocdim_1965@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<vertrieb@jetreports.de> to=<itnocdim_1965@jortosh.com> proto=ESMTP helo=<OPAL.swpros.com>
Apr 15 17:08:28 infecticide postfix/smtpd[15546]: disconnect from 216-64-161-214.static.twtelecom.net[216.64.161.214]
Apr 15 17:08:29 infecticide postfix/smtpd[15337]: connect from ercilla.unapvic.cl[64.76.140.19]
Apr 15 17:08:29 infecticide postfix/smtpd[15337]: NOQUEUE: reject: RCPT from ercilla.unapvic.cl[64.76.140.19]: 450 4.1.1 <itnemogs_1990@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<itnemogs_1990@jortosh.com> proto=ESMTP helo=<ercilla.unapvic.cl>
Apr 15 17:08:30 infecticide postfix/smtpd[15337]: disconnect from ercilla.unapvic.cl[64.76.140.19]
Apr 15 17:08:30 infecticide postfix/smtpd[15572]: connect from dsl-202-45-116-106-static.VIC.netspace.net.au[202.45.116.106]
Apr 15 17:08:30 infecticide postfix/smtpd[15516]: timeout after RSET from ns.intecwash.navy.mil[138.145.2.3]
Apr 15 17:08:30 infecticide postfix/smtpd[15516]: disconnect from ns.intecwash.navy.mil[138.145.2.3]
Apr 15 17:08:31 infecticide postfix/smtpd[15572]: NOQUEUE: reject: RCPT from dsl-202-45-116-106-static.VIC.netspace.net.au[202.45.116.106]: 450 4.1.1 <itsiap_2001@jortosh.com>: Recipient address rejected: User unknown in local recipient table; from=<> to=<itsiap_2001@jortosh.com> proto=ESMTP helo=<trslsbs1.TraralgonRSL.local>
Apr 15 17:08:31 infecticide postfix/smtpd[15572]: disconnect from dsl-202-45-116-106-static.VIC.netspace.net.au[202.45.116.106]



```


I consistently have 5 - 10 connections to my mail server, this is eating up drive space and bandwidth as you can imagine.

What can I do to curb this?

---

### Post by lisati on 2009-04-15
If you can trap some of them, you can report them via [www.spamcop.net](www.spamcop.net)
I think the spamcop website also has some tips for configuring servers somewhere.

---

### Post by HermanAB on 2009-04-15
I use these three RBLs:
bl.spamcop.net
zen.spamhaus.org
dnsbl.ahbl.org

That takes care of about 90% of spam.  Spam Assassin gets the rest.

---

### Post by infecticide on 2009-04-15
Looks like what I'm encountering is a address harvest or directory harvest.

How do I configure the RBL's in postfix or postgrey?

---

### Post by infecticide on 2009-04-16
I've installed Postgrey but I'm confused by the log entries I'm seeing from it.

```

action=pass, reason=triplet found, client_name=www.allrecords.de, client_address=217.115.144.234, recipient=Mohamed-itnereg@domain.com

```


This would (at face value) suggest that the greylisting isn't working, its allowing this mail through.

Does anyone have any tips on this?

---

