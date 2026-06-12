---
title: "Postfix question"
date: 2013-09-18
forum: Server Platforms
---

### Post by adamjseed on 2013-09-18
Hi all,

I have done quite a bit of research on this but struggling to resolve my issue.

I have a network at home with a server (server1.mydomain.com) which can hook upto a mail server to send alerts out and an email server (server-mail.mydomain.com). I started to try and build an email server using postfix to send an email to my gmail account (adam@gmail.com) from server1

I installed postfix and added a few config changes: 
```
mydestination = server-mail.mydomain.com, localhost.mydomain.com, localhost, mydomain.com, gmail.com
mynetworks = 127.0.0.0/8, 192.168.1.0/24
```

I then just tried to send an email: 
```
telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 server-mail.mydomain.com ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu2; Wed, 18 Sep 2013 18:59:16 +0400; (No UCE/UBE) logging access from: server-mail.mydomain.com(OK)-server-mail.mydomain.com [127.0.0.1]
ehlo server1.mydomain.com
250-server-mail.mydomain.com Hello server-mail.mydomain.com [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-DELIVERBY
250 HELP
mail from: server1@mydomain.com
250 2.1.0 server1@mydomain.com... Sender ok
rcpt to: adam@gmail.com
553 5.1.8 adam@gmail.com... Domain of sender address server1@mydomain.com does not exist
```


I'm trying to emulate my server1 sending a mail (I think) by using ehlo server1.mydomain.com

I dont know if I'm way off here but any help would be appreciated

---

### Post by adamjseed on 2013-09-18
So a bit of development, I noticed the telnet resulted in 'ESMTP Sendmail' being shown. it looked like a install of sendmail was overriding postfix. I removed and restarted it now im getting the correct connection

```
telnet server-mail.mydomain.com 25
Trying 192.167.1.x...
Connected to server-mail.mydomain.com.
Escape character is '^]'.
220 server-mail.mydomain.com ESMTP Postfix (Ubuntu)
MAIL FROM: server1@mydomain.com
250 2.1.0 Ok
RCPT TO: adam@gmail.com
550 5.1.1 <adam@gmail.com>: Recipient address rejected: User unknown in local recipient table
```

... but a different error.

---

### Post by TheFu on 2013-09-18
Sending email requires DNS-MX records and that your ISP doesn't block outbound SMTP traffic. Most residential ISPs block inbound and outbound SMTP traffic. That is why the ISP has email gateways.

Output from **postconf -n ** would be helpful after you confirm that you can telnet to gmail.com port 25, and have an MX DNS record.

---

### Post by CharlesA on 2013-09-18
> **TheFu said:**
> Sending email requires DNS-MX records and that your ISP doesn't block outbound SMTP traffic. Most residential ISPs block inbound and outbound SMTP traffic. That is why the ISP has email gateways.

Output from **postconf -n ** would be helpful after you confirm that you can telnet to gmail.com port 25, and have an MX DNS record.

You should be able to send email via gmail by using port 587 instead of port 25. That's how I have my home server set up.

---

### Post by adamjseed on 2013-09-19
Hi Charles, thanks for the reply

I think your right, I'm with Virgin UK and telnet gmail.com 25 does not work. 

Do you have any suggestions on how I can me create a mail server that can send emails to gmail? it needs to work with standard software which can hook up to a mail server.

---

### Post by klausmedk on 2013-09-19
Hi Adam

do you know that the "mydestination" configuration parameter lists all the domains that your server can deliver mails locally for.
When you put gmail.com there it means that whenever a mail for [email]xxx@gmail.com[/email] is sent through your server it will try to deliver that mail locally instead of passing it on to another (gmails mail sever) to have it deliver the mail.

I'm not sure but I do not think that is what you want.

Regards
Klaus

---

### Post by TheFu on 2013-09-19
Do you only want to send email to 1 email address or do you want to be able to send emails to anyone using your gmail address as the only sender?  
The 2nd is what CharlesA has setup, if I'm reading his text correctly. Using that technique, you should be able to use any email address that lets you use a "thick client" to send emails ... including the email address that your ISP provides.

If you don't have any need to receive emails, ever, then you are covered.  You can use something like **fetchmail** to poll your email accounts (IMAP/POP3) and pull any email back to your server, so that it appears you have send and receive capabilities.  That works.  

For just a few local accounts, this can work fine by setting up account translation maps so a local userid sends to a specific external email account using connection parameters.  I'd have to look up exactly how postfix supports this, but I've seen it done.

Hummm ... just got a business idea.

---

### Post by CharlesA on 2013-09-19
> **adamjseed said:**
> Hi Charles, thanks for the reply

I think your right, I'm with Virgin UK and telnet gmail.com 25 does not work. 

Do you have any suggestions on how I can me create a mail server that can send emails to gmail? it needs to work with standard software which can hook up to a mail server.

Check this out. It's for CentOS, but it's basically the same for Ubuntu/Debian.
[http://charlesa.net/tutorials/centos/postfix-as-gmail-relay-centos.php](http://charlesa.net/tutorials/centos/postfix-as-gmail-relay-centos.php)

Note to self, write up one of those for Debian...

---

