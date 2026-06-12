---
title: "Halyfax and Postfix mail to fax"
date: 2011-03-22
forum: Server Platforms
---

### Post by gnagnibu on 2011-03-22
Hi all!
I have a working hylafax server on a Ubuntu Server 10.04 and I want to configure postfix to set up mail to fax feature.
For example, my lan domain is: mydomain.it
FQDN of the fax server will be: faxserver.mydomain.it
My questions are:

1) postfix documentations ([http://www.postfix.org/faq.html#fax](http://www.postfix.org/faq.html#fax)) says to not advertise FQDN of the server into DNS... but how can I send e-mails??
2) we already have a mail server on the same lan (mail.mydomain.it that manage mail @mydomain.it), may it cause problems?

---

### Post by SeijiSensei on 2011-03-22
It would probably be a lot simpler if you configure Postfix on the fax server to use mail.mydomain.it as a "smart host" using a Postfix directive in the main.cf file like:

```
relayhost = mail.mydomain.it
```

---

### Post by gnagnibu on 2011-03-23
> **SeijiSensei said:**
> It would probably be a lot simpler if you configure Postfix on the fax server to use mail.mydomain.it as a "smart host" using a Postfix directive in the main.cf file like:

```
relayhost = mail.mydomain.it
```

But relyhost is for outgoing mail, not for ingoing, isn't it?
I don't really understand why I don't have to advertise my server on DNS...

---

### Post by SeijiSensei on 2011-03-23
Whoops, my bad.  Let's start again.  

Are all the desktop clients configured to use mail.domain.it as their SMTP relay?  If so, you could probably configure mail.domain.it to forward messages addressed to [email]something@fax.domain.it[/email] over to the Hylafax host.  I can do this in sendmail quite easily using its "[mailertable]("http://www.sendmail.org/m4/mailertables.html")" feature. I presume other MTAs like Postfix and Exim can do the same.

This approach would avoid the need to publish a DNS record for fax.domain.it because users wouldn't be sending mail directly there.  They'd be sending the faxes to mail.domain.it and letting it forward them to fax.domain.it.  Create an entry in /etc/hosts for fax.domain.it with the Hylafax server's address.

---

### Post by gnagnibu on 2011-03-25
The solution was so simple :D

Thanks SeijiSensei

Bye!

---

