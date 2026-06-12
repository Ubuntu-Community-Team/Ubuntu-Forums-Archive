---
title: "ubuntu 16.04 - mail not using /etc/mailname correctly"
date: 2016-09-23
forum: Server Platforms
---

### Post by andrew725 on 2016-09-23
hi all,

I'm not sure if this is a known bug or something is set up incorrectly on my server, but the mail utility is not using the name set in /etc/mailname correctly, which is mysite.com for the sake of this thread.  when I use mail (mail -s "sometext" [email]someemailaddress@somesite.com[/email]), it's sending it as [email]andrew@site.mysite.com[/email] (andrew is the user I'm logged in as, site is my server's hostname, and mysite.com is specified in /etc/mailname).  sparkpost keeps bouncing it because it's not set up as a sending domain, mysite.com is.  I could bypass the issue by setting up site.mysite.com as a sending domain in sparkpost, though I prefer to fix the issue if there's a fix for it.

server info:
ubuntu 16.04 64-bit


thanks!

---

### Post by SeijiSensei on 2016-09-23
Are you also running Postfix, sendmail, or some other SMTP server program?  That's where you can force the domain part of the address.  For instance, in sendmail you can use the MASQUERADE_DOMAIN and MASQUERADE_AS directives in sendmail.mc to create a sendmail.cf that will do the masquerading.  I rarely use Postfix so I can't help with that, but I'm sure it's possible to configure Postfix similarly.

---

### Post by andrew725 on 2016-09-23
> **SeijiSensei said:**
> Are you also running Postfix, sendmail, or some other SMTP server program?  That's where you can force the domain part of the address.  For instance, in sendmail you can use the MASQUERADE_DOMAIN and MASQUERADE_AS directives in sendmail.mc to create a sendmail.cf that will do the masquerading.  I rarely use Postfix so I can't help with that, but I'm sure it's possible to configure Postfix similarly.

Hi,

I only use postfix on the server..I don't bother with IMAP or anything like that.  I have the following config options enabled in postfix, which I believe is the fallback if mail isn't using /etc/mailname.  I can't remember which of these it uses, but I'm pretty sure it's one of them:

myhostname = mysite.com
myorigin = mysite.com

having looked at my config file, I also see this as well:

mydestination = site.mysite.com, localhost.localdomain, localhost

site.mysite.com might be what it's using, but isn't ubuntu supposed to use /etc/mailname first? and if so, why isn't it?

---

### Post by SeijiSensei on 2016-09-23
I don't know of anything that uses /etc/mailname myself. Things like that go back to early Unix days, I believe.  In general, the default for most mailers is to use [email]user@host.domain[/email] rather than just user@domain.

However the answer to your question is in the extensive documentation for Postfix: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin)

"The myorigin parameter specifies the domain that appears in mail that is posted on this machine. The default is to use the local machine name, $myhostname, which defaults to the name of the machine. Unless you are running a really small site, you probably want to change that into $mydomain, which defaults to the parent domain of the machine name."

---

### Post by andrew725 on 2016-09-23
> **SeijiSensei said:**
> I don't know of anything that uses /etc/mailname myself. Things like that go back to early Unix days, I believe.  In general, the default for most mailers is to use [EMAIL="user@host.domain"]user@host.domain[/EMAIL] rather than just user@domain.

However the answer to your question is in the extensive documentation for Postfix: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin)

"The myorigin parameter specifies the domain that appears in mail that is posted on this machine. The default is to use the local machine name, $myhostname, which defaults to the name of the machine. Unless you are running a really small site, you probably want to change that into $mydomain, which defaults to the parent domain of the machine name."

thanks for the info, I'll read up on it.

---

