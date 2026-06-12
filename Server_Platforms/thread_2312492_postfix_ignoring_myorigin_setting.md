---
title: "postfix ignoring myorigin setting?"
date: 2016-02-04
forum: Server Platforms
---

### Post by Moses_Moore on 2016-02-04
Using Ubuntu 14.03.3 LTS, postfix 2.11.0-1ubuntu1.

The machine's hostname is 'alpha.company.com', and it has to send important alerts to employees of company.com.  Unfortunately, company.com will throw any email in the trash if it's addressed "someone@company.com" and the origin IP address isn't a machine owned by a big TLA.  So I have to make all outgoing email from this machine addressed "someone@notcompany.com".

In the Postfix instructions, I'm lead to believe that I should change 'myorigin' in /etc/postfix/main.cf to beta.notcompany.com, or I set it to /etc/mailname, and edit /etc/mailname to contain "beta.notcompany.com".   I do either, restart postfix, and send an email, and it's still sending mail affixing "@alpha.company.com" to the end.

The only way I can get postfix to send "@beta.notcompany.com" mail is if I do `hostname beta.notcompany.com` and then restart postfix.

It seems postfix is ignoring the 'myorigin' configuration setting.  Am I misunderstanding the postfix config?  Is there a more proper way I can tell postfix to default to using '@beta.notcompany.com' to all outgoing mail without a suffix, without having to change the machine's hostname and thus mucking up the configuration of every other daemon on that machine?

---

### Post by Moses_Moore on 2016-02-05
> `hostname`
> alpha.company.com

> postconf -n
> mydomain = beta.notcompany.com
> myhostname = beta.notcompany.com
> myorigin = beta.notcompany.com

> telnet localhost 25
> 220 beta.notcompany.com ESMTP Postfix (Ubuntu)

And yet when I do `echo "ping" |mail [EMAIL="moses@homemachine.com"]moses@homemachine.com[/EMAIL]` , I still see in the mail logs it uses "From: [EMAIL="root@alpha.company.com"]root@alpha.company.com[/EMAIL]" .  What am I doing wrong?

> Feb  5 09:43:22 alpha postfix/qmgr[6488]: 27215631E9: from=<root@alpha.company.com>, size=360, nrcpt=1 (queue active)

---

### Post by Moses_Moore on 2016-02-05
Found it.  It's not postfix appending that @alpha.company.com, it's /usr/bin/mail, which is a softlink to /usr/bin/mail.mailutils .
GNU mail is appending the @`hostname`, not postfix.  If I use /usr/sbin/sendmail instead it's fine.

---

### Post by Habitual on 2016-02-05
Good catch and great job, well done, Moses!

---

