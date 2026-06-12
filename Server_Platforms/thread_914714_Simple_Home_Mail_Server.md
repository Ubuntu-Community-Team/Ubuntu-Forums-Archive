---
title: "Simple Home Mail Server"
date: 2008-09-09
forum: Server Platforms
---

### Post by colskinet on 2008-09-09
Hi

I would like to setup a server that hosts a basic website, but more importantly is responsible for the sending and receiving of my email.

I have a domain name that I own and have full control over DNS, etc. I would like to use this domain name on my mail/web server but have seen several guides, all of which seem very complex (I also have Exchange available to me but don't like the overheads/system resources that it uses in Windows 2k3).

So, to sum up, I'd like a nice easy to setup mail server that is easy to configure - i.e. add/delete users, setup forwarders, etc.

My clients would be using Outlook/Outlook Express to connect to the mail server.

Anyone have any recommendations/step by step guides?

Thanks in advance.

Colin

---

### Post by devonps on 2008-09-09
Hi,

I've recently installed [www.citadel.org](www.citadel.org) which can do all of the things you mention and some more. This was a first install for me, it took about 20 mins and went very smooth.

You may want to look at Zimbra as an alternative - I've not used that solution but it was recommended to me along with Citadel.

Hope this helps,

Steve.

I forgot to mention, I used the EasyInstall version of Citadel and that's the reason why things went so smooth for me.

---

### Post by Greyed on 2008-09-09
First step before anything else would be to see if your ISP allows such things on a home connection.

---

### Post by lenswipe on 2008-09-09
> **Greyed said:**
> First step before anything else would be to see if your ISP allows such things on a home connection.

colskinet: i know mine doesnt - if you are with Orange Broadband like me then forget it.

---

### Post by colskinet on 2008-09-09
> **Greyed said:**
> First step before anything else would be to see if your ISP allows such things on a home connection.

Hi

Yes I am allowed to do all of this - I am with Plus.net in the UK.

devonps - thanks, sounds like the kind of thing I am after, will have a look at that!

Colin

---

### Post by schettj on 2008-09-09
I use postfix + clamav + spamassassin. There are ubuntu howtos. I'm not a rookie (used to run sendmail - shudder) but even for a rookie the postfix guides for ubuntu are pretty easy.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

(advanced)
[http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)

(geek)
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Have fun. Make sure you're not an open relay. Do set up your SPF record ([http://en.wikipedia.org/wiki/Sender_Policy_Framework](http://en.wikipedia.org/wiki/Sender_Policy_Framework)) - enjoy battling spam. Set up fail2ban to block brute force SMTP username/password attacks. Have fun...

---

### Post by lazyart on 2008-09-09
I've used both Citadel and Zimbra.  Citadel was quicker to set up (ok, maybe I cheated because I downloaded the virtual appliance and threw it in VMware).  Zimbra has a lot prettier web interface, but that is of little consequence here.  I also felt Zimbra gives you more control over accounts.  Hosting additional domains (if you felt like it) is a snap.

Note that while the both have groupware functions, you need a special (read "non-free") connector to use them in Outlook.  You could use the free Zimbra Desktop for Windows (or Linux) and have access to all the extra goodies Zimbra has to offer.

As above, make sure you're not an open relay.  There are spam filtering services available when you have your own domain.  I haven't needed one yet but I know someone who uses spamstopshere and say they catch everything.

There are also services to catch your mail in case you have a server outage and then deliver it later for you.  Something else to consider. :)

---

### Post by scurlaruntings on 2008-09-10
Hopefully one of you guys can help me. Im trying to set up a mail server that can POP email from 1and1 inject that into postfix and then allow a MUA to recieve and send mail from that server. Do i require Dovecot to use IMAP/POP3 as i cant see anything natively within Postfix to configure IMAP/POP3 access for clients. Also im using fetchmail to retrieve the emails from 1and1 how do i then configure this to inject the email into Postfix? Is this setup possible i guess may be the right question. Please note i am a windows exchange admin so the world of Linux is pretty new to me.:(

---

### Post by lazyart on 2008-09-10
> **scurlaruntings said:**
> Hopefully one of you guys can help me. Im trying to set up a mail server that can POP email from 1and1 inject that into postfix and then allow a MUA to recieve and send mail from that server. Do i require Dovecot to use IMAP/POP3 as i cant see anything natively within Postfix to configure IMAP/POP3 access for clients. Also im using fetchmail to retrieve the emails from 1and1 how do i then configure this to inject the email into Postfix? Is this setup possible i guess may be the right question. Please note i am a windows exchange admin so the world of Linux is pretty new to me.:(

We can help you, but please create a new thread instead of hijacking another.

---

### Post by scurlaruntings on 2008-09-10
> **lazyart said:**
> We can help you, but please create a new thread instead of hijacking another.
Oops sorry. I thought it would be easier to append it to this one..:confused:

---

