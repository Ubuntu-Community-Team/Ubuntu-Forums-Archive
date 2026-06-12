---
title: "solid-pop3d gives permission denied on opening mailbox"
date: 2010-01-31
forum: Server Platforms
---

### Post by Jotijo on 2010-01-31
Hi.  The user &quot;abimail&quot; has a mailbox specified in /home/abimail/.spop3d which is /var/mail/abimail.  The permissions of /var/mail/abimail are: ```
 -rwxrwx--- 1 abimail mailgroup 192113 2010-01-28 20:24 /var/mail/abimail 
```  When logging in to solid-pop3d as user abimail and attempting to fetch mails, the login works but it will pop up the error &quot;can't open mailbox file&quot;; syslog entries: ```
Jan 31 17:38:10 h1347290 solid-pop3d[23857]: user abimail authenticated - 87.176.220.50
Jan 31 17:38:10 h1347290 solid-pop3d[23857]: mailbox: can't open mailbox file: /var/mail/abimail
Jan 31 17:38:10 h1347290 solid-pop3d[23857]: mailbox: open: Permission denied

```  I did an strace on solid-pop3d while it tries to do that which reveals: ```
[pid 22404] open(&quot;/var/mail/abimail&quot;, O_RDWR) = -1 EACCES (Permission denied)
``` (Basically it simply shows that it is indeed accessing that file, and indeed getting EACCES when trying to do that and not failing at something else)  Now my question is: why doesn't it just work?  PS: Complain to forum administrators for broken &quot; things.

---

### Post by Jotijo on 2010-02-07
Any hint appreciated. I must be missing something obvious, but can't figure out what it is.

---

### Post by gmargo on 2010-02-09
solid-pop3d runs in the group "mail".  Your mailbox file's group is "mailgroup", but should be "mail".  Where did "mailgroup" come from?

---

