---
title: "Cannot remove qmail"
date: 2010-10-28
forum: Server Platforms
---

### Post by jcooke22 on 2010-10-28
Hi all,

I am trying to install postfix but there seems to be an old install of qmail hanging on to port 25. I cannot see qmail in aptitude and I can't see any way to uninstall it.

result from:
# ps auxww | grep qmail

root      4907  0.0  0.0   3724   416 ?        S    09:08   0:00 supervise qmail-qmqpd
root      4914  0.0  0.0   3724   416 ?        S    09:08   0:00 supervise qmail-send
qmaild    4916  0.0  0.0   3760   436 ?        S    09:08   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.qmqp.cdb -c 20 -u 71 -g 71 0 628 qmail-qmqpd
root      4918  0.0  0.0   3724   412 ?        S    09:08   0:00 supervise qmail-smtpd
qmails    4920  0.0  0.0   3904   512 ?        S    09:08   0:00 qmail-send
qmaill    4923  0.0  0.0   3868   468 ?        S    09:08   0:00 multilog t /var/log/qmail-send
qmaild    4926  0.0  0.0   5988   664 ?        S    09:08   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.smtp.cdb -c 20 -u 71 -g 71 0 smtp qmail-smtpd smtp.donhost.co.uk /var/qmail/bin/smtpcheckpasswd.pl /bin/true
qmaill    4928  0.0  0.0   3868   468 ?        S    09:08   0:00 multilog t /var/log/qmail-qmqpd
root      4929  0.0  0.0   3724   416 ?        S    09:08   0:00 supervise qmail-smtpd-2500
qmaill    4931  0.0  0.0   3868   468 ?        S    09:08   0:00 multilog t /var/log/qmail-smtpd
qmaild    4933  0.0  0.0   3760   436 ?        S    09:08   0:00 /usr/bin/tcpserver -v -R -l 0 -x /etc/qmail/tcp.smtp.cdb -c 50 -u 71 -g 71 0 2500 qmail-smtpd smtp.donhost.co.uk /var/qmail/bin/smtpcheckpasswd.pl /bin/true
qmaill    4934  0.0  0.0   3868   472 ?        S    09:08   0:00 /usr/bin/multilog t /var/log/qmail-smtpd-2500
root      5012  0.0  0.0   3864   448 ?        S    09:08   0:00 qmail-lspawn ./Maildir/
qmailr    5013  0.0  0.0   3864   432 ?        S    09:08   0:00 qmail-rspawn
qmailq    5014  0.0  0.0   3852   448 ?        S    09:08   0:00 qmail-clean
root      6709  0.0  0.0   3948   668 pts/0    S+   09:09   0:00 grep qmail

It seems to be "tcpserver" which is listing on port 25.

Is there any way I can free port 25 and allow postfix to listen on it?

Thanks

---

### Post by jcooke22 on 2010-10-28
I have tried killing the PIDs and they just respawn. supervise looks like it is keeping the processes alive but I can find no way to stop this.

---

