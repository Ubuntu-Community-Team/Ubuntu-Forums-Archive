---
title: "Email Server Solutions?"
date: 2011-05-15
forum: Server Platforms
---

### Post by kevin11951 on 2011-05-15
So far I have found (and used) Citadel/UX and Zimbra.

I was wondering if there are any others that I missed.

What I am looking for is an email solution with an easy to use integrated webmail gui like Zimbra...  But light enough to run on a VPS for example.

Anything?

(Commercial support as an option would be nice too ;))

---

### Post by volkswagner on 2011-05-15
I have not found anything easier than Citadel.

What don't you find easy, or what don't you like about Citadel?

I run it on a modest VPS alongside Apache2 server.  Granted both Apache and Citadel get minimal use, but I could just ramp up the server if I need to.  I only get a few hundred web hits, ~20 emails per day with only a few users.

```
top - 20:14:51 up 176 days, 14:14,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  32 total,   1 running,  31 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  0.1%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    786432k total,   413576k used,   372856k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

```

What is your usage like?

---

### Post by elico on 2011-05-16
zimbra is one hell good system...
if you need only mail you can use postfix+dovecot+rouncubemail\squirrelmail or any imap\pop3 mail client.
much more efficient for most mail users

---

### Post by Lars Noodén on 2011-05-16
> **kevin11951 said:**
> So far I have found (and used) Citadel/UX and Zimbra.

Those are more than just mail servers.  Those are groupware.  In groupware category you should also take a look at [Kolab](http://www.kolab.org/), [OpenGroupware](http://www.opengroupware.org/) and [Bedework](http://www.bedework.org/)

If you are looking for only a mail server, then the list starts with [simta](http://rsug.itd.umich.edu/software/simta/), [Dovecot](http://www.dovecot.org/), [Postfix](http://www.postfix.org/), [Exim](http://www.exim.org/), [Sendmail](http://www.sendmail.org/)

---

### Post by Lars Noodén on 2011-05-16
> **kevin11951 said:**
> 
What I am looking for is an email solution with an easy to use integrated webmail gui like Zimbra... 

The client is separate from the server.  If you want a web client then one to consider is [Roundcube](http://roundcube.net/).

---

