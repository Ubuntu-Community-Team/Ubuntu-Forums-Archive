---
title: "hosts.allow"
date: 2009-09-08
forum: Server Platforms
---

### Post by Cardale on 2009-09-08
How would you setup your hosts allow file to accept any local lan user to ssh into the server? or even on specific workstation on the lan?

I try

ssh : LOCAL : allow

and that didn't work

I also tried

ssh : 127.0.0.1 : allow

and that didn't work

Thanks.

---

### Post by wojox on 2009-09-08
Try:

```
ALL : 192.168.1.0/255.255.254.0
```

---

### Post by Cardale on 2009-09-08
Thanks ..alright sweet got it work...what about if I want users to beable to see my webserver from outside my lan?

http : ALL ?

---

### Post by wojox on 2009-09-08
If you mean just web pages I would port forward port 80 and 443 on my router. That how I have mine set up.

---

### Post by Cardale on 2009-09-08
443? why? Don't I have to include some kind of hosts allow information to?

---

### Post by Cardale on 2009-09-08
Well I looked up port 443 https.

---

