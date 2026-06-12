---
title: "Sending Mail to External Email"
date: 2010-04-14
forum: Server Platforms
---

### Post by Nascentes on 2010-04-14
I have looked everywhere and scoured posts and guides looking for a solution but I cannot for the life of me find one : /

I just setup a mail server on my web server and I cannot for the life of me figure out how to send emails to external(as in outside my LAN) emails or receive from external emails.

I'm using Postfix with Dovecot and Squirrelmail.

I get this delivery report in Squirrelmail when trying to send an email to my hotmail address
> 
Final-Recipient: rfc822; [example@hotmail.com]("http://atk-studios.com/squirrelmail/src/compose.php?send_to=un.daunted%40hotmail.com")
Action: failed
Status: 5.0.0
Remote-MTA: dns; mx3.hotmail.com
Diagnostic-Code: smtp; 550 DY-001 Mail rejected by Windows Live Hotmail for
    policy reasons. We generally do not accept email from dynamic IP's as they
    are not typically used to deliver unauthenticated SMTP e-mail to an
    Internet mail server. [http://www.spamhaus.org]("http://www.spamhaus.org/") maintains lists of dynamic
    and residential IP addresses. If you are not an email/network admin please
    contact your E-mail/Internet Service Provider for help. Email/network
    admins, please visit [http://postmaster.live.com]("http://postmaster.live.com/") for email delivery information and support    


If you need more information let me know....

Thanks ahead of time

---

### Post by HermanAB on 2010-04-15
Two things are usually wrong:
1. Your DNS must have A, MX and PTR records.
2. Your ISP must allow port 25 outgoing.

Test the DNS setup with 'dig'.

Pay your ISP an extra $10 per month for a 'server' account, or forward your outgoing mail via their mail server using the postfix 'smarthost' feature.

---

### Post by KB1JWQ on 2010-04-15
Technically, smarthost is a sendmail-ism.  

Postfix uses the relayhost option. :-)

---

### Post by hictio on 2010-04-15
What HermanAB said, and on top of that, be aware that if you are mailing to a Hotmail account, unless the person you are mailing to has your email address on his/ her address book, it is pretty likely that your email will end on the Hotmail Spam directory of that account.

For sending emails from your box, another option you might consider is using [ssmtp](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/).

---

