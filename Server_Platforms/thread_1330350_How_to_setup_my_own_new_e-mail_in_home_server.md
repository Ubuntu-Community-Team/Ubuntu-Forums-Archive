---
title: "How to setup my own new e-mail in home server?"
date: 2009-11-18
forum: Server Platforms
---

### Post by Raymond Day on 2009-11-18
I am not sure if this could be done.

I think it be very neat if I could make up my own e-mail just for me. I have a http name that gets forword to a Ubuntu server I run in my house with port 80 forword to it.

So if I can how would I set up so I have like a e-mail name of like [email]name@myhttp.com[/email]

Is there any step-by-step way to tell how?

Then it be cool if can set up like Windows live mail to send and get mail from that server. Is there a way to do this?

-Raymond Day

---

### Post by fahadsadah on 2009-11-18
If you have an MX record on the domain, then you can install a mailserver.

```
tasksel
```
And add the Mail Server role.

---

