---
title: "Howto verify user/pass is encrypted during mail login?"
date: 2007-01-25
forum: Server Platforms
---

### Post by mlcampbe on 2007-01-25
I'm setting up a mail server on ubuntu 6.1 server and have pretty much gotten it to work using flurdy's instructions and a few others I found in the help and google.

I can send/receive mail and I have tried to configure postfix so that road-warrior users can send mail via the server after entering their user/pass.  To do this I configured the /etc/postfix/sasl/smtpd.conf file as follows:

pwcheck_method: saslauthd
mech_list: PLAIN LOGIN

I can now send mail (at least internally) using no password or if I configure the email client to require an outgoing password. I am concerned though that the user/pass is transmitted in clear text even though I specified TLS mode. In the mail.log file I see the following when sending mail:

Jan 25 15:10:07 mail postfix/smtpd[4716]: connect from unknown[192.168.1.102]
Jan 25 15:10:07 mail postfix/smtpd[4716]: setting up TLS connection from unknown[192.168.1.102]
Jan 25 15:10:07 mail postfix/smtpd[4716]: TLS connection established from unknown[192.168.1.102]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jan 25 15:10:07 mail postfix/smtpd[4716]: DA9F4448D74: client=unknown[192.168.1.102], sasl_method=PLAIN, sasl_username=administrator

Notice that it says sasl_method=PLAIN and that is what concerns me. Does the fact that the TLS connection was established ensure that the login is encrypted?

FWIW if I try to add "cram-md5 digest-md5" to the mech_list then I am not able to send a message at all.

---

### Post by MJN on 2007-01-25
That's exactly right - whilst your SASL credentials are in the clear they have been wrapped up inside the encrypted TLS tunnel.

Just make sure you set **smtpd_tls_auth_only = yes** to only allow SMTP AUTH once a TLS session has been established.

Mathew

---

### Post by mlcampbe on 2007-01-25
Matthew,

Thanks for the reply. I indeed had smtpd_tls_auth_only=no and that makes sense now. Previously (with smtpd_tls_auth_only=no) when I telnet to port 25 then I would see the following:

250-PIPELINING
250-SIZE 20000000
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


Now, after setting smtpd_tls_auth_only=yes I see this and that looks a lot better:

250-PIPELINING
250-SIZE 20000000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

One more question though - how do I test this? When I set smtpd_tls_auth_only=yes I was then able to send mail by specifying a user/pass in the email client but it seems to be ignored as there is no entry in the mail.log that shows it was accepted. Is that correct?

---

### Post by MJN on 2007-01-25
I'm not sure I understand your question - can you rephrase it?

Remember that mail destined for your local machine/network will never require username/passord otherwise you'd never receive any mail! Bear this in mind when testing authentication as it's all to easy to send a mail to yourself to minimise the spamming of the others, but it can trip you up if you're not careful as authentication is not then required!

Your logs should look exactly as before when a client has authenticated i.e. a TLS connection established and then SASL AUTH used. If SASL AUTH is appearing then you know they **must** have established a TLS tunnel as they're not able to do otherwise. Bear in mind that Postfix isn't just 'hiding' the fact that SMTP AUTH can be used, but rather explicitly defining what it will accept at that given time. Only when START TLS is issued by the client will it then allow SMTP AUTH to be used.

Does that make sense?

One way of testing that SMTP AUTH can only being used after a TLS connection is to tell your mail client that authentication is required but TLS/encryption is not. You should get a failure when it tries to login without first having first established TLS.

Mathew

P.S. How are your users collecting their mail? Do make sure their POP/IMAP access is encrypted (I've only used IMAP but presumably POP can run over TLS) otherwise their username/password will be sniffable from those connections instead...

---

### Post by mlcampbe on 2007-01-25
Ok, let me reprhase. I am using thunderbird to my PC to send mail to a local ubuntu user and thunderbird is configured to use the postfix smtp server running on ubuntu. The goal here is to try to make sure that email can be sent from my internal network (192.168.1.x) without requiring a password while external users would need a password to connect and send mail through postfix.

My simple test was to configure thunderbird first to require a user/pass to send email AND I selected the TLS option. This worked and I saw the TLS connection and SASL info. I then went back and reconfigured thunderbird to send the user/pass but selected neither TLS nor SSL just to see what happened. To my surprise the mail was accepted when I thought it would be rejected since I sent the user/pass without TLS/SSL enabled. In this 2nd test though I did not see any authentication happening - it appears to just accept the mail the same way as if I had not told thunderbird to send the user/pass.

Therefore my question is how do I test this without putting the server on the internet? Perhaps thunderbird is not sending the user/pass (even though I have that option enabled) when neither TLS or SSL is selected. Is that possible?

---

### Post by MJN on 2007-01-25
It is indeed possible - because you're sending mail to a **local** user! By definition receiving mail for local users mustn't require authentication otherwise you'd never receive any mail. Try sending to a non-local address...

You've likely got **permit_mynetworks** in your **smtpd_recipient_transactions** list hence local clients always pass this test and hence are permitted to send (without having to match the **permit_sasl_authenticated **directive).

In direct response to your question on standalone testing, remove the **permit_mynetworks** and send your mail to an offsite address - don't worry about you not having an Internet connection - Postfix doesn't know this (yet) and hence will accept the mail for delivery... then of course it will struggle to deliver...

Mathew

---

### Post by MrHorus on 2007-01-26
> **mlcampbe said:**
> 
Therefore my question is how do I test this without putting the server on the internet? 

There is a package I use called swaks.

You can install it from the repos and there was a good guide to courier-imap that had info on swaks and how to verify that TLS/SSL was indeed being used.

---

### Post by MJN on 2007-01-26
If you really want proof fire up Ethereal or any other packet sniffer and hunt the passwords down! If TLS is being used you won't see anything...
 
Mathew

---

### Post by mlcampbe on 2007-01-27
Thanks Matthew, that seems to have done the trick. From what I can tell all is working fine now.

---

