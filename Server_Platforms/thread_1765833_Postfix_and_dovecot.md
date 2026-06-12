---
title: "Postfix and dovecot"
date: 2011-05-23
forum: Server Platforms
---

### Post by tapi0n on 2011-05-23
So setting up postfix and using dovecot 2 as an LMTP server. I'm still very new to this and I'm quite stuck.

when doing

```
nc mx.sub.domain.tld port
```I don't get any errors and always get 'OK' as response. So I'm assuming postfix is configured correctly.

now when checking mail.log

I get messages like these (it's a scripted mail I think, from my lecturer at school)

```
 postfix/virtual[5007]: 983932B0C2BD: to=<user@sub.domain.tld>, relay=virtual, delay=0.01, delays=0.01/0/0/0, dsn=4.2.0, status=deferred (maildir delivery failed: create maildir file /var/vmail/user/tmp/1306181435.P5007.gil: Permission denied)

```in dovecot.conf I put I put

```
mail_location = maildir:/var/vmail
```as path, so I correctly pointed to where store mails right?

Now I read that postfix runs chrooted. And we've been tasked to create a dovecot lmtp listener under /var/spool/postfix/private/.

I've looked into the listener, used multiple sources. But I just don't understand what to do and where. But most importantly why.

Hoping someone can help me with this. 

Cheers

---

### Post by tapi0n on 2011-05-30
Bump please, still looking for a solution to this and can't find one :(


Edit: Found out there was a permission error on /var/vmail/user.

---

