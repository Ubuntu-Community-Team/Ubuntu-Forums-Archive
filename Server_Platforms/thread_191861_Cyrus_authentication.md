---
title: "Cyrus authentication"
date: 2006-06-08
forum: Server Platforms
---

### Post by catfox on 2006-06-08
Hi all,
i'm struggling with setting up a cyrus imap server. i've got the service running, and can telnet to localhost 143 etc.
in my imapd.conf, i have
```

admins: admin backend

```
but cant figure out how to set their passwords. i've tried saslpasswd2 admin, and putting a password, but when i try:
```

cyradm -u admin localhost

```
and use the same password, it doesn't authenticate.

does anyone have an idea where the passwords can be properly set?

---

