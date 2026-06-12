---
title: "Sending Mail to Fax"
date: 2011-03-22
forum: Server Platforms
---

### Post by gnagnibu on 2011-03-22
Hi all!
I'm setting my Ubuntu Server as a Fax Server, to send mail to fax.
I've correctly configured Hylafax and Postfix, but I've got this error:
when sending mail, /var/log/mail.info says:

Mar 22 10:38:04 postfix/pipe[18710]: D77AA3601B1: to=<FaxMaster@XXXXXX.domain.com>, orig_to=<FaxMaster>, relay=fax, delay=0.3, delays=0.2/0/0/0.1, dsn=5.3.0, status=bounced (Command died with status 255: "/usr/bin/faxmail". Command output: faxmail: Cannot create temp directory /tmp//faxmail.rdqNMa. )

It seems that postfix can't create dirs into /tmp

So, it's better to change tmp permissions or try to configure another tmp directory where postfix can write (and how to do this???)?

Thanks

---

### Post by SeijiSensei on 2011-03-22
/tmp usually has 1777 permissions, read/write to everyone plus the "[sticky bit]("http://en.wikipedia.org/wiki/Sticky_bit")."  If you type "ls -l /" you should see "drwxrwxrwt" as the permissions on /tmp.  If it's not set to that, then run "sudo chmod 1777 /tmp" to fix it.

---

### Post by gnagnibu on 2011-03-22
I don't understand why /tmp has 755 permissions... maybe my several tests...
Changing permissions solve the problem.
I'm really sorry.

Thanks.

PS: faxmaster needs to create dirs into /tmp, not postfix.

---

