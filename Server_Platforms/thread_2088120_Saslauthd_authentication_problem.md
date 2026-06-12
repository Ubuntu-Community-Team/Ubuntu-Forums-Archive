---
title: "Saslauthd authentication problem"
date: 2012-11-25
forum: Server Platforms
---

### Post by JellyJim on 2012-11-25
My server has developed an expected problem where I am unable to connect from a mail client.

I've looked at the server logs and the only thing that looks to identify a problem are events like the following:

> Nov 23 18:32:43 hig3 dovecot: imap-login: Login: user=, method=PLAIN, rip=xxxxxxxx, lip=xxxxxxx, TLS Nov 23 18:32:55 hig3 postfix/smtpd[11653]: connect from xxxxxxx.co.uk[xxxxxxx] Nov 23 18:32:55 hig3 postfix/smtpd[11653]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory Nov 23 18:32:55 hig3 postfix/smtpd[11653]: warning: xxxxxxx.co.uk[xxxxxxxx]: SASL LOGIN authentication failed: generic failure Nov 23 18:32:56 hig3 postfix/smtpd[11653]: lost connection after AUTH from xxxxxxx.co.uk[xxxxxxx] Nov 23 18:32:56 hig3 postfix/smtpd[11653]: disconnect from xxxxxxx.co.uk[xxxxxxx]

The problem is unusual, because just half an hour previously at my office, I was not being prompted for a correct username and password in my mail client. I haven't made any changes to the server, so I can't understand what would have happened to make this error occur.

Searches for the error messages yield various results, with 'fixes' that I'm uncertain of (obviously don't want to make it worse or fix something that isn't broken).

When I run

> testsaslauthd -u xxxxx -p xxxxxx

I also get the following result:

> connect() : No such file or directory

But when I run

> testsaslauthd -u xxxxx -p xxxxxx -f /var/spool/postfix/var/run/saslauthd/mux -s smtp

I get:

> 0: OK "Success."

I found those commands on another forum and am not entirely sure what they mean, but I'm hoping they might give an indication of where the problem might lie.

When I run

> ps -ef|grep saslauthd

This is the output:

> root 1245 1 0 Nov24 ? 00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5 root 1250 1245 0 Nov24 ? 00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5 root 1252 1245 0 Nov24 ? 00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5 root 1254 1245 0 Nov24 ? 00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5 root 1255 1245 0 Nov24 ? 00:00:00 /usr/sbin/saslauthd -a pam -c -m /var/spool/postfix/var/run/saslauthd -r -n 5 root 5902 5885 0 08:51 pts/0 00:00:00 grep --color=auto saslauthd

If it makes any difference, I'm running Ubuntu 10.04.1, Postfix 2.7.0 and Webmin/ Virtualmin.

---

