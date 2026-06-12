---
title: "Mail server spaming"
date: 2008-10-03
forum: Server Platforms
---

### Post by elvinatom on 2008-10-03
I recently sent an email that got rejected by a host that previously had no problems with my emails.  The given reason was "Connection refused due to abuse".  The log was filled with entries that I cannot interpret, all at times when no message was received or sent (at least not by any legitimate user).

```
Oct  3 13:23:41 mymailserver postfix/anvil[10268]: statistics: max connection rate 1/60s for (smtp:66.163.168.155) at Oct  3 13:17:25
Oct  3 13:23:41 mymailserver postfix/anvil[10268]: statistics: max connection count 1 for (smtp:66.163.168.155) at Oct  3 13:17:25
Oct  3 13:23:41 mymailserver postfix/anvil[10268]: statistics: max cache size 2 at Oct  3 13:18:03
Oct  3 13:23:56 mymailserver postfix/qmgr[8375]: EC1CE1560C8: from=<>, size=5919, nrcpt=1 (queue active)
Oct  3 13:23:56 mymailserver postfix/qmgr[8375]: EFE421560A7: from=<>, size=3358, nrcpt=1 (queue active)
Oct  3 13:23:56 mymailserver postfix/qmgr[8375]: 8D4A91560BE: from=<>, size=3149, nrcpt=1 (queue active)
Oct  3 13:23:56 mymailserver postfix/qmgr[8375]: DDF8B1560A8: from=<>, size=3092, nrcpt=1 (queue active)
Oct  3 13:23:57 mymailserver postfix/smtp[10407]: DDF8B1560A8: to=<tengel@eqm.com>, relay=mail.eqm.com[66.161.160.174]:25, delay=193235, delays=193235/0.06/0.47/0, dsn=4.0.0, status=deferred (host mail.eqm.com[66.161.160.174] refused to talk to me: 554 Service unavailable; Client host [pc-11-61-215-24.sta.myisp.net] blocked using Barracuda Reputation; http://bbl.barracudacentral.com/q.cgi?ip=--my-server-ip-address--)
Oct  3 13:23:57 mymailserver postfix/smtp[10405]: EFE421560A7: to=<dwsusqsfm@susqsf.com>, relay=barracuda.cumulus.com[216.234.1.139]:25, delay=185025, delays=185025/0.04/0.42/0.31, dsn=4.4.2, status=deferred (lost connection with barracuda.cumulus.com[216.234.1.139] while sending RCPT TO)
Oct  3 13:23:57 mymailserver postfix/smtp[10406]: 8D4A91560BE: host srv3-sao.sao.terraempresas.com.br[200.154.117.76] refused to talk to me: 450 Client host rejected: cannot find your hostname, [--my-server-ip-address--]
Oct  3 13:23:58 mymailserver postfix/smtp[10406]: 8D4A91560BE: to=<ijxxekadi@brancoperes.com.br>, relay=mx-sec.terraempresas.com.br[200.154.117.76]:25, delay=231155, delays=231153/0.05/1.8/0, dsn=4.0.0, status=deferred (host mx-sec.terraempresas.com.br[200.154.117.76] refused to talk to me: 450 Client host rejected: cannot find your hostname, [--my-server-ip-address--])
Oct  3 13:24:26 mymailserver postfix/smtp[10404]: connect to sterlingsavingsbank.net[12.19.55.215]:25: Connection timed out
Oct  3 13:24:26 mymailserver postfix/smtp[10404]: EC1CE1560C8: to=<updates@sterlingsavingsbank.net>, relay=none, delay=348796, delays=348766/0.04/30/0, dsn=4.4.1, status=deferred (connect to sterlingsavingsbank.net[12.19.55.215]:25: Connection timed out)
```

Any help would much appreciated!

---

### Post by y@w on 2008-10-03
Do you have an A record for your mail server at the IP the connections are coming from? It looks like the remote mail server is doing a lookup on your hostname and not getting an IP back. 

[http://isp.vail.net/reverse-dns.html](http://isp.vail.net/reverse-dns.html)

---

### Post by elvinatom on 2008-10-03
Please forgive my ignorance, but how do I check for that?
Besides, the domains my mail server is talking with are completely unknown to anyone who's got 'legitimate' access to it.  "sterlingsavingsbank.net", that means nothing to me are they trying to send to me or relay?

---

### Post by y@w on 2008-10-03
On the server, run 'hostname'.

In your case it should return something like "mail.sterlingsavingsbank.net". 

Then you should be able to dig that hostname from outside the network. Post it here and I can try it as well.

I'm doing dig's on your domain and am not showing an MX record associated with it.. Does this server receive messages for that domain?

---

### Post by y@w on 2008-10-03
Oops, double post..

---

### Post by elvinatom on 2008-10-03
sterlingsavingsbank.net is a foreign domain and i don't know what they want with us.  Our mail server is "lucy.rmeg.ca"

---

### Post by y@w on 2008-10-03
Ok, sorry I read it the opposite way. It looks like someone tried to send a bunch of messages to junk addresses and they're sitting in the mail queues and trying to deliver. As the postfix user, run 'mailq' and it will dump the messages waiting to go out.

---

### Post by elvinatom on 2008-10-03
Thank you very much ...
While looking at the queue - some remote servers refused to talk to our mail server because of reputation (Barracuda).

It seems that our mail server has been compromised, is that correct?

Is there a simple way to allow only emails being sent from within our lan?

---

### Post by y@w on 2008-10-03
> **elvinatom said:**
> Thank you very much ...
While looking at the queue - some remote servers refused to talk to our mail server because of reputation (Barracuda).

It seems that our mail server has been compromised, is that correct?

Is there a simple way to allow only emails being sent from within our lan?

Well, it may or may not have been.. How many is some? I'd run your mail server through the blacklist checks at [http://www.mxtoolbox.com](http://www.mxtoolbox.com). There are other blacklist checkers to use, but I don't remember any others off hand.
I did run your server through an open relay check and it appeared it wasn't an open relay.. You could have had a user's account get compromised or a user that did something dumb. :)


All the mail systems I deal with of late have been Zimbra, so I'm not entirely sure where the config file for this is located, but.. it's called 'mynetworks' in postfix.

---

### Post by elvinatom on 2008-10-03
Thank you for your reply.  I really appreciate your taking the time to help me.

37 messages are queued and 6 of them are rejected by barracuda reputation.  

So, you're positive that our mail server does not act as an open relay?  That's a good thing, I guess.  Can I find out which user tried to sent out the messages in the queues?

I am looking into locating 'mynetworks' right now.

---

### Post by y@w on 2008-10-03
I'm pretty sure it's not an open relay.. I ran it through the checker on mxtoolbox's website. There's a number of others out there. It would probably be worthwhile to try it on your own. The messages should show the sender address in the mailq list. You can request that your IP be removed from the Barracuda blacklist here: [http://www.barracudacentral.org/rbl/removal-request](http://www.barracudacentral.org/rbl/removal-request)

---

### Post by elvinatom on 2008-10-03
here it is ...

/etc/postfix/main.cf
```
...
mynetworks = 127.0.0.0/8
...
```

---

### Post by y@w on 2008-10-03
Ok, everyone else has to authenticate besides from the localhost.

---

### Post by elvinatom on 2008-10-03
Thank for that link - I'll need that once I put a stop to this.  My last issue that remains is finding the user that does it.  

Here's a sample of the mailq:
```
4D8C21560C0     5955 Tue Sep 30 12:55:12  MAILER-DAEMON
       (connect to sterlingsavingsbank.com[12.19.55.215]:25: No route to host)
                                         netbanker@sterlingsavingsbank.com

488681560C5     4566 Mon Sep 29 13:19:16  MAILER-DAEMON
(host barracuda.sunserver.com[209.240.72.75] refused to talk to me: 554 Service unavailable; Client host [pc-11-61-215-24.sta.mountaincable.net] blocked using Barracuda Reputation; http://bbl.barracudacentral.com/q.cgi?ip=24.215.61.11)
                                         dwwhitebearvolleyballm@whitebearvolleyball.org

4D2A51560B0     4103 Fri Oct  3 10:50:55  MAILER-DAEMON
                (connect to aaael.com[209.210.60.51]:25: Connection timed out)
                                         atfob@aaael.com

4D81E1560AC     4256 Sun Sep 28 17:56:39  MAILER-DAEMON
  (lost connection with mail.hoogvliet.com[83.80.24.38] while sending RCPT TO)
                                         r.lagerweij@hoogvliet.com

789D21560C3     3247 Mon Sep 29 12:08:23  MAILER-DAEMON
(lost connection with mail.ultralink.com[216.34.193.45] while sending RCPT TO)
                                         dwultralinkm@ultralink.com

01C001560AF     3791 Thu Oct  2 09:08:56  MAILER-DAEMON
               (connect to mail.tank.no[217.13.30.238]:25: Connection refused)
                                         dwtankdesignm@tankdesign.no

06CB91560AA     3676 Mon Sep 29 04:32:33  MAILER-DAEMON
(lost connection with mailgate.sc2000.net[64.88.197.254] while sending RCPT TO)
                                         dwsuperioralarmsm@superioralarms.com

-- 167 Kbytes in 37 Requests.
```

---

### Post by y@w on 2008-10-03
No route to host and connection refused is probably a non-existent email address or hostname. If you're sure those messages are junk you can clear the queue [http://www.rigadicomando.org/node/49](http://www.rigadicomando.org/node/49)


Check out this article as well regarding the Mailer Daemon messages:
[http://en.wikipedia.org/wiki/Mailer-Daemon](http://en.wikipedia.org/wiki/Mailer-Daemon)

---

### Post by elvinatom on 2008-10-03
Thank's a bunch.  I'll check that out.

---

