---
title: "Email problem"
date: 2010-11-13
forum: Server Platforms
---

### Post by schmutztaucher on 2010-11-13
MTA = Postfix
MDA = Dovecot
WebGUI = squirrelmail

Got these installed and it working but I have 2 problems.

1. When using squirrelmail it sends out emails with the sender address [EMAIL="user@mail.mydomain.com"]user@mail.mydomain.com[/EMAIL]. Is there a way to configure it to send as [EMAIL="user@mydomain.com"]user@mydomain.com[/EMAIL] by default?

2. Sending mail from my users accounts on squirrelmail goes into other clients spam folder i.e. gmail. Im hopeful its because Im sending mail out as mail.domain.com but i will only be able to tell if i fix problem 1.

my main.cf for postfix has```

mydestination = mydomain.com, mail.mydomain.com, localhost.localdomain, localhost

```Thanks for any help you can give.

---

### Post by SeijiSensei on 2010-11-13
In Squirrelmail, go to Options > Personal Information and fill in the name and email address fields.  Squirrel will use those to address messages.  Otherwise the default for any unqualified username like "bill" is "bill@host.example.com".

I suspect there's a way to tell Postfix to "masquerade" all your outbound mail to use the @example.com suffix rather than @host.example.com.  I know how to do this in sendmail, but I'm not up on Postfix.

---

### Post by schmutztaucher on 2010-11-13
Thanks for the help.

You pointed me to postfix address rewriting

```
/etc/postfix/[main.cf]("http://www.postfix.org/postconf.5.html"):
    [masquerade_domains]("http://www.postfix.org/postconf.5.html#masquerade_domains") = foo.example.com example.com

```

Everything works now

---

