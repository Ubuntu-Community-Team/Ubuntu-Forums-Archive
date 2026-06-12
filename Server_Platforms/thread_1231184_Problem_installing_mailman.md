---
title: "Problem installing mailman"
date: 2009-08-04
forum: Server Platforms
---

### Post by vagamente on 2009-08-04
I'm tryng to install mailman with postfix  in my VPS (the mailboxes are directly managed by the web-hoster) . I followed the how-to and i guess everything is ok. I tihnk i've some problem of misconfiguration 'cause if i try to send an invitation mail, mail.log logs

```
Aug  1 16:22:55 www postfix/master[26938]: daemon started -- version 2.5.1, configuration /etc/postfix
Aug  1 16:25:32 www postfix/smtpd[26998]: connect from localhost[127.0.0.1]
Aug  1 16:25:32 www postfix/smtpd[26998]: warning: Illegal address syntax from localhost[127.0.0.1] in MAIL command: <prova-bounces@89.31.74.211>
Aug  1 16:25:32 www postfix/smtpd[26998]: disconnect from localhost[127.0.0.1]
```

an message is not delivered.

Any suggestions?
Thanks

---

### Post by cdunbar on 2009-08-04
Hello,

It appears to be upset that an @ IP address is being specified instead of an @ domain name. Were you successfully using Postfix on this server prior to installing or Mailman or are they both basically new? The reason I ask is that the problem may be in the Postfix config and not the Mailman config.

Regards,
Chris

---

### Post by vagamente on 2009-08-07
Thanks, but...

Now i think i've messed'em up too much... ;-)

Here they are, if some of you could take a look:
. [/etc/apache2/sites-available/mailman.conf]("http://pastebin.com/f299879f1") : [http://pastebin.com/f299879f1](http://pastebin.com/f299879f1)
. [/etc/postfix/main.cf]("http://pastebin.com/f65f9432f") : [http://pastebin.com/f65f9432f](http://pastebin.com/f65f9432f)
. [/etc/postfix/master.cf]("http://pastebin.com/f56b257d7") : [http://pastebin.com/f56b257d7](http://pastebin.com/f56b257d7)

Need some more?

Thanks

---

