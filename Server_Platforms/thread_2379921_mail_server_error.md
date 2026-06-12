---
title: "mail server error"
date: 2017-12-11
forum: Server Platforms
---

### Post by micahpage on 2017-12-11
I am trying to send mail thourhg a forum MyBB but i only get an error there saying it could not use the PHP mail function.

When i send mail on the server via
```
echo "This is the body of the email" | mail -s "arggggg" PERSONAL_EMAIL_REMOVED


```
it does send email. It is in the spam folder but that is for another day i guess. Im just wondering if any of these warning might be the reason why MyBB forum service is not able to use PHP mail properly? 


This is the mail log file after i send the mail
```
[COLOR=#333333][FONT=Monaco]c 11 09:07:22 python-forum postfix/pickup[6360]: D5D1B1408E1: uid=1000 from=<[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]metulburr@python-forum[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]>[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Dec 11 09:07:22 python-forum postfix/cleanup[6485]: warning: connect to Milter service inet:localhost:8891: Connection refused[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Dec 11 09:07:22 python-forum postfix/cleanup[6485]: D5D1B1408E1: message-id=<[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]20171211140722.D5D1B1408E1@python-forum.io[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]>[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Dec 11 09:07:22 python-forum postfix/qmgr[6361]: D5D1B1408E1: from=<[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]metulburr@python-forum[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]>, size=412, nrcpt=1 (queue active)[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Dec 11 09:07:23 python-forum postfix/smtp[6487]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c00::1a]:25: Network is unreachable[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Dec 11 09:07:23 python-forum postfix/smtp[6487]: D5D1B1408E1: to=<PERSONAL_EMAIL_ERMOVED>, relay=gmail-smtp-in.l.google.com[74.125.124.26]:25, delay=0.74, delays=0.03/0.03/0.4/0.27, dsn=2.0.0, status=sent (250 2.0.0 OK 1513001243 p203si6094540itg.131 - gsmtp)[/FONT][/COLOR]
[COLOR=#333333][FONT=Monaco]Dec 11 09:07:23 python-forum postfix/qmgr[6361]: D5D1B1408E1: removed[/FONT][/COLOR]
```

and there is nothing in the mail.err file

---

### Post by SeijiSensei on 2017-12-11
Are you on a residential connection?  If so, your ISP may be blocking connections to remote SMTP servers.  Try running the command "telnet gmail-smtp-in.l.google.com 25" and see if you get a reply from Google's server.  It would look like this:

```
220 mx.google.com ESMTP n190si5562519qkb.84 - gsmtp
```

If you don't see that banner, or the connection just hangs, then you're being blocked.

---

### Post by micahpage on 2017-12-11
I am not trying to remote connect to SMTP Google. I am trying to make my own mail server on my server with postfix. But if i do try that i get

> Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP c11si11217902qkh.374 - gsmtp



No its not a home connection, its a droplet VPS located in NYC by Digital Ocean.

---

### Post by SeijiSensei on 2017-12-16
Well, I'm not much of a Postfix expert, but let's start with this:
```
warning: connect to Milter service inet:localhost:8891: Connection refused
```

Are you running a milter that listens on port 8891?  

```
connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c00::1a]:25: Network is unreachable
```

Postfix is trying to connect to GMail's IPv6 address and failing.  You can limit Postfix to using IPv4 with the [inet_protocols]("http://www.postfix.org/postconf.5.html#inet_protocols") directive:

```
inet_protocols = ipv4
```

in /etc/postfix/main.cf.

This error is benign, since Google confirms delivery on its IPv4 address.

I don't know what the milter is supposed to be.  I've also not used MyBB so I don't know if the milter is associated with that or not.

---

### Post by micahpage on 2017-12-20
im not sure what google is even in there for. I am not trying to relay anything to/from them but create a mail server. IT sends out mail through php but wont receive mail.

The milter was me trying to get out of the spam when i send emails so other services know the mailer is not  a spammer. I havent fully figured that out, but i am able to send mail...its just in the spam folder when people receive it. Milter is suppose to fix that.

---

### Post by cariboo on 2017-12-21
Moved to server platforms.

---

### Post by lisati on 2017-12-21
If I've interpreted the log entries correctly, your server actually delivered something to Google's server:
```

Dec 11 09:07:23 python-forum postfix/smtp[6487]: D5D1B1408E1: to=<PERSONAL_EMAIL_ERMOVED>, relay=gmail-smtp-in.l.google.com[74.125.124.26]:25, delay=0.74, delays=0.03/0.03/0.4/0.27, dsn=2.0.0, status=sent (250 2.0.0 OK 1513001243 p203si6094540itg.131 - gsmtp)

```

It has been a while since I've run a Postfix server at home, but I never used ipV6 or tinkered with [milter services]("http://www.postfix.org/MILTER_README.html").

---

### Post by SeijiSensei on 2017-12-22
> **micahpage said:**
> im not sure what google is even in there for. I am not trying to relay anything to/from them but create a mail server. IT sends out mail through php but wont receive mail.

You sent a message to GMail.  I'm sure you realize that's a Google service.

> The milter was me trying to get out of the spam when i send emails so other services know the mailer is not  a spammer. I havent fully figured that out, but i am able to send mail...its just in the spam folder when people receive it. Milter is suppose to fix that.

There are lots of reasons that a server can be marked as a spam source that cannot be fixed with a milter.  Is this milter designed to implement DMARC?  Do you have an SPF record for your domain that designates this server as the legitimate sender for the domain?  That can help a lot.  Also make sure the server has both forward and reverse DNS configured, and that the name matches both ways.

Now as for why you cannot receive mail, what do you have for mynetworks and mydestination in /etc/postfix/mail.cf?  If you haven't changed [mynetworks]("http://www.postfix.org/postconf.5.html#mynetworks") from its Ubuntu default, then the server will only accept mail from localhost.  To accept mail from anywhere use

```
mynetworks = 0.0.0.0/0
```

After you get things running, read [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html), then read it again.

Running a mail server is not for the faint of heart.  It requires a lot of configuration and monitoring.  Once you have the server up and running, run the diagnostic checks at [https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx).  You can also run specific checks from [https://mxtoolbox.com/supertool.aspx](https://mxtoolbox.com/supertool.aspx).

If your primary concern is sending outbound mail from your forum software, then I'd avoid receiving mail on this server entirely.  Just address the outbound messages as From a public email address you already maintain like the one at GMail.  Leave the mynetworks setting at its default value so only localhost is permitted to connect.

---

