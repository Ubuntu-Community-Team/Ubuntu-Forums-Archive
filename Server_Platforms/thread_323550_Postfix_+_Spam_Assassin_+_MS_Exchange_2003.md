---
title: "Postfix + Spam Assassin + MS Exchange 2003"
date: 2006-12-22
forum: Server Platforms
---

### Post by jonathan.lees on 2006-12-22
Help! My boss at work is giving me grief about the amount penxx extension emails she gets on a daily basis.  I've read about the possibility of using Postfix to filter emails for spam/viruses and then forward valid ones to an Exchange server. I've tried to figure it out, but being a fair noob getting it running is really confusing. 

First I installed Postfix etc on a Ubuntu Server 6.06 as per the how to forge guide found [here]("http://www.howtoforge.com/ubuntu6.06_firewall_gateway").  But  there there is no info on configuring it to send valid mails to the Exchange server. More googling I found [this]("http://flurdy.com/docs/postfix/") setup guide for installing Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey.

Now I'm more confused, do I really need all this to filter spam. 

I'd like Postfix filter spam and send valid emails to only valid accounts on the exchange server. I'd also like to use postfix for some additional email accounts as we don't have too many Exchange cal's where users can access their emails using Squirrelmail. I don't care much for POP3 or IMAP.

Is this possible, has anyone done anything like this and if so can you help me out with the configs.

thanks

---

### Post by gfowler on 2006-12-22
Take a look at this.  I using it to an Exchange 2K server

[http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)

Jerry

---

