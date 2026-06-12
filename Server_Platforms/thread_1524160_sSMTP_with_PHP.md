---
title: "sSMTP with PHP"
date: 2010-07-04
forum: Server Platforms
---

### Post by pEkvo on 2010-07-04
So I'm developing a small website for a friend of mine which is going to use a cron job to send out emails to members as notifiers. So I need to use a mailserver. I've been trying with postfix, exim4 and sendmail but to no avail.

I then found sSMTP and I can send mails via my terminal without any problem. But I can't mail from PHP using the mail() function.

In my php.ini I have:

```
sendmail_path = /usr/bin/ssmtp -t
```

When I try to create symlink this happens:

```
ln -s /usr/sbin/sendmail /usr/sbin/ssmtp
ln: creating symbolic link `/usr/sbin/ssmtp': File exists
```

I have no idea why it sends mail through my terminal but not PHP. I'm new to this so no super complicated reponses please :-p.

---

### Post by hictio on 2010-07-04
You have restarted Apache after editing the php.ini file, right?
Why do you need to create that symbolic link?

---

### Post by pEkvo on 2010-07-04
Yes, I restarted the apache server. I don't know, it was suggested at some other forum, although I could have mixed up the instructions from different MTAs. Should I 'uncreate' the symlink? How would I do that?

---

