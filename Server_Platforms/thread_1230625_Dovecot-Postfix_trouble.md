---
title: "Dovecot-Postfix trouble"
date: 2009-08-03
forum: Server Platforms
---

### Post by comandrei on 2009-08-03
Today I've installed a mail server on top of a  Jaunty x64 OS.
I did :
```

apt-get install dovecot-postfix

```
Then changed the mail_location to 
```

mail_location = mbox:~/mail:INBOX=/var/mail/%u
mail_privileged_user=mail

```
in /etc/dovecot/dovecot-postfix.conf

I can send mails, but i can't receive any mails.


```

#in /var/log/mail.err there are a lot of messages like

Aug  3 22:45:20 timmy deliver(fester): file_lock_dotlock() failed with mbox file /var/mail/fester: Permission denied


ls -ld /var/mail
drwxrwsr-x 2 root mail 4096 2009-08-03 21:46 mail

root@timmy:/var/mail# ls -l
total 0
-rw------- 1 director mail 0 2009-08-03 21:46 director
-rw------- 1 fester   mail 0 2009-08-03 16:56 fester

```

What do i have to do to receive mails?
PS : /var is mounted as a separate partition with nodev,realtime as mount options.

---

### Post by Wistful on 2009-08-18
Please read the post in the Romanian forum. 

Which suggested to use :

> sudo chmod a+wr /var/mail

---

