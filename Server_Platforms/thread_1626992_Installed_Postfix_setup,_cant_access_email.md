---
title: "Installed Postfix setup, cant access email"
date: 2010-11-20
forum: Server Platforms
---

### Post by clay7 on 2010-11-20
Hello,

I installed [Postfix]("https://help.ubuntu.com/community/Postfix"), [Amavis-new + Spamassassin + Clamav]("https://help.ubuntu.com/community/PostfixAmavisNew"), [Dovecot]("https://help.ubuntu.com/community/Dovecot"), and [SquirrelMail]("https://help.ubuntu.com/community/Squirrelmail") today, using the Ubuntu guides for each. I have 10.04 LTS Server. 

My PHP scripts can send email, but when I tried to log into Squirrelmail, I couldn't. Here is what my error log produced (the server name and user name have been changed) :

```
myserver dovecot: imap-login: Login: user=<username>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
 myserver dovecot: IMAP(username): opendir(/home/username/Maildir) failed: Permission denied (euid=1000(username) egid=1000(username) missing +r perm: /home/username/Maildir)
 myserver dovecot: IMAP(username): stat(/home/username/Maildir/.INBOX.Sent/tmp) failed: Permission denied (euid=1000(username) egid=1000(username) missing +x perm: /home/username/Maildir)
 myserver dovecot: IMAP(username): Connection closed bytes=53/411
 myserver dovecot: imap-login: Login: user=<username>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
 myserver dovecot: IMAP(username): stat(/home/username/Maildir/tmp) failed: Permission denied (euid=1000(username) egid=1000(username) missing +x perm: /home/username/Maildir)
```

Any ideas??

---

### Post by clay7 on 2010-11-21
Solved: The guide, which I followed without really thinking, had me make the owner of the mail folders "700". The owner should have been me. I hope this helps someone.

---

