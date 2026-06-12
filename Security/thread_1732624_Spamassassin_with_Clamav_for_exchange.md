---
title: "Spamassassin with Clamav for exchange"
date: 2011-04-18
forum: Security
---

### Post by CNM on 2011-04-18
Hi ,

i just implemented a microsoft environment (AD and Exchange ... etc ) windows server 2008 
R2 with Exchange 2010 and MS SQL 2008 R2
i am planning to implement a Linux box to filter emails coming to exchange ... antispam and antivirus
the first idea that popped into my mind was spamassassin and clamav ...
anyone did that before ?
i need some pointers 
and is there a better solution ?

Thanks :)

---

### Post by SeijiSensei on 2011-04-18
[http://www.mailscanner.info/](http://www.mailscanner.info/).  It will run both a virus scan and run SpamAssassin against each message.  It also has a wide array of useful configuration options.

---

### Post by CNM on 2011-04-19
> **SeijiSensei said:**
> [http://www.mailscanner.info/](http://www.mailscanner.info/).  It will run both a virus scan and run SpamAssassin against each message.  It also has a wide array of useful configuration options.

hey ,

thanks for your reply :)
i encountered mailscanner during my research
did you work with it before ?
do you happen to have some sort of step by step guide ?
actually i'm still not sure how to make the thing work ... i was thinking that in the MS DNS i would point an MX record to the linux box IP
and in the DNS of the linux box , i would set an MX record to the MS Exchange server ...
i'm really not sure if it's the correct way to go ... :/

---

### Post by SeijiSensei on 2011-04-19
> **CNM said:**
> i encountered mailscanner during my research
did you work with it before ?

I've used it for at least half-a-dozen years now to scan my clients' mail.  However I use [CentOS]("http://www.centos.org/") on servers, which makes installation of mailscanner really simple.  You just download the [tar.gz file]("http://www.mailscanner.info/files/4/rpm/MailScanner-4.83.5-1.rpm.tar.gz"), unpack it, and run install.sh.  You can install mailscanner on Ubuntu/Debian from the repositories with apt-get.

> actually i'm still not sure how to make the thing work

Well, the specific configuration will depends on what MTA you use (sendmail, Postfix, exim, etc.).  However the general strategy is to have the external MX record point to the MailScanner box with its MTA configured to forward mail for the domain to the Exchange server.  I use sendmail for the MTA with a [mailertable]("http://www.sendmail.org/m4/mailertables.html") that looks like this:

```

example.com        relay:exchange.example.com

```

That tells sendmail to ignore any MX records and deliver mail for example.com to exchange.example.com.  Outbound messages for other domains will be delivered normally.

On the Exchange server you need only configure a "smart host" that points to the Linux box.  Exchange will then forward all the mail to the Linux box for scanning before it gets forwarded out to the Internet.

---

### Post by CNM on 2011-04-19
> **SeijiSensei said:**
> I've used it for at least half-a-dozen years now to scan my clients' mail.  However I use [CentOS]("http://www.centos.org/") on servers, which makes installation of mailscanner really simple.  You just download the [tar.gz file]("http://www.mailscanner.info/files/4/rpm/MailScanner-4.83.5-1.rpm.tar.gz"), unpack it, and run install.sh.  You can install mailscanner on Ubuntu/Debian from the repositories with apt-get.



Well, the specific configuration will depends on what MTA you use (sendmail, Postfix, exim, etc.).  However the general strategy is to have the external MX record point to the MailScanner box with its MTA configured to forward mail for the domain to the Exchange server.  I use sendmail for the MTA with a [mailertable]("http://www.sendmail.org/m4/mailertables.html") that looks like this:

```

example.com        relay:exchange.example.com

```That tells sendmail to ignore any MX records and deliver mail for example.com to exchange.example.com.  Outbound messages for other domains will be delivered normally.

On the Exchange server you need only configure a "smart host" that points to the Linux box.  Exchange will then forward all the mail to the Linux box for scanning before it gets forwarded out to the Internet.

This should do the trick for the installation on ubuntu am i right ? : [http://www.mailscanner.info/ubuntu.html](http://www.mailscanner.info/ubuntu.html)

concerning the MX records i am not really sure how to send an email for the internet since i am deploying this solution in a lab environment so i'm not using public IPs ...
i'm using all private IPs ... any idea about that ??

Also , do you think it's important to scan emails transiting between people from the same domain ?
lets say X and Y are different people in the same domain ... is it a good practice to scan emails sent from X to Y or from Y to X ?

another thing , can you elaborate please why you are using mailertable ? is it just to forward the emails from example.com to server.example.com ?
can't this be done from the DNS ? ... i'm not really sure about that ...

one last thing , the smart host is only to make sure we are sending virus free emails ... right ?

Thanks a lot :)
i really appreciate your help :)

---

### Post by SeijiSensei on 2011-04-19
> **CNM said:**
> This should do the trick for the installation on ubuntu am i right ? : [http://www.mailscanner.info/ubuntu.html](http://www.mailscanner.info/ubuntu.html)

I'd imagine so.  Julian is a pretty careful guy, so I'd guess any posted documentation should work.

> concerning the MX records i am not really sure how to send an email for the internet since i am deploying this solution in a lab environment so i'm not using public IPs ...
i'm using all private IPs ... any idea about that ??

The type of IP doesn't matter.  I just don't understand what you're trying to do.  Suppose there were no Linux box scanning at all.  How would you set up the Exchange server to send mail to and from the Internet?  It sounds like you're only interested in sending outbound messages and not accepting inbound ones?  Why?

> Also , do you think it's important to scan emails transiting between people from the same domain ?

Yes, unless you can guarantee that none of the people using the server will ever become infected with a virus or trojan that replicates via email.  At my clients' sites, we scan every message, both inbound and outbound.

> another thing , can you elaborate please why you are using mailertable ? is it just to forward the emails from example.com to server.example.com ? can't this be done from the DNS ?

Yes, if you have an internal DNS server with an MX record that points to the Exchange server as the MX host for the domain.  I'm often in situations where there's both a public external DNS server for the domain and a private internal server with different records entirely.  If the Linux scanner is the external MX host, then you have to make sure that its resolv.conf uses the internal DNS server to handle deliveries.  I often just avoid worrying about these sorts of problems by using a mailertable.

> one last thing , the smart host is only to make sure we are sending virus free emails ... right ?

A "smart host" identifies the machine which handles delivery for an SMTP server.  In your case you don't want the Exchange server delivering mail to the Internet directly since you want to scan the outbound mail before it's released.  So you tell Exchange to forward all its outbound messages to the Linux scanner and let that box handle final delivery.

Note that in these kinds of settings, you definitely do not want to put the domain into /etc/mail/local-host-names.  That would tell the Linux box that it provides final delivery to local mailboxes which isn't what you want.  local-host-names should only include "localhost" and perhaps the fully-qualified name of the Linux box itself so that messages sent to [email]root@mailscanner.example.com[/email] get delivered locally, while mail for example.com gets sent to the Exchange server.

---

### Post by CNM on 2011-04-20
> **SeijiSensei said:**
> I'd imagine so.  Julian is a pretty careful guy, so I'd guess any posted documentation should work.



The type of IP doesn't matter.  I just don't understand what you're trying to do.  Suppose there were no Linux box scanning at all.  How would you set up the Exchange server to send mail to and from the Internet?  It sounds like you're only interested in sending outbound messages and not accepting inbound ones?  Why?



Yes, unless you can guarantee that none of the people using the server will ever become infected with a virus or trojan that replicates via email.  At my clients' sites, we scan every message, both inbound and outbound.



Yes, if you have an internal DNS server with an MX record that points to the Exchange server as the MX host for the domain.  I'm often in situations where there's both a public external DNS server for the domain and a private internal server with different records entirely.  If the Linux scanner is the external MX host, then you have to make sure that its resolv.conf uses the internal DNS server to handle deliveries.  I often just avoid worrying about these sorts of problems by using a mailertable.



A "smart host" identifies the machine which handles delivery for an SMTP server.  In your case you don't want the Exchange server delivering mail to the Internet directly since you want to scan the outbound mail before it's released.  So you tell Exchange to forward all its outbound messages to the Linux scanner and let that box handle final delivery.

Note that in these kinds of settings, you definitely do not want to put the domain into /etc/mail/local-host-names.  That would tell the Linux box that it provides final delivery to local mailboxes which isn't what you want.  local-host-names should only include "localhost" and perhaps the fully-qualified name of the Linux box itself so that messages sent to [EMAIL="root@mailscanner.example.com"]root@mailscanner.example.com[/EMAIL] get delivered locally, while mail for example.com gets sent to the Exchange server.

ok thanks for the tip

concerning the IP issue , i want to scan all emails ... coming from the internet and outgoing from our users whether to the exterior or within the same domain
i'm just not sure how to do that without having a public IP in the testing environment ... how am i supposed to simulate mails coming from the internet ? ...

concerning mailertable , it seems like the easy way out right ?
it might make me gain some time i guess ... never tried it before though ...

is it possible to elaborate more about the "smart host" ? i never encountered it before actually ... it seems pretty interesting ... :)

---

