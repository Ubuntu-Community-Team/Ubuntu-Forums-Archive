---
title: "unknown user vmail postfix, dovecot"
date: 2012-07-07
forum: Server Platforms
---

### Post by makoshark55 on 2012-07-07
Hello
I am running 10.04 LTS on a xen VPS and am having errors with my email setup. I followed the instructions here: [https://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid](https://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid). My fatal error is unknown user vmail. I get this in the email log: ```
Jul  7 10:35:46 nilandsplace postfix/oqmgr[27403]: 46DE5A4724: from=<phplinkd@vps.phplinkdirectory.com>, size=2298, nrcpt=1 (queue active)
Jul  7 10:35:47 nilandsplace postfix/pipe[3677]: fatal: get_service_attr: unknown username: vmail
Jul  7 10:35:48 nilandsplace postfix/oqmgr[27403]: warning: private/dovecot socket: malformed response
Jul  7 10:35:48 nilandsplace postfix/oqmgr[27403]: warning: transport dovecot failure -- see a previous warning/fatal/panic logfile record for the problem description
Jul  7 10:35:48 nilandsplace postfix/master[27401]: warning: process /usr/lib/postfix/pipe pid 3677 exit status 1
Jul  7 10:35:48 nilandsplace postfix/master[27401]: warning: /usr/lib/postfix/pipe: bad command startup -- throttling
Jul  7 10:35:48 nilandsplace postfix/error[3678]: 46DE5A4724: to=<nilandjp@nilandsplace.com>, relay=none, delay=67657, delays=67656/1.7/0/0.02, dsn=4.3.0, status=deferred (unknown mail transport error)

```vmail is user 5000 and group 5000. So I don't know why it would be unknown. If I set up users they seem to be unknown too. I have never been an administrator before so I am at the mercy of others to find out what I need to know
Thanks for your help

---

