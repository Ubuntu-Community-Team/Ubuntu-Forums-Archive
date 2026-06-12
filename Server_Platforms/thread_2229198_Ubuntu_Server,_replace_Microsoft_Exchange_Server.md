---
title: "Ubuntu Server, replace Microsoft Exchange Server?"
date: 2014-06-11
forum: Server Platforms
---

### Post by kmccmk9 on 2014-06-11
Hello, if I have a ubuntu server installation, what packages can I install that would turn my simple ubuntu server into a microsoft exchange server replacement? What I am looking for it mail server, calandar sync, task sync, addressbook sync and mobile device support.

---

### Post by Bucky Ball on 2014-06-11
*Thread moved to **Server Platforms**.*

---

### Post by volkswagner on 2014-06-12
This is a much talked about subject with much info on the net. I suggest you do some research and come back with more specific questions.

[Here is an article]("http://www.smallbusinesscomputing.com/biztools/article.php/10730_3932591_2/Top-5-Open-Source-Alternatives-to-Microsoft-Exchange.htm") that talks about the top 5 alternatives to Exchange server.

Good luck.

---

### Post by Lars Noodén on 2014-06-12
[Kolab](http://kolab.org/) and [Citadel](http://www.citadel.org/) can be installed in Ubuntu and are built of components from the repository.  There is also [OpenChange](http://doc.zentyal.org/en/openchange.html) which is supposed to be a drop-in replacement.  All three would need modification if you rely on a certain percentage of mail loss and delay (e.g. plausible deniability) from the old system.

---

### Post by kmccmk9 on 2014-06-12
> **volkswagner said:**
> This is a much talked about subject with much info on the net. I suggest you do some research and come back with more specific questions.

[Here is an article]("http://www.smallbusinesscomputing.com/biztools/article.php/10730_3932591_2/Top-5-Open-Source-Alternatives-to-Microsoft-Exchange.htm") that talks about the top 5 alternatives to Exchange server.

Good luck.

I have done much research on the topic and I too had found that article. However, when investigating those services, they all were mostly just free trials.

> **Lars Noodén said:**
> [Kolab]("http://kolab.org/") and [Citadel]("http://www.citadel.org/") can be installed in Ubuntu and are built of components from the repository. There is also [OpenChange]("http://doc.zentyal.org/en/openchange.html") which is supposed to be a drop-in replacement. All three would need modification if you rely on a certain percentage of mail loss and delay (e.g. plausible deniability) from the old system.

I have looked at Kolab and so far it seem sto be the closest. But, I'm trying to see how I could integrate the various clients (like mobile). There is a Android Sync (no iphone) but I don't see much spec on actually mail use. Citadel also looks nice and they blatantly list POP3, IMAP, SMTP protocol support so mobile devices shouldn't be a problem there. Sadly Zentyal isn't free (or at least it wouldn't be for me).

---

### Post by nerdtron on 2014-06-12
How about the easy install iRedMail? Fast and easy.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

### Post by kmccmk9 on 2014-06-13
> **nerdtron said:**
> How about the easy install iRedMail? Fast and easy.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

Oh wow that does look nice too. But does it have calendar sync? Also can you explain this piece a bit more?

[TABLE="width: 1034"]
[TR]
[TH]Service[/TH]
[TH]Per-user support[/TH]
[TH]Per-domain support[/TH]
[/TR]
[TR]
[TD]Mail service[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[/TR]
[TR]
[TD]Monitor incoming/outgoing mails with BCC[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD]Check[/TD]
[/TR]
[TR]
[TD]Sending mail via SMTP, fetching mail via POP3/IMAP[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Sending mail vai SMTPS (SMTP over TLS/SSL), fetching mail via POP3S/IMAPS[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Receiving mail[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Mail forwarding[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Customize mail filter rule[/TD]
[TD][IMG]http://www.iredmail.org/images/enabled.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="colspan: 3"]**Note: *Mail service*** means all mail related services, include POP3, IMAP, SMTP and other services listed above.[/TD]
[/TR]
[/TABLE]

---

### Post by tripp98 on 2014-06-13
Zimbra is one to look at for drop in replacement.

---

### Post by kmccmk9 on 2014-06-13
> **tripp98 said:**
> Zimbra is one to look at for drop in replacement.

Zimbra is only a free trial for their collaboration I thought?

---

### Post by nerdtron on 2014-06-13
Can't do calendar sync on iRedMail Roundcube.

+1 for Zimbra I tried it also when searching for an email solution. It is one of the heavyweights. It also has a free editions. I'm not quite sure if what you are looking for is included on the free version.

---

