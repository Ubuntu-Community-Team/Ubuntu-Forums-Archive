---
title: "Sendmail w/ Google Apps Conflict"
date: 2010-12-20
forum: Server Platforms
---

### Post by Joeb454 on 2010-12-20
I have sendmail installed on my server, and it sends emails fine, as you'd expect it to. That is, provided the email isn't [email]anyuser@mydomain.com[/email], which it then just sends locally, despite the MX records pointing to Google's servers.

**dig mx +short mydomain.com** returns ```
5 alt1.aspmx.l.google.com.
10 aspmx2.googlemail.com.
1 aspmx.l.google.com.
5 alt2.aspmx.l.google.com.
``` So I know that the MX records also resolve properly.

I've tried editing /etc/hosts to read **host.mydomain.com**, but then it stops sending emails altogether.

Is there any way to make sendmail send these emails to users at my domain as well as everybody else?

---

### Post by stmiller on 2010-12-21
You can try this with sendmail to in effect disable local delivery:

[http://serverfault.com/questions/65365/disable-local-delivery-in-sendmail](http://serverfault.com/questions/65365/disable-local-delivery-in-sendmail)

```
define(`MAIL_HUB', `example.com.')dnl
define(`LOCAL_RELAY', `example.com.')dnl
```

---

### Post by SeijiSensei on 2010-12-21
The file /etc/mail/local-host-names contains a list of all domains and hostnames for which sendmail uses local delivery. Often the installer will put entries there for the local machine.  If you don't want local delivery for anything other than localhost, remove the remaining entries from local-host-names.

---

### Post by Joeb454 on 2010-12-22
> **SeijiSensei said:**
> The file /etc/mail/local-host-names contains a list of all domains and hostnames for which sendmail uses local delivery. Often the installer will put entries there for the local machine.  If you don't want local delivery for anything other than localhost, remove the remaining entries from local-host-names.

I saw this mentioned on a few sites I looked at before posting here, oddly the domain name in question was never in that file, only localhost was.

> **stmiller said:**
> You can try this with sendmail to in effect disable local delivery:

[http://serverfault.com/questions/65365/disable-local-delivery-in-sendmail](http://serverfault.com/questions/65365/disable-local-delivery-in-sendmail)

```
define(`MAIL_HUB', `example.com.')dnl
define(`LOCAL_RELAY', `example.com.')dnl
```

Adding those 2 lines to the end of /etc/sendmail.mc and re-running sendmailconfig worked perfectly, thanks!

---

