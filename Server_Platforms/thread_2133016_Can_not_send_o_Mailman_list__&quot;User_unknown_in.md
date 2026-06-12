---
title: "Can not send o Mailman list : &quot;User unknown in relay recipient table &quot;"
date: 2013-04-06
forum: Server Platforms
---

### Post by mscag on 2013-04-06
Hi,

I have followed the "http://library.linode.com/email/mailman/ubuntu-12.04-precise-pangolin" and installed Mailman on my fresh Ubuntu 12.04LTS server. I have also modified the DNS to include an A and MX record for my new server. Everything went fine. I have created a few lists through the web interface. 

One important problem I came accross is not being able to send message to any of the lists. The members do receive the "Welcome to the list" message from the server, but Whenever any member of any list sends a message to the list, s/he immidiately receives a message saying 

***********************
<test@lists.domain.com>: host lists.domain.com[10.0.0.24] said: 550 5.1.1
    <test@lists.domain.com>: Recipient address rejected: User unknown in relay
    recipient table (in reply to RCPT TO command)

Any idea on how I can handle this situation ?

Regards.

---

### Post by lisati on 2013-04-06
Have you configured the email aliases for your mailing list?

If you're using postfix, having a line that look something like this in your main.cf *might* be needed:
```

alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases

```

---

### Post by mscag on 2013-04-06
Hi,

Yes, the mentioned line is available, and the aliases are all correct in both the files.

---

### Post by lisati on 2013-04-06
There is a discussion of a similar problem on the mailman mailing list. The discussion can be found here: [http://mail.python.org/pipermail/mailman-users/2011-January/070896.html](http://mail.python.org/pipermail/mailman-users/2011-January/070896.html)

---

### Post by mscag on 2013-04-07
Hi again,

I have followed this thread and added 

VIRTUAL_MAILMAN_LOCAL_DOMAIN = 'localhost'

into mm_cfg.py, and also added "*hash:/var/lib/mailman/data/aliases*" at the end of the line starting with "*alias_database" and "**alias_maps**" in the file main.cf of postfix.*But unfortunately I ended up with a setup responding "mail for lists.domain.com loops back to myself" for every message sent to the list. At the end of the thread, the gentelmen who seems to found a solution, points to a howto page, which does no longer exists.

Any help appriciated.

---

### Post by mscag on 2013-04-07
Hi,

I have observed that "http://library.linode.com/email/mailman/ubuntu-12.04-precise-pangolin" has many missing issues like wrong file ownerships of "...../aliases" files, logging and debugging feature, message archiving feature, self-service subscription/unsubscription feature, let alone making Mailman work itself. Or may be, I couldn't do it.

Below is the address which I followed and installed the current version of Mailman on a fresh Ubuntu 12.04LTS server. Without any issue, the setup was up and running in 15 minutes.

[http://free-electrons.com/blog/mailman-howto-ubuntu-10-04/](http://free-electrons.com/blog/mailman-howto-ubuntu-10-04/)

Regards.

---

