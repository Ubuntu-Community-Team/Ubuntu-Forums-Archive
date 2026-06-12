---
title: "Mail server and no-ip dynamic dns"
date: 2006-02-22
forum: Server Platforms
---

### Post by mr_mojo_risin on 2006-02-22
Is it possible to run a mail server with out a real domain.  I'm using no-ip to update my website, ftp, and gnump3d servers, and it works flawlessly.  I'm also running squid as well.  I want to set up a mail server next and wanted to know if it would work with a dynamic host name.  Thanks for the help!

---

### Post by robert_pectol on 2006-02-23
Somewhat possible, but not practical! :)  Here's why:

1. Many dynamic DNS services don't allow or provide MX entries in their zone file, for your domain.  Although not absolutely required per se, MTAs trying to deliver mail to your domain will first be looking for the MX record(s) for it, in order to know which IP your mail exchanger is listening on.  Also, be prepared to lose some mail due to the fact that you're on a dynamic IP.  The reason for this is that your cached IP to name mapping in the DNS cache of any mail servers (and/or associated DNS servers) which have delivered, or attempted to deliver mail to you in the past, will probably be stale because your IP is dynamic and will possibly have changed to another since then.  When the delivering MTA attempts to deliver mail and gets a TCP reset from whomever happens to now be assigned your old IP, the mail will be deferred.  You can only hope that the DNS cache for that MTA (and/or associated DNS servers) expires before the deferred mail becomes a permanent failure and is considered undeliverable!  It's not a gamble too many are willing to take!

2. If you plan on sending mail directly to other MTAs instead of via a smarthost (such as your ISP's mail server), then be prepared to have considerable amounts of un-deliverable mail!  Many administrators refuse to accept mail that comes from residential dial-up, DSL, and Cable modem pools because of the high probability that it is spam and/or UCE.

3. Your ISP has to allow inbound SMTP connections, to your dynamic IP, on port 25.  Many don't.  They'll also have to allow outbound SMTP connections from your dynamic IP, to port 25.  Most don't anymore.  They only allow connections to their SMTP server while blocking all other outgoing traffic destined for port 25.  This is to protect them from from the fallout of their users sending out spam.  By forcing their users to send via their mail server, they can enforce mail policies, limits, etc.

For those reasons, and probably some I've missed, it really isn't too practical to do it.  If you really want to run a full service mail server, it really ought to be on a static IP.

---

### Post by mr_mojo_risin on 2006-02-23
Thanks for the advice.  My current isp will not give me a static ip unless I set up a business account.  I could get one if i switched to dsl, but I just bought a cable modem.  Thanks again.

---

### Post by MJN on 2006-02-23
.

---

### Post by uopjohnson on 2006-02-23
I have this going without any problems.  I use the excelent dynamic dns services over at [http://www.dnsmadeeasy.com/](http://www.dnsmadeeasy.com/) which also allows you to set mx records and you can purchase backup protection in case you have an outage.  You will want to send your outgoing mail through you ISPs smart host, which is also very easy to set up.

---

