---
title: "Sendmail help please"
date: 2008-05-23
forum: Server Platforms
---

### Post by infosys on 2008-05-23
I'm running sendmail, and would like to stick with it instead of changing to something else. However, it does not seem to be working. I've had several different permissions problems before, so I suspect my issues are related to permissions, just don't know what files need what permissions.

Here is my problem though, sendmail is not sending mail. Simple enough, right?

Some additional information:

From /var/log/mail.info I'm getting:
"May 23 03:40:04 perldesk sm-msp-queue[17310]: m4JG01PH004931: to=root, ctladdr=smmsp (106/113), delay=3+18:40:03, xdelay=00:00:00, mailer=relay, pri=390385, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]"

From /var/log/mail.err I'm getting:
"May 23 03:10:36 perldesk sendmail[17170]: NOQUEUE: SYSERR(infosys): can not chdir(/var/spool/mqueue-client/): Permission denied"
-and-
"May 23 03:11:16 perldesk sendmail[17180]: NOQUEUE: SYSERR(www-data): can not chdir(/var/spool/mqueue-client/): Permission denied"

When I try running the command "sendmail" I get:
"WARNING: RunAsUser for MSP ignored, check group ids (egid=1000, want=113)
can not chdir(/var/spool/mqueue-client/): Permission denied
Program mode requires special privileges, e.g., root or TrustedUser.
infosys@perldesk:/var/log$"
even if I do "sudo sendmail".

Anybody have any thoughts, things I should look at, etc.?

-Thanks in advance

---

### Post by infosys on 2008-05-23
Maybe this has taken care of it...

I changed the group permissions of /usr/lib/sm.bin/sendmail to sr from xr. Now when I do the sendmail command it's not coming back with any errors. That's the good news.

The bad news is I still don't seem to be getting any mail in my inbox. Anybody know what/where I should be looking now?

---

### Post by windependence on 2008-05-23
Can you tell us why you want to stay with sendmail?

-Tim

---

