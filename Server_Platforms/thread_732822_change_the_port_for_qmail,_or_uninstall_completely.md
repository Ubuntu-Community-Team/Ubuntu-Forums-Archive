---
title: "change the port for qmail, or uninstall completely"
date: 2008-03-23
forum: Server Platforms
---

### Post by leewilson78 on 2008-03-23
Hi all, 

My Ubuntu powered server came with QMail configured, the only problem I have is trying to run SpamAssassin with it, can't get it to work. I decided to install Postfix since there seems to be more support help on this site, with regards to configuring SA. 

Everything seems to install fine, but I just don't know how to remove Qmail, I have a feeling it is using the same port as Postfix.

Thanks

---

### Post by Oldsoldier2003 on 2008-03-23
> **leewilson78 said:**
> Hi all, 

My Ubuntu powered server came with QMail configured, the only problem I have is trying to run SpamAssassin with it, can't get it to work. I decided to install Postfix since there seems to be more support help on this site, with regards to configuring SA. 

Everything seems to install fine, but I just don't know how to remove Qmail, I have a feeling it is using the same port as Postfix.

Thanks

have you tried ```
sudo dpkg -r qmail
```

---

### Post by leewilson78 on 2008-03-23
Cheers for the quick reply buddy, strangely, here is the message I get back when I try the above:

```
dpkg - warning: ignoring request to remove qmail which isn't installed.

```

hmmm, pretty sure its running.

---

### Post by leewilson78 on 2008-03-23
Literally on day on learning SSH and command lines, found this command:

ps auxww | grep qmail

which I believe tells me if qmail is running, here is what I get:
```

root      5214  0.0  0.0    104    20 ?        S    08:40   0:00 supervise qmail-smtpd
root      5216  0.0  0.0    100    20 ?        S    08:40   0:00 supervise qmail-send
root      5224  0.0  0.0    104    20 ?        S    08:40   0:00 supervise qmail-qmqpd
75        5227  0.0  0.0    112    32 ?        R    08:40   0:00 multilog t /var/log/qmail-smtpd
qmails    5228  0.0  0.0   1592   412 ?        S    08:40   0:00 qmail-send
75        5229  0.0  0.0    108    28 ?        S    08:40   0:00 multilog t /var/log/qmail-send
75        5231  0.0  0.0    112    36 ?        S    08:40   0:00 multilog t /var/log/qmail-qmqpd
root      5242  0.0  0.0   1564   344 ?        S    08:40   0:00 qmail-lspawn ./Maildir/
qmailr    5243  0.0  0.0   1556   320 ?        S    08:40   0:00 qmail-rspawn
qmailq    5244  0.0  0.0   1548   340 ?        S    08:40   0:00 qmail-clean
qmaild   12003  0.0  0.0    124    48 ?        S    11:07   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.qmqp.cdb -c 20 -u 71 -g 71 0 628 qmail-qmqpd
qmaild   12007  0.0  0.0    124    48 ?        S    11:07   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.smtp.cdb -c 20 -u 71 -g 71 0 smtp qmail-smtpd smtp.donhost.co.uk /var/qmail/bin/smtpcheckpasswd.pl /bin/true
qmaild   13251  0.0  0.0   1444   312 ?        S    11:42   0:00 qmail-smtpd smtp.donhost.co.uk /var/qmail/bin/smtpcheckpasswd.pl /bin/true
root     13777  0.0  0.0   1624   488 pts/0    R+   12:00   0:00 grep qmail
qmaild   13778  0.0  0.0   1440   304 ?        S    12:00   0:00 qmail-smtpd smtp.donhost.co.uk /var/qmail/bin/smtpcheckpasswd.pl /bin/true
```

The donhost.co.uk is not actually my own server, its the parent company of my hosting providerl 123-reg.

Is there anyway I can disable using their smtpd server, they don't have me any spam filters?

Appreciate any help.

Thanks
Lee

---

