---
title: "Mail not being delivered externally"
date: 2010-03-01
forum: Server Platforms
---

### Post by gertjuhh on 2010-03-01
Hi,

We've just setup an Ubuntu server as our main web server.
The site's domain, say mydomain.com, has its DNS hosted elsewhere. 
A records are pointed to the IP address of the new server, so far so good.
Email is however handled elsewhere.
Sending mail to _anything but_ mydomain.com works fine.
However when i try to send mail to [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL] the mail ends in /var/mail/me

Any idea's on how to deliver the mail externally?

Using Ubuntu 9.10 with sendmail

Thanks in advance!

---

### Post by gertjuhh on 2010-03-03
*bump*
Any help would be appreciated!

---

### Post by gertjuhh on 2010-03-08
Still haven't been able to solve this problem.
Will gladly switch to another mail server if that will solve the problem.
All we need it for is sending out mail.

---

### Post by Bachstelze on 2010-03-08
Your server probably thinks it is the final destination for mail sent to example.com, you need to remove that in your config. Post the output of the command

```
hostname
```

as well as the contents of /etc/mail/local-host-names.

---

### Post by gertjuhh on 2010-03-08
Hostname in the case would be the domain without the extension.
/etc/mail/local-host-names only contains localhost, i already checked this.
/etc/hosts also only contains localhost

---

### Post by Bachstelze on 2010-03-08
> **gertjuhh said:**
> Hostname in the case would be the domain with the extension.
Being 'rgbsystems'

So you mean the [font=monospace]hostname[/font] command returns [font=monospace]rgbsystems.nl[/font]? If it does, that's your problem. You must give your machine a hostname in that domain ([font=monospace]something.rgbsystems.nl[/font]).

---

### Post by koenn on 2010-03-08
I agree with Bachstelze about your mail server thinking it's final destination for *mydomain.com*

I don't know how to configure sendmail to fix this.
Debian uses exim4, which would probably work with Ubuntu as well.
If you decide to use this, you can run
```
dpkg-reconfigure exim4-config
``` to set it up and (re-)configure it. Your best bet would be "no local delivery" and/or "domains this system should accept mail for:"(leave blank, or put only the server's FQDN)



edit:
didn't see Bachstelze post. 
you probably better try his suggestions first.

---

### Post by gertjuhh on 2010-03-08
> **Bachstelze said:**
> So you mean the [FONT=monospace]hostname[/FONT] command returns [FONT=monospace]rgbsystems.nl[/FONT]? If it does, that's your problem. You must give your machine a hostname in that domain ([FONT=monospace]something.rgbsystems.nl[/FONT]).
Sorry i made a typo there...
The exact output of the hostname command is 'rgbsystems' being the domain name _without_ the extension.

That being said, do i still need to change the server's hostname to something.rgbsystems.nl ?

Thanks for the help thus far, much appreciated!

---

### Post by noway2 on 2010-03-08
I am afraid that I can't offer more help, but take a look at the following: [http://www.sendmail.org/sm-X/release.html#SMXREADME](http://www.sendmail.org/sm-X/release.html#SMXREADME)

Sendmail X is the local delivery agent.  About page 40 there is a section on using sendmail for sending mail only. 

I think your problem comes down to the fact that it thinks it is supposed to be the recipient for your domain and then it tries to use the local delivery agent.  Instead you don't want it to use local delivery and instead to forward or relay to another SMTP.

---

### Post by gertjuhh on 2010-03-09
'Solved' my problem for now.
Using PHPMailer with an SMTP config to our mail server.
Will look into setting a mail server when i get some more spare time.
Thanks for the help

---

