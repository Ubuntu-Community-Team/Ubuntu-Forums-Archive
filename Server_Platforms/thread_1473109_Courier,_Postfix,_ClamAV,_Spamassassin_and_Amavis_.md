---
title: "Courier, Postfix, ClamAV, Spamassassin and Amavis Setup"
date: 2010-05-04
forum: Server Platforms
---

### Post by mlbarnes on 2010-05-04
I am currently running Ubuntu Server 9.10 and followed this HOWTO on setting up my email server. 

[https://help.ubuntu.com/community/PostfixAmavisNewClamAVSpamAssassin](https://help.ubuntu.com/community/PostfixAmavisNewClamAVSpamAssassin)

Everything seems to work correctly. If I look in the Maildir the emails I send to test are there.

The problem is when I try to sync my email via IMAP from my windows box (on a different network) it doesn't show any of my email nor does it deliver new email. My email app doesn't  give any errors nor does the logs on the server. How can I get it so my email syncs to windows computer? I am sure it is something really small that I am over looking but I can't seem to find it anywhere. I don't know if you need to see any of my config files but I can post them if needed.

---

### Post by cariboo on 2010-05-04
This question will get better answers in the server section. Moved.

---

### Post by mlbarnes on 2010-05-05
> **cariboo907 said:**
> This question will get better answers in the server section. Moved.

Thanks, I wasn't sure where to post it.

---

### Post by TheFuturian on 2010-05-06
Have you had a look at the mail log?

```
tail -n 100 /var/log/mail.log
```

Just out of curiosity, how come you picked Courier over Dovecot?

---

### Post by windependence on 2010-05-06
If you need to do this again, you may want to consider trying Zimbra. It's everything you built all in one package and works extremely well. There is also an install package for 8.04LTS, and support if you need it. Upgrades are much easier too, as you can upgrade the whole package at once instead of worrying about each piece individually.

-Tim

---

### Post by mlbarnes on 2010-05-06
I figured it out today. It was looking in the wrong place for my email. I added home_mailbox = Maildir/ to my /etc/postfix/main.cf and it fixed the problem.

---

