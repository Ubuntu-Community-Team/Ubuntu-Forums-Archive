---
title: "backup email server"
date: 2014-10-16
forum: Server Platforms
---

### Post by atux on 2014-10-16
hello everyone. in my server i am running an email server with postfixadmin, dovecot, roundcube. the domain is  mail.abcxyz.com with priority 10 at IP 1.1.1.1.
when user is mobile can access webmain from mail.abcxyz.com/webmail. when at desktop it can be reached from email clients.
i am running a second identical machine as mail**2**.abcxyz.com priority 20 at IP 2.2.2.2. when first server is down the second receives the messages, but users will not be able to send receive until mail.abcxyz.com is up and running.
i am thinking to have both machine as mail.abcxyz.com the first with priority 10 at IP 1.1.1.1 and the second with priority 20 at IP 2.2.2.2. both named as mail.abcxyz.com. i have not tried that since the machines are in production and i would like to ask your optinion.

---

### Post by Michael_McKenney on 2014-10-16
How are you replicating mail between two servers?  You need replication setup first.  You need MX records setup for both servers with proper priorities?  Mail will come into one server.  You need replication.   On Exchange, you setup clustering with a common SAN location that the two server share mailboxes.  So you need Microsoft clustering licensing for both OS and Exchange.  You should be able to send/receive from either active mail server.

---

### Post by atux on 2014-10-17
i am not replicating at the moment. this is what i am looking to do and ask for help.

---

### Post by SeijiSensei on 2014-10-17
Read [http://www.linux-ha.org/wiki/Main_Page](http://www.linux-ha.org/wiki/Main_Page).  I'd suggest building a couple of virtual machines and seeing how well you do at replicating them before trying it in production.

---

### Post by TheFu on 2014-10-17
There are 2 aspects.  MTA for server-2-server and user access via SMTP and IMAP.

The server-2-server stuff is handled by the MX records.  Those can be trivial MTA gateways that accept good stuff, bounce bad things and forward real emails to specific back end systems.

For the client/user access, use a VIP on the front end for web/IMAP access (nginx or ha-proxy). Nominal clustering with failover will handle this - easier with SAN storage shared by the 2+ systems. That avoids block-level replication.  It really depends on where the mail systems are 'network-wise" - close or far.  Authenticated SMTP goes thru the MTA gateways, so those can be almost anywhere on the internet to provide receiving redundancy.

Disclosures:
I have redundant front-end MTA servers, but not a redundant user-interface/IMAP server.  We've decided that solid daily backups of the main user-email server is enough for our business requirements.  Haven't had any terrible issues in a decade with this method.  A larger business would need an active-standby setup or multiple user-mail systems each with a failover facility.  I've tested the backup restores and can have a new VM built in 30 min and ready to go in an hour from nothing. It shouldn't be too hard for me to automate taking the nightly backup data and scripting a restore into a different VM daily. That would make the failover/switchover during business just an IP swap.  

Oh - and we run Zimbra.

---

