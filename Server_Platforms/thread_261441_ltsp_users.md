---
title: "ltsp users"
date: 2006-09-20
forum: Server Platforms
---

### Post by yemu on 2006-09-20
hi
how to add users to my ltsp server? i added a user using adduser command (on a server) but I can't log using this user from terminals. do I have to do something to allow normal users log from terminals?
thanks in advance for any suggestions
yemu

---

### Post by bluefrog on 2006-09-27
what error is it giving you when you try to log in from a thin client?

James

---

### Post by dalo on 2006-09-27
you have to update your ssh-keys this is done by tybing following kode into a
terminal window

```
sudo ltsp-update-sshkeys

```

---

### Post by fnjordy on 2006-09-27
> **dalo said:**
> you have to update your ssh-keys this is done by tybing following kode into a
terminal window

The OP implies some users can already login, this step is redundant.

As bluefrog suggests what error message do you see?  An alternative is to login with a user that does work then bring up a terminal and use SSH to login locally and then verify /var/log/auth.log and /var/log/messages for any errors:

```

$ ssh *new-user-name*@localhost

```

---

### Post by Kalif on 2006-11-02
well, I had a similar problem. My password
worked well for a normal ssh shell session
but not for authentication for an ldm lstp
session. My password turned out to be to
short when beeing 6 characters; then changing
password to something longer worked out fine :-)

Best,
K.

---

