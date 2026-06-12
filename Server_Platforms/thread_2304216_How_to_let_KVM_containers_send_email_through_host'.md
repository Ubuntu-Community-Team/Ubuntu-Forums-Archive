---
title: "How to let KVM containers send email through host's Postfix"
date: 2015-11-25
forum: Server Platforms
---

### Post by Matheo84 on 2015-11-25
It's enough to add their IPs (10.0.3.x) to $mynetwork? if so, how to modify this line?
```
127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```
Thanks in advance!

---

### Post by TheFu on 2015-11-25
Probably not. Not enough details to say more.

Are the host and client  on the same subnet?
Is the host configure as a relay-host? For that subnet?
Is the client configured as a satellite?
Are the firewalls open for SMTP between the systems?

---

### Post by Matheo84 on 2015-11-26
Indeed, I would need to read more about networking to have a better idea of what can be done.
In the mean time, I figured out the outgoing email through gmail :) Thanks

---

### Post by TheFu on 2015-11-27
> **Matheo84 said:**
> Indeed, I would need to read more about networking to have a better idea of what can be done.
In the mean time, I figured out the outgoing email through gmail :) Thanks

Would be nice if you shared the gmail-specific config, as many people seem interested in that, NOT running a normal email server. Please.

---

### Post by Matheo84 on 2015-11-28
@TheFu oh, but I configured my web platform to do that.

Perhaps, in my research I saw many posts using sasl authentication to connect with gmail and use their smtp server.
Googling it should be enough ;)

---

