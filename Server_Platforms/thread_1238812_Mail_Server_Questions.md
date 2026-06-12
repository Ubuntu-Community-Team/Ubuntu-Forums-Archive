---
title: "Mail Server Questions"
date: 2009-08-12
forum: Server Platforms
---

### Post by Znupi on 2009-08-12
Ok, I just managed to successfully receive e-mail on my own server. I must admit, it took me a while to figure stuff out, but I still have some questions. I followed the instructions in the Ubuntu Server Guide and installed Postfix and Dovecot. Now, I'm not really sure what each one of these does, so I'm going to write what I think they do and let you people correct me:
**Postfix** receives e-mail from the outside world and saves it to the HDD. Also, it can send mail, because it has a sendmail-like component.
**Dovecot** reads the e-mail saved by Postfix and serves it to clients (i.e. Thunderbird etc.) via POP3. Also, it allows clients to connect through SMTP and send e-mail from the server. (I haven't tried this yet, I installed roundcube webmail and used that. I guess I wouldn't know how to configure a client for that -- wouldn't know all the ports, certificates and secure connections to use)

Another question: how are accounts handled? I.e. can I have more e-mail accounts than the ones defined in the actual system? If I only have an account on the server with the username "felix", can I only receive e-mail on felix@my-domain, or can I somehow define other accounts, and where?

One last thing: I'm a bit confused about protocols. A client (Thunderbird-like) connects to the server via POP3 to fetch e-mail and via SMTP to send mail. If that's right, then what's the protocol that postfix uses to receive mail from the outside world?

---

### Post by Znupi on 2009-08-13
Bump?

---

### Post by HermanAB on 2009-08-13
Howdy,

In a simple Postfix setup, the users are system users, so you need to make an account for each one.

If you want the users to be managed with a database, then you need a MySQL setup with Postfix, but the email is still saved per user, which can take up a lot of space.  For example, if you send a message CC to each user, it will save a copy of the same message for each one.  So if HR sends a 10MB Word document as an attachment to each user in a 25000 person company, then you have to run out and buy more disk drives.

A more efficient system is one that is completely database backed, with the user data and email all inside the database.  In this case, a message sent to multiple users will result in only one saved copy.  Examples of this kind of system is Zimbra and Citadel.  Citadel especially, extremely easy to install - it takes all of about 20 minutes to run the Easy Install script.  It can handle 256 terabytes of data with its BerkeleyDB back end.

So once you are done playing with Postfix, give Citadel a try - you won't look back.

---

### Post by Bachstelze on 2009-08-13
> **Znupi said:**
> Ok, I just managed to successfully receive e-mail on my own server. I must admit, it took me a while to figure stuff out, but I still have some questions. I followed the instructions in the Ubuntu Server Guide and installed Postfix and Dovecot. Now, I'm not really sure what each one of these does, so I'm going to write what I think they do and let you people correct me:
**Postfix** receives e-mail from the outside world and saves it to the HDD. Also, it can send mail, because it has a sendmail-like component.
**Dovecot** reads the e-mail saved by Postfix and serves it to clients (i.e. Thunderbird etc.) via POP3. Also, it allows clients to connect through SMTP and send e-mail from the server. (I haven't tried this yet, I installed roundcube webmail and used that. I guess I wouldn't know how to configure a client for that -- wouldn't know all the ports, certificates and secure connections to use)

Correct.

> **Znupi said:**
> Another question: how are accounts handled? I.e. can I have more e-mail accounts than the ones defined in the actual system? If I only have an account on the server with the username "felix", can I only receive e-mail on felix@my-domain, or can I somehow define other accounts, and where?

In addition to what HermanAB said about database-driven backends, you can also define aliases and virtual users, which will for example forward mail sent to alice@my-domain to another address (Alice's GMail address, for example) without the need to create an alice account.

> **Znupi said:**
> One last thing: I'm a bit confused about protocols. A client (Thunderbird-like) connects to the server via POP3 to fetch e-mail and via SMTP to send mail. If that's right, then what's the protocol that postfix uses to receive mail from the outside world?

SMTP.

---

### Post by Znupi on 2009-08-13
Thank you both for your great answers!

> **HymnToLife said:**
> SMTP.
I was afraid of that -- that brings me to another confusion. Postfix is a Mail Transfer Agent, correct? If yes, then what stops people from using it to send e-mails? I.e. pretending to be another MTA and relaying mail to through my server to another?

---

### Post by noway2 on 2009-08-13
It is all in the configuration (main.cf)

For example, smtpd_sasl_security_options = noanonymous will prohibit anonymous relaying.  I use SASL authentication, with an exception for my local LAN, so in order to transmit anything you need to be an authenticated user.

---

### Post by HermanAB on 2009-08-13
BTW, Dovecot is ONLY used to deliver mail to mail clients like Thunderbird and Outlook.  Dovecot is not involved in sending mail at all.  Postfix does all the receiving and sending.

---

