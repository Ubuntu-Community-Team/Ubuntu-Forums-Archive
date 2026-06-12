---
title: "[SOLVED] Postfix SMTP hostname problem"
date: 2008-07-25
forum: Server Platforms
---

### Post by Dr Small on 2008-07-25
On my mailserver, my hostname is:
```
mycroft
```

But the mailname is:
```
mycroftserver.homelinux.org
```

When I send outgoing mail to hackermail.com, I get:
```
<drsmall@hackermail.com>: host hackermail-com.mr.outblaze.com[64.62.181.94]
    said: 504 <drsmall@**mycroft**>: No thank you rejected: need fully-qualified
    address (in reply to RCPT TO command)
```

And then the mail never gets delivered. How do I solve this problem?

---

### Post by k_grdn on 2008-07-25
Hi,


You can set your hostname with the myhostname = directive in main.cf, also you can set your domain with the mydomain directive.


Regards,

k_grdn

---

### Post by Dr Small on 2008-07-25
These options are already set in my /etc/postfix/main.cf file, and postfix has already been reloaded:
```
myhostname = mycroftserver.homelinux.org
mydomain = mycroftserver.homelinux.org
```

---

### Post by k_grdn on 2008-07-25
Hi,


What do you have myorigin set to?


Regards,


k_grdn

---

### Post by Dr Small on 2008-07-25
```
myorigin = $mydomain
```

Also, from reading the posfix documentation, it looks as if I need to do some masquerade_domains, but I am not really clear on how to use them.

I added:
```
masquerade_domains = mycroftserver.homelinux.org
```

But it still didn't seem to help.

Dr Small

---

### Post by k_grdn on 2008-07-25
Hmmmmmm.


Shouldn't your domain be homelinux.org, you don't need to masquerade domains.


Regards,


k_grdn

---

### Post by Dr Small on 2008-07-25
No, I do not own homelinux.org, because I have a subdomain off of DynDNS.org.

Also, on a sidenote, if I add:
```
append_dot_mydomain = yes
```

Mail will send, but in the header's it will say:
```
drsmall@mycroft.mycroftserver.homelinux.org
```

---

### Post by k_grdn on 2008-07-25
So if your domain is: mycroftserver.homelinux.org


What is your mailname? this will be the hostname prefix to your domain.


Regards,


k_grdn

---

### Post by Dr Small on 2008-07-25
My domain is:
```
mycroftserver.homelinux.org
```

My Mailname is:
```
mycroftserver.homelinux.org
```

My System Hostname is:
```
mycroft
```

But, I just got it solved anyhow. I tried both the masquerading and rewrite and got it to work.
```
append_dot_mydomain = yes
masquerade_domains = mycroftserver.homelinux.org
```

Now, mail sends, and when it is received on the other end, it looks correct.

Thanks for your time and patience.

Dr Small

---

### Post by MJN on 2008-07-25
Whilst you've worked around the issue you ought to take a look at the configuration of your client as it is its responsibility to provide a fully qualified address when advising sender details to the MTA.

Mathew

---

### Post by Dr Small on 2008-07-25
> **MJN said:**
> Whilst you've worked around the issue you ought to take a look at the configuration of your client as it is its responsibility to provide a fully qualified address when advising sender details to the MTA.

Mathew
The client is SqWebmail found in Ubuntu's Repositories, hosted on the same server.

---

