---
title: "opendkim failures"
date: 2010-07-26
forum: Server Platforms
---

### Post by gdanko on 2010-07-26
**Here is my /etc/opendkim.conf:**

Syslog			yes
UMask			002

Domain			hookit.com
KeyFile			/etc/mail/dkim.key
Selector		        mail2

Mode			sv
SubDomains		no
ADSPDiscard		no
LogWhy			yes

**Here is the DKIM config from main.cf:**

milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891

**Here are the DNS records:**

_domainkey.hookit.com.		IN	TXT	"t=y; o=-;"

mail2._domainkey.hookit.com.	IN	TXT	"k=rsa; t=y; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDVWW2CUQ4Mzm46oNzpn309iaZ7A1+bE1HgmgE4nDZqNpjhovShDRjK+GMKfV03/O7BJ5L2sm2bW8H2pQhjS55qYaDgxrOx6V+IbNI1M9JY/g2OTfdcdMbyIoNN8DdiB0gyb/VUNZmHhXN2EVcag9zdjCPmjTzw/xZpFPWU5rXZXwIDAQAB"

The server is an internal relay for servers in the same subnet, 172.16.10.0/24. If I try to send an email while logged into the mail server I see the following errors in the mail.log. What could I be doing wrong?

Jul 26 16:05:30 ns1 postfix/pickup[28697]: 75B39D00FD: uid=0 from=<root>
Jul 26 16:05:30 ns1 postfix/cleanup[28703]: 75B39D00FD: message-id=<20100726230530.75B39D00FD@mail2.hookit.com>
Jul 26 16:05:30 ns1 opendkim[28750]: 75B39D00FD no signing domain match for `mail2.hookit.com'
Jul 26 16:05:30 ns1 opendkim[28750]: 75B39D00FD no signing subdomain match for `mail2.hookit.com'
Jul 26 16:05:35 ns1 opendkim[28750]: 75B39D00FD ADSP query: timeout DNS query for `mail2.hookit.com'
Jul 26 16:05:35 ns1 opendkim[28750]: 75B39D00FD: no signature data
Jul 26 16:05:35 ns1 postfix/qmgr[28698]: 75B39D00FD: from=<root@mail2.hookit.com>, size=372, nrcpt=1 (queue active)
Jul 26 16:05:35 ns1 postfix/smtp[28706]: 75B39D00FD: to=<xxx@xxx.com>, relay=gmail-smtp-in.l.google.com[72.14.213.27]:25, delay=5.4, delays=5/0/0.1/0.28, dsn=2.0.0, status=sent (250 2.0.0 OK 1280185559 z1si8710759wfd.8)

---

### Post by gdanko on 2010-07-27
Okay I can now sign messages but I am getting this one last error in mail.log:


Jul 26 21:23:11 ns1 postfix/pickup[30070]: 353F5D001B: uid=0 from=<root>
Jul 26 21:23:11 ns1 postfix/cleanup[4966]: 353F5D001B: message-id=<20100727042311.353F5D001B@mail2.hookit.com>
**Jul 26 21:23:11 ns1 opendkim[4956]: 353F5D001B no signing domain match for `mail2.hookit.com'**
Jul 26 21:23:11 ns1 postfix/qmgr[28698]: 353F5D001B: from=<root@mail2.hookit.com>, size=372, nrcpt=1 (queue active)
Jul 26 21:23:12 ns1 postfix/smtp[4968]: 353F5D001B: to=<xxx@xxx.com>, relay=gmail-smtp-in.l.google.com[74.125.53.27]:25, delay=1.8, delays=0.18/0.01/0.21/1.4, dsn=2.0.0, status=sent (250 2.0.0 OK 1280204616 e3si9321360wam.41)
Jul 26 21:23:12 ns1 postfix/qmgr[28698]: 353F5D001B: removed

Any idea how to fix "no signing domain match" errors?

---

