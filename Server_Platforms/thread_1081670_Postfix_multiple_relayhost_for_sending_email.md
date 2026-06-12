---
title: "Postfix multiple relayhost for sending email"
date: 2009-02-26
forum: Server Platforms
---

### Post by jamesab on 2009-02-26
Hello all, I'm new here and this is my first question posted. I have been using Ubuntu Server 8.10 for about 2 months now. Perhaps I should find a Postfix forum, but I thought there would be some guru's on this site that may be able to help.
Here's the issue:
I'm trying to set up Postfix to use an outgoing relay for sending email because I have a dynamic IP listed at spamhaus and my emails are rejected by almost all email recipients servers.  So anyway, I got Postfix all set up and it works when I give it the details for a single relayhost.  My problem is that I am hosting 3 different domains on the same server and each one uses the same relay host (secureserver.net through 3rd party cheapville.com) but with a different username/password.  Here are the settings I am using:

_main.cf_
smtp_sender_dependent_authentication = yes
    sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay
    smtp_sasl_auth_enable = yes
    smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
    relayhost = smtpout.secureserver.net

_sender_relay_
[email]email@server.com[/email] smtpout.secureserver.net
[email]email2@server2.net[/email] smtpout.secureserver.net
[email]email3@server3.com[/email] smtpout.secureserver.net

_sasl_passwd_
[email]email@server.com[/email] login_name: password
[email]email2@server2.net[/email] login_name: password
[email]email3@server3.com[/email] login_name: password

Now, the email addresses are correct and the usernames/passwords are also correct as per my account settings.  I did a postmap on both the sender_relay and sasl_passwd files before restarting the Postfix server.  Seems like it should be working, but I get a Bounced message each time from secureserver.net, I'm assuming because Postfix is not actually looking up the server/login info from the tables provided.  If I set it up to work with a single relayhost this way, it works:

_main.cf_
relayhost = smtp.secureserver.net
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

_sasl_passwd_
smtpout.secureserver.net login_name: password

P.S. I had to insert spaces after the colon to prevent a smilie insert, but the file has no space.

Does anyone have any advice on how to get this working?

Thanks,
James

---

### Post by jamesab on 2009-02-26
I just noticed this in my log and though it might be relevant.  Notice how the from=<> is blank... I was thinking it might be causing my look up to be wrong because it is supposed to look it up by sender, which shows blank.  I tried setting From: in the header of the email, but it looks the same still.

Feb 26 19:21:13 ubuntu postfix/qmgr[15006]: 1337AD39BD: from=<>, size=2260, nrcpt=1 (queue active)
Feb 26 19:21:13 ubuntu postfix/bounce[16082]: 11025D39BB: sender non-delivery notification: 1337AD39BD
Feb 26 19:21:13 ubuntu postfix/qmgr[15006]: 11025D39BB: removed
Feb 26 19:21:14 ubuntu postfix/smtp[16081]: 1337AD39BD: to=<www-data@my-server.com>, relay=smtpout.secureserver.net[64.202.165.58]:25, delay=0.96, delays=0.01/0/0.72/0.22, dsn=5.0.0, status=bounced (host smtpout.secureserver.net[64.202.165.58] said: 553 Sorry, that domain isn't in my list of allowed rcpthosts. (in reply to RCPT TO command))

---

### Post by csurlee on 2009-02-26
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")

I hope helps ;)

---

### Post by jamesab on 2009-02-26
OK, so Postfix is working.  I just verified by sending an email through my inbox in Postfix from 2 diff server addresses and it is relaying properly through smtpout.secureserver.net and shows Accepted in the mail log.  So that's great news I guess.  

I suppose it's a problem with PHP then?  Anyone with advice on this?

Thanks.

---

### Post by jamesab on 2009-02-26
> **csurlee said:**
> [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")

I hope helps ;)

Thanks, I am browsing that right now.  

However I forgot to mention that I am only using Postfix to relay server generated emails from my web sites with PHP mail().  My clients connect to secureserver.net through to send and receive.

---

### Post by jamesab on 2009-02-26
Not sure why this isn't working with the default PHP function, but I was able to get it working using the additional_parameters option.

Looks like this:  mail($to, $subject, $message, $headers, "-fsender@server.com");

Yes, that's right no space between -f and sender email address.

Thanks for looking and hopefully this will help someone else in the future.

---

