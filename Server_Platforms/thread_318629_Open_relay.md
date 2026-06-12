---
title: "Open relay?"
date: 2006-12-14
forum: Server Platforms
---

### Post by cpminga on 2006-12-14
I recently received an email from contact@mydomain to contact@mydomain. It was delivered to my maibox as a catchall. I sometimes get mail delivered TO various_things@mydomain, but this one was differnt in that it was supposidly sent FROM mydomain. I've tested my server against several open relay testing sites, and all failed to find a hole. I'm thinking that this was just spoofed and my account wasn't actually used as the sender. Below is the output from /var/log/mail.log. Can anyone allay my fears or should I be concerned?

```
Dec 13 18:30:49 localhost postfix/smtpd[21674]: connect from 81-172-32-7.usuarios.retecal.es[81.172.32.7]
Dec 13 18:30:51 localhost postfix/smtpd[21674]: 107FF54804F: client=81-172-32-7.usuarios.retecal.es[81.172.32.7]
Dec 13 18:30:51 localhost postfix/cleanup[21678]: 107FF54804F: message-id=<20061213233051.107FF54804F@elebug.net>
Dec 13 18:30:52 localhost postfix/qmgr[20847]: 107FF54804F: from=<contact@elebug.net>, size=773, nrcpt=1 (queue active)
Dec 13 18:30:52 localhost postfix/local[21679]: 107FF54804F: to=<jnkastler@elebug.net>, orig_to=<contact@elebug.net>, relay=local, delay=2, status=sent (deli
vered to command: IFS=' ' && exec /usr/bin/procmail || exit 75 #jnkastler)
Dec 13 18:30:52 localhost postfix/qmgr[20847]: 107FF54804F: removed
Dec 13 18:30:52 localhost postfix/smtpd[21674]: disconnect from 81-172-32-7.usuarios.retecal.es[81.172.32.7]
```

---

### Post by bjd on 2006-12-14
Whether you're an open relay or not does not really matter here since the recipient is a local user for the server. Since the checks indicate your not, you're probably ok.
The address is almost certainly spoofed. The sender can put anything they want in the From: field, so it can't be trusted. It's not necessarily the real sender's address.

---

### Post by cpminga on 2006-12-14
Would something like SPF help here? If so, is that possible with postfix?

---

### Post by cpminga on 2006-12-14
Well, to answer my own post, yes.. it looks like SPF is possible. Found this site [http://www.freesoftwaremagazine.com/articles/focus_spam_postfix/](http://www.freesoftwaremagazine.com/articles/focus_spam_postfix/) and may go through it if this becomes a problem

---

