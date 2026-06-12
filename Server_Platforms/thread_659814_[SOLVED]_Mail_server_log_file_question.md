---
title: "[SOLVED] Mail server log file question"
date: 2008-01-06
forum: Server Platforms
---

### Post by DSK on 2008-01-06
I found this in my log file for postfix.  I assume its an attempt to compromise my system.  Do I have anything to be concerned about?

Jan  1 01:51:22 ###### postfix/smtpd[6541]: connect from 203-70-51-232.adsl.dynamic.seed.net.tw[203.70.51.232]
Jan  1 01:51:23 ###### postfix/smtpd[6541]: NOQUEUE: reject: RCPT from 203-70-51-232.adsl.dynamic.seed.net.tw[203.70.51.232]: 554 5.7.1 <evo86tw@gmail.com>: Relay access denied; from=<baby@gmail.com> to=<evo86tw@gmail.com> proto=SMTP helo=<###.###.###.###>
Jan  1 01:51:24 ###### postfix/smtpd[6541]: lost connection after RCPT from 203-70-51-232.adsl.dynamic.seed.net.tw[203.70.51.232]
Jan  1 01:51:24 ###### postfix/smtpd[6541]: disconnect from 203-70-51-232.adsl.dynamic.seed.net.tw[203.70.51.232]
Jan  1 01:54:44 ###### postfix/anvil[6544]: statistics: max connection rate 1/60s for (smtp:203.70.51.232) at Jan  1 01:51:22
Jan  1 01:54:44 ###### postfix/anvil[6544]: statistics: max connection count 1 for (smtp:203.70.51.232) at Jan  1 01:51:22
Jan  1 01:54:44 ###### postfix/anvil[6544]: statistics: max cache size 1 at Jan  1 01:51:22

Jan  1 13:21:42 ###### postfix/smtpd[9278]: connect from unknown[218.16.119.142]
Jan  1 13:21:42 ###### postfix/smtpd[9278]: NOQUEUE: reject: RCPT from unknown[218.16.119.142]: 554 5.7.1 <dvdr0503@yahoo.com.cn>: Relay access denied; from=<youipopo@yahoo.com> to=<dvdr0503@yahoo.com.cn> proto=SMTP helo=<###.###.###.###>
Jan  1 13:21:43 ###### postfix/smtpd[9278]: lost connection after RCPT from unknown[218.16.119.142]
Jan  1 13:21:43 ###### postfix/smtpd[9278]: disconnect from unknown[218.16.119.142]
Jan  1 13:25:03 ###### postfix/anvil[9280]: statistics: max connection rate 1/60s for (smtp:218.16.119.142) at Jan  1 13:21:42
Jan  1 13:25:03 ###### postfix/anvil[9280]: statistics: max connection count 1 for (smtp:218.16.119.142) at Jan  1 13:21:42
Jan  1 13:25:03 ###### postfix/anvil[9280]: statistics: max cache size 1 at Jan  1 13:21:42

---

### Post by MJN on 2008-01-06
Not so much 'compromise', but rather an attempt to use you as relay for spam in the hope that you're an 'open relay' (i.e. willing to relay mail for unauthenticated/untrusted clients).

Your server is behaving correctly so nothing to worry about.

Mathew

---

### Post by DSK on 2008-01-06
Thank you much for the reply.  Wanted to make sure I was being responsible server admin!

:guitar:

---

