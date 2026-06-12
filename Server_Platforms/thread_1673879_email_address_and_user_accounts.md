---
title: "email address and user accounts"
date: 2011-01-23
forum: Server Platforms
---

### Post by MightyMe on 2011-01-23
I'm setting up a mail server for the first time using Postfix and Dovecot on Ubuntu 10.04. So far I have managed to send and receive mail between user accounts on my example domain, for example mail between [email]john1@mydomain.net[/email] and [email]john2@mydomain.net[/email]. 

How do I connect their real email addresses to the accounts and send mail between [email]john.smith@mydomain.net[/email] and [email]john.jackson@mydomain.net[/email]? I have not set up LDAP authentication yet.

Any help would be much appreciated.

---

### Post by SeijiSensei on 2011-01-23
Use aliases.  Edit as root the file /etc/aliases and add entries like this:

```
john.smith:          john1
john.jackson:        john2
```

Then run (again as root) the command "newaliases" to update the alias database. See "man aliases" for more details.

---

### Post by MightyMe on 2011-01-24
Works like a charm. Thanks.

---

