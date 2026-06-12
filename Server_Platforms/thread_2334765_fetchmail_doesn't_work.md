---
title: "fetchmail doesn't work"
date: 2016-08-22
forum: Server Platforms
---

### Post by france68 on 2016-08-22
Hi,
i installed fetchmail on Ubuntu 14.04 because i need to fetch mails from an external server mailbox and manage them in LAN with Zimbra but it doesn't works.
The fetchmailrc file is: 

```
set daemon 600
poll imap.server_esterno.it with proto IMAP
user "info@server_esterno.it" pass "password" is "utente@server_interno" keep
```


No mail is fetched.
With ```
fetchmail -v
``` results:
```
no mailserver specified
```.

Please, could you help me?
Thank's

---

### Post by SeijiSensei on 2016-08-22
> imap.server_esterno.it 

That isn't a valid domain name since underscores are not permitted.  I tried replacing the underscore with a hyphen, which is a valid character, but that name doesn't resolve to an IP address either.  Nor does imap.server.esterno.it.  You need to contact the IMAP provider and get the correct name.

---

### Post by france68 on 2016-08-22
Thank's for your reply but imap.server_esterno isn't the real server, it's only an example.
The real server is correct and ping reacheable.

---

### Post by SeijiSensei on 2016-08-22
Can you open a telnet session and connect to its port 143?  Try this:
```

$ telnet server.example.org 143
[server replies]
100 login yourusername yourpassword

```
What happens?

---

### Post by france68 on 2016-08-23
yes, this is the result:

> Connected to server.example.org.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot ready.


---

### Post by SeijiSensei on 2016-08-23
According to this [https://www.howtoforge.com/debian_etch_fetchmail](https://www.howtoforge.com/debian_etch_fetchmail), there is no "with" keyword in the poll command.  Since Ubuntu is a Debian derivative, that document might be helpful.  The Linode guide might also be of assistance: [https://www.linode.com/docs/email/clients/using-fetchmail-to-retrieve-email](https://www.linode.com/docs/email/clients/using-fetchmail-to-retrieve-email).

---

