---
title: "Postfix problems on Ubuntu Server 7.10 - Postgrey and reject_unverified_sender"
date: 2008-04-02
forum: Server Platforms
---

### Post by PcPixel on 2008-04-02
I have been tasked with setting up a new email server at work to replace our aging sendmail box. Initially, I was testing Postfix on CENTOS 5.1 but am repeating the tests on Ubuntu Server 7.10 (I'm going to try to pressure my boss to let me use Ubuntu Server 8.04LTS as the production server).

First, on Ubuntu the reject_unverified_sender option fails. According to the book, if I add this to smtpd_recipient_restrictions it should send a challenge email to any incoming emails. The example in the book also states to place the database file thus: 
address_verify_map = btree:/var/spool/postfix/verified_senders

I can't get it to issue the challenge or create this file.I thought it might have been a permissions issue, but even if i put the file in a folder owned by postfix:postdrop it doesn't work. I am not using the permit_mynetworks pararameter so all my restrictions should be applied to everyone. Why is this happening?

Second, since I couldn't get that to work, I figured I would attempt to use postgrey since it would achieve a similar result. I installed postrey:
sudo apt-get install postgrey
and I followed an online howto that said all I needed to do was add: check_policy_service inet:127.0.0.1:60000
and that should do it. If I look at the mail.log, I can see that postgrey is in fact being started, but no greylisting is occuring at all. What could be the problem?

---

