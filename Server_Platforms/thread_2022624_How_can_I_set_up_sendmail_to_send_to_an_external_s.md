---
title: "How can I set up sendmail to send to an external server using TLS?"
date: 2012-07-11
forum: Server Platforms
---

### Post by Azdour on 2012-07-11
Hi all,

I recently installed Webmin on our Xubuntu 12.04 server so that we can manage various things like the firewall etc via its web UI.

We have sendmail on the server and that is working ok when sending emails to users on the system.

I know this is not an Xubuntu specific question but I'm trying to set up Webmin and Sendmail so that when an email goes to root@servername it gets forwarded (relayed?) to our hosted email server that is external so that I can get those emails.

I've looked at the various guides for setting up sendmail and Gmail. We are not using Gmail but it gives me clues as to what may be required.

My first step is just to try and get sendmail to send external emails out to our hosted email server.

I've added the following to sendmail.mc:

```

dnl # Setting up sendmail to sent to our SMTP server
define(`SMART_HOST',`[host.email.server]')dnl
define(`RELAY_MAILER_ARGS', `TCP $h 465')dnl
define(`ESMTP_MAILER_ARGS', `TCP $h 465')dnl
define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CARM-MD5 LOGIN PLAIN')dnl
FEATURE(`authinfo',`hash /etc/mail/auth/client-info.db')dnl

```

Then used m4 to create the sendmail.cf

In client-info I gave it the login details for our host email server:

```

AuthInfo:host.email.server “U:smsp” “I:username” “P:password” “M:PLAIN”
AuthInfo:host.email.server:465 “U:smsp” “I:username” “P:password” “M:PLAIN”

```	

I then used makemap to create the client-info.db

When sending an email with an external address I get the following in the Mail Queue Status column for the email:

Deferred: Connection reset by host.email.server

On the hosted email server I see the following in the exim_mainlog:

2012-07-11 13:12:25 TLS error on connection from [my server ip] (SSL_accept): timed out

What do I need to add to authenticate with the external email server using TLS?

---

### Post by Azdour on 2012-07-12
bump

---

### Post by Azdour on 2012-07-18
Hi,

Ok, not a 100% perfect solution but it works. In the end I edited the sendmail submit.mc according to:

[http://www.harker.com/sendmail/submit.html](http://www.harker.com/sendmail/submit.html)

So all emails go directly out to our external server.

---

