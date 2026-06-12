---
title: "help with postfix &amp; courier &amp; dynamic IP"
date: 2007-02-03
forum: Server Platforms
---

### Post by bspratt on 2007-02-03
I have put together an Edgy server with Apache2; proftpd (hosting web sites just fine) then the mail server: Postfix, Courier, Greylist, ClamAV, Spam Assassin, Squirrel and Fetchmail. The problem: The mail components all pass their individual tests. However, I did noticed my outgoing mail being rejected by my ISP (Roadrunner) because they don't allow dynamic IP servers. I did set up the no-ip client and the address only changes maybe twice a year. Is there not some way to bypass my local SMTP component and tell PostFix just to go out to the Roadrunner SMTP server? Also what do I have to configure to get Postfix to deliver the mail in queue to the actual mailboxes on the mail server (user home folders)? Thanks in advance for any help or direction to docs on this - Bill

---

### Post by bspratt on 2007-02-03
I think I found the answer to first question - falko's relaying postfix below:
[http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)
Still, I have mail in my Postfix queue and it doesn't seem to go anywhere. Need it to be delivered to my mail boxes. What needs to be configured to do this please?  Thanks - Bill

---

