---
title: "Problems with Hylafax and Avantfax"
date: 2009-03-21
forum: Server Platforms
---

### Post by farebalk on 2009-03-21
Hi guys,

I just finished installing Hylafax and Avantfax on Ubuntu Server 8.10, but both have problems sending a fax, and I couldn't configure properly that when I recive a fax immediately send by email.

When I acces to Avantfax, this appears:
ttyS0 [Please wait]

When I try to send a fax, syslog sends me the following message:
send_mail> ':-( rejected fax: 229 15.03.2009 18:20' sent to 'prueba@test.com' from 'prueba2@test.com' - /var/www/avantfax/tmp/2009-03-15-229-182044/fax.pdf (229.pdf)

In the syslog server:
Mar 15 18:24:18 fax FaxQueuer[5508]: SUBMIT JOB 9
Mar 15 18:24:18 fax FaxQueuer[5508]: JOB 9: 
Mar 15 18:24:18 fax FaxQueuer[5508]: NOTIFY: bin/notify.php "doneq/q9" "rejected" ""
Mar 15 18:24:21 fax FaxQueuer[5508]: NOTIFY exit status: 0 (5893)
Mar 15 18:24:21 fax postfix/pickup[5601]: 07AD06C43C: uid=10 from=<prueba2@test.com>
Mar 15 18:24:21 fax postfix/cleanup[5907]: 07AD06C43C: message-id=<20090315232421.07AD06C43C@fax.zen>
Mar 15 18:24:21 fax postfix/qmgr[5603]: 07AD06C43C: from=<prueba2@test.com>, size=55385, nrcpt=1 (queue active)
Mar 15 18:24:53 fax postfix/smtp[5909]: warning: 07AD06C43C: non-ESMTP response from aspmx.l.google.com[74.125.45.27]:25: 0- [] Our system has detected an unusual amount of unsolicited mail
Mar 15 18:24:53 fax postfix/smtp[5909]: warning: to prevent loss of mail, turn off command pipelining for 74.125.45.27 with the smtp_discard_ehlo_keyword_address_maps parameter

Mar 15 18:24:53 fax postfix/smtp[5909]: 07AD06C43C: to=<prueba1@test.com>, relay=aspmx.l.google.com[74.125.45.27]:25, delay=33, delays=0.2/0.02/0.62/32, dsn=2.0.0, status=sent (0- [] Our system has detected an unusual amount of unsolicited mail 0- originating from your IP address. To protect our users from spam, 0- mail sent from your IP address has been . Please visit [http://www.goo](http://www.goo) 0- gle.com/mail/help/bulk_mail.html to review our Bulk Email Senders 0  Guidelines. 9si2518256yxs.56 221 2.0.0 closing connection 9si2518256yxs.56)
Mar 15 18:24:53 fax postfix/qmgr[5603]: 07AD06C43C: removed

I configure an SMTP server in config.php and I don't know why still appear these messages of google.

When I acces to Avantfax add the modem as follows:
Device:/dev/ttyS0
Alias:ttyS0
Contact:prueba1@test.com

And I try to create a file FaxDispatch and add this:
sento=prueba1@test.com
type=tif;

But with any of the two settings I don't receive any e-mail.

Sorry for any misspellings but I am just learning English and I'm helping with the google translator.

---

### Post by HermanAB on 2009-03-21
Hmm, you are on your own with this.  The problem is that fax machines are going the way of the Dodo.  You should try Google, maybe it can dig something up.

Cheers,

Herman

---

### Post by cariboo on 2009-03-21
Can you actually send a fax to another fax machine?

@HermanAB

We may all want faxes to disappear, but I know several local businesses that depend on fax machines to do business. My last employer just plain wore out 3 fax machnes in the 2½ years I for worked for them. Just before I left I purchased a higher end HP for them, and they are still using the same machine 1 year later.

Jim

---

### Post by lptr on 2009-07-06
Having an ISDN based (FritzCard using) HylaFAX machine running on Jaunty (9.04 server) under my table. The machine here is newly setup. Hylafax is working smoothly with WHFC (Windows HylafaxClient). I am close to install Avantfax on it. 

As of avantfax-3.1.6 comming with nearly no description for things needed to be done BEFORE this debian installer script is run I am curious if anyone successfully used this installer on a recent server installation and if there are some pitholes that can be avoided?

Another info lacking is if WHFC can be run in parallel with it?

Any infos would be great.

/rob*

---

