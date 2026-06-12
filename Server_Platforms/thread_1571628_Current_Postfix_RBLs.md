---
title: "Current Postfix RBLs"
date: 2010-09-09
forum: Server Platforms
---

### Post by Zeophlite on 2010-09-09
I've been trying to set up a mail server using: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I get the following error in /var/log/mail.warn:
```

daniel@Mustrum:~$ tail /var/log/mail.warn
Sep  8 01:54:40 Mustrum postfix/smtpd[6505]: warning: 106.101.168.118.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=106.101.168.118.dnsbl.njabl.org type=A: Host not found, try again
Sep  8 15:37:04 Mustrum postfix/smtpd[7286]: warning: 51.99.168.118.sbl.spamhaus.org: RBL lookup error: Host or domain name not found. Name service error for name=51.99.168.118.sbl.spamhaus.org type=A: Host not found, try again
Sep  8 15:37:04 Mustrum postfix/smtpd[7286]: warning: 51.99.168.118.blackholes.easynet.nl: RBL lookup error: Host or domain name not found. Name service error for name=51.99.168.118.blackholes.easynet.nl type=A: Host not found, try again
Sep  8 15:37:05 Mustrum postfix/smtpd[7286]: warning: 51.99.168.118.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=51.99.168.118.dnsbl.njabl.org type=A: Host not found, try again
Sep  9 01:50:09 Mustrum postfix/smtpd[7872]: warning: 118.139.11.124.sbl.spamhaus.org: RBL lookup error: Host or domain name not found. Name service error for name=118.139.11.124.sbl.spamhaus.org type=A: Host not found, try again
Sep  9 01:50:09 Mustrum postfix/smtpd[7872]: warning: 118.139.11.124.blackholes.easynet.nl: RBL lookup error: Host or domain name not found. Name service error for name=118.139.11.124.blackholes.easynet.nl type=A: Host not found, try again
Sep  9 01:50:10 Mustrum postfix/smtpd[7872]: warning: 118.139.11.124.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=118.139.11.124.dnsbl.njabl.org type=A: Host not found, try again
Sep 10 09:25:03 Mustrum postfix/smtpd[9681]: warning: 1.0.0.127.sbl.spamhaus.org: RBL lookup error: Host or domain name not found. Name service error for name=1.0.0.127.sbl.spamhaus.org type=A: Host not found, try again
Sep 10 09:25:04 Mustrum postfix/smtpd[9681]: warning: 1.0.0.127.blackholes.easynet.nl: RBL lookup error: Host or domain name not found. Name service error for name=1.0.0.127.blackholes.easynet.nl type=A: Host not found, try again
Sep 10 09:25:04 Mustrum postfix/smtpd[9681]: warning: 1.0.0.127.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=1.0.0.127.dnsbl.njabl.org type=A: Host not found, try again
daniel@Mustrum:~$

```

In /etc/postfix/main.cf I have the following line:
```

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

```

Which RBL clients are currently in service and considered good by you?

Thanks for your help.

---

### Post by lisati on 2010-12-18
Apologies for the delay replying: if you have alread found a solution, please at least mark your thread "solved".

I'd suggest using zen.spamhaus.org instead of sbl.spamhaus.org

---

### Post by HermanAB on 2010-12-19
spamhaus and spamcop are good.

---

