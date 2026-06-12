---
title: "DNS issues"
date: 2012-07-16
forum: Server Platforms
---

### Post by glennbtn on 2012-07-16
HI All

I am still quite new to Linux but have a 10.4 server and have installed zimbra using what they call split dns.

I am no where near an exper but keep getting these errors emailed to me through ossec.

Received From: mail->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Jul 15 19:59:05 mail named[855]: error (connection refused) resolving '141.53.94.32.bl.spamcop.net/TXT/IN': 72.232.197.50#53

I also keep seeing these errors when I start up.

Jul 15 12:51:26 mail named[7314]: /etc/bind/db.0.0.127:8: unknown RR type 'mail.myserver.co.uk.'
Jul 15 12:51:26 mail named[7314]: zone 0.0.127.in-addr.arpa/IN: loading  from master file /etc/bind/db.0.0.127 failed: unknown class/type
Jul 15 12:51:26 mail named[7314]: zone 0.0.127.in-addr.arpa/IN: not loaded due to errors.

Can anyone advise as dns seems to get and send email ok

Thanks

Glenn

---

