---
title: "Ubuntu Postfix, Dovecot, MySQL, Roundcube - Configuration help ;)"
date: 2013-08-15
forum: Server Platforms
---

### Post by ktosi on 2013-08-15
Hi.

The first time I configure mail server. I use [https://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](https://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/) + Roundcube and a few other websites. I configured server by the tutorial but does not work properly. Well I have few questions:

1. By the tutorial my hostname should be my mail domain. Like mail.example.com But I don't sure what I should do when my domain is an alias for another DNS. i.e. My server is on windows azure and I use CNAME record to redirect to my azurename.cloudapp.net server. I don't know which url I should use as hostname. 
What name should I set if I have more domain connect with my mail server?? Like mail.domain1.com, domain1.com,  mail.domain2.com, ... ??

2. I configured all packages but don't work. I don't know how debug them. I can add user and domain with postfixadmin but sending emails don't run. I can not login by roundcube. I added the logs and server configs in attachments.

3. What should I do to my post don't be in spam folder??

Add desc:
a) In the mail.err file the most important error is: fatal: no SASL authentication mechanisms
b) the hostname was be replaced with --hiddenhostname-- ;)

I am hope someone know what can me help ;)

---

### Post by TheFu on 2013-08-15
Email can be complicated.
* The actual name of the mail server (hostname + FQDN) doesn't matter, what matters is that for every domain you want that server to accept email for, that the DNS MX record point to it.
* The easiest way to prevent spam is to run an email gateway. This machine's primary job is to refuse email that makes no sense for your domain(s). [http://www.howtoforge.com/configure-an-email-gateway-with-scrollout-f1-anti-spam-and-dlp](http://www.howtoforge.com/configure-an-email-gateway-with-scrollout-f1-anti-spam-and-dlp) explains.  Having an email gateway is also a best practice for email security.
* Your ISP must allow emails to be received and sent. If you are on a residential connection, the common ports are probably blocked.
* I've never used roundcube or mysql in relation to postfix. Sorry.
* Skimmed that guide - seems overly complex to me.
* I don't understand the third question. Sorry. If you don't want your email to end up in spam folders, there are lots of things - mainly, don't send spam, don't use servers to send email that others have used to spam with. Don't let other people use your server to send spam. Avoid getting on block lists, use SPF and DKIM.  Lots of other things, but those are the main ones.

"No SASL authentication"  Google found this: [http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html) should help. You probably already read that. Did you have a specific question?

---

