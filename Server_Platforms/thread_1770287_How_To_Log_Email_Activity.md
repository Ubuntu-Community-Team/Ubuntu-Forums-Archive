---
title: "How To Log Email Activity"
date: 2011-05-29
forum: Server Platforms
---

### Post by own3mall on 2011-05-29
How do I log email activity on my server?  I'd like to see who's trying to login and who's sending email.

This shows most of what I want, but I'm not sure how to have the log saved daily and sent to my email address.  

```


tail -f /var/log/syslog


```

Is there a better way to log email activity?  If so, how do I log it?  I'm using Ubuntu 10.04 as my server.

---

### Post by Lars Noodén on 2011-05-29
You could try putting your Mail Transfer Agent (MTA) behind [Xinetd](http://linux.die.net/man/5/xinetd.conf) and use xinetd's exta logging capabilities.  Take a look at the manual page for **xinetd.conf** and see if there is anything of use to you.

---

### Post by Lars Noodén on 2011-05-29
By the way, which MTA are you using for this?

---

### Post by own3mall on 2011-05-29
> **Lars Noodén said:**
> By the way, which MTA are you using for this?

Postfix

---

### Post by Lars Noodén on 2011-05-29
It looks like it is possible to [log from and to](http://www.seaglass.com/postfix/faq.html#lgsbj) if that's what you were looking for.

---

