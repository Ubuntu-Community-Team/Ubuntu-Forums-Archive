---
title: "Help with hosting my own email, &quot;from scratch&quot;?"
date: 2013-07-01
forum: The Cafe
---

### Post by booksmart00 on 2013-07-01
Hello! I was wondering if someone could telll me or point me to a guide to hosting email at my domain. I have found many posts about how to do it with Google Apps, but that's not what I want. I would like to have it set up to where I completely control it and do not have to buy email services from anyone. What kinds of things would I need to know, and how would I set it up.

---

### Post by newbie-user on 2013-07-02
You will need:
1. mail delivery agent (MDA)
2. mail transfer agent (MTA)
3. mail user agent (MUA)

Dovecot is a popular program that includes MDA functionality
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

Postfix is a popular MTA
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

MUAs can be a web-based login, or a program such as Evolution, Thunderbird, Outlook. For a web-based login, you could look at squirrelmail or roundcube
[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)
[https://help.ubuntu.com/community/Roundcube](https://help.ubuntu.com/community/Roundcube)

---

### Post by SeijiSensei on 2013-07-02
Other important things you would need:

A service with a publicly-visible Internet address that can accept incoming traffic on port 25 and send out such traffic as well.  Usually a server on a residential connection will not be able to exchange mail reliably because of restrictions imposed by ISPs.  I use a [Linode]("http://www.linode.com") VM as my mail server.

You'll also need to create an MX record for your domain  that points to your server.  While it's still considered good practice to have a backup MX server, it's less common these days.

Then you have the issue of spam and virus filtering.  For this I use [MailScanner]("http://www.mailscanner.info/").  In fact my preferred mail server configuration runs CentOS 6.x and the complete suite of scanners at MailScanner.  Justin offers a prepackaged version on the site that installs all three of MailScanner, spamassassin and ClamAV automatically.  Since it's designed to run on RedHat-flavored machines, I use CentOS as the operating system, not Ubuntu.  I continue to use sendmail as my MTA, but Postfix is supported as well.

Next, how many mailboxes will there be?  If we're a talking a couple dozen accounts at most, it's easiest to create each account as a Linux user and let the mail be delivered to /var/spool/mail/username.  Elaborate methods that use Maildir formats and MySQL account databases are overkill for a simple mail server.

---

### Post by Bucky Ball on 2013-07-02
***Thread reopened.***

---

### Post by CharlesA on 2013-07-02
> **SeijiSensei said:**
> 
A service with a publicly-visible Internet address that can accept incoming traffic on port 25 and send out such traffic as well.  Usually a server on a residential connection will not be able to exchange mail reliably because of restrictions imposed by ISPs.  I use a [Linode]("http://www.linode.com") VM as my mail server.

I do the same except at another VPS provider. I don't have port 25 open, though as I use port 587 for SMTP, is that a problem ? postfix is listening on both, but I believe I firewalled port 25.

@OP: Read this:
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

---

### Post by SeijiSensei on 2013-07-03
How do you accept incoming mail?  My understanding is that 587 is the "[mail submission]("http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol#Mail_processing_model")" port, designed for client software to submit outbound mail to a server using the SMTP protocol. But communication between mail servers occurs over the traditional SMTP port, 25.

---

### Post by CharlesA on 2013-07-03
> **SeijiSensei said:**
> How do you accept incoming mail?  My understanding is that 587 is the "[mail submission]("http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol#Mail_processing_model")" port, designed for client software to submit outbound mail to a server using the SMTP protocol. But communication between mail servers occurs over the traditional SMTP port, 25.

I'm not sure. I've tested it with Gmail and it worked fine via port 587, but I think that is how gmail has their stuff configured.

I just opened port 25 up again and Outlook.com works and so does Yahoo.

Methinks I'll be leaving it open. Thanks!

---

### Post by SeijiSensei on 2013-07-03
You're not talking about using the clients at a place like Yahoo to manage a mailbox on your server, right?  You are talking about sending a message from Yahoo with an @yahoo.com From address to an address in a domain for which your server is the MX, yes?

With sendmail, you get log messages that look like this:
```

Jul  3 13:17:24 xxxxx sendmail[29689]: r63HHLk7029689: from=<someone@yahoo.com>, size=267838, class=0, nrcpts=1, msgid=1372871757.78624.YahooMailNeo@web142602.mail.bf1.yahoo.com>, proto=ESMTP, daemon=MTA, relay=[10.1.1.12]

``` 
The message originated on web142602...yahoo.com and arrived on a server I manage using ESMTP over port 25.

Any server advertised as the MX for a domain needs to accept mail on port 25.

---

### Post by SeijiSensei on 2013-07-03
You're not talking about using the clients at a place like Yahoo to manage a mailbox on your server, right?  You are talking about sending a message from Yahoo with an @yahoo.com address to an address in a domain for which your server is the MX, yes?

With sendmail, you get log messages that look like this:
```

Jul  3 13:17:24 xxxxx sendmail[29689]: r63HHLk7029689: from=<someone@yahoo.com>, size=267838, class=0, nrcpts=1, msgid=1372871757.78624.YahooMailNeo@web142602.mail.bf1.yahoo.com>, proto=ESMTP, daemon=MTA, relay=[10.1.1.12]

``` 
The message originated on web142602...yahoo.com and arrived on a server I manage using ESMTP over port 25.

Any server advertised as the MX for a domain needs to accept mail on port 25. That's one of the things that makes it so hard to manage a mail server.  Grandmas in Palm Beach have compromised computers that pump out spam every day.  Sure the disk drive is flashing like crazy, but that's not something they'd notice.  If the machine is connected at night, the bot can schedule itself to run then so no one notices.

---

### Post by CharlesA on 2013-07-03
> **SeijiSensei said:**
> You're not talking about using the clients at a place like Yahoo to manage a mailbox on your server, right?  You are talking about sending a message from Yahoo with an @yahoo.com address to an address in a domain for which your server is the MX, yes?

Nah, I logged into a yahoo account and sent a test email. So far it seems to work. That must explain my lack of spam too. :lol:

> With sendmail, you get log messages that look like this:
```

Jul  3 13:17:24 xxxxx sendmail[29689]: r63HHLk7029689: from=<someone@yahoo.com>, size=267838, class=0, nrcpts=1, msgid=1372871757.78624.YahooMailNeo@web142602.mail.bf1.yahoo.com>, proto=ESMTP, daemon=MTA, relay=[10.1.1.12]

``` 
The message originated on web142602...yahoo.com and arrived on a server I manage using ESMTP over port 25.

The logs I'm seeing look different, but similar:
```
Anonymous TLS connection established from co9ehsobe002.messaging.microsoft.com[207.46.163.25]: TLSv1 with cipher AES128-SHA 
```

I'm running postfix, though. :)
.
EDIT: Rejection entry looks like this:

```
postfix/smtpd[10226]: NOQUEUE: reject: RCPT from p12.sdc.mail.turner.com[157.166.252.165]: 550 5.1.1 <user@somerandomdomain.COM>: Recipient address rejected: User unknown; from=<owner-ADULTSWIM-COMEDY*user**somerandomdomain*-COM@EMA3LSV04.TURNER.COM> to=<jpond@somerandomain.com> proto=ESMTP helo=<p12.sdc.mail.turner.com>

```
> Any server advertised as the MX for a domain needs to accept mail on port 25. That's one of the things that makes it so hard to manage a mail server.  Grandmas in Palm Beach have compromised computers that pump out spam every day.  Sure the disk drive is flashing like crazy, but that's not something they'd notice.  If the machine is connected at night, the bot can schedule itself to run then so no one notices.

That's good to know, thanks.

---

