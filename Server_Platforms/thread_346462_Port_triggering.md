---
title: "Port triggering"
date: 2007-01-25
forum: Server Platforms
---

### Post by tinman on 2007-01-25
Hi All,

I was wondering if you use port triggering to resolve my ip or domain name without having to 

type the port number after?  ex. mydomain.com:1111 or 99.999.99.99:1111

Is there a way to get around that?:confused:  Thanks

---

### Post by kidders on 2007-01-25
Hi there,

Your question is a little confusing. :confused: I'm not sure what port triggering has to do with DNS resolution.

Perhaps you are trying to run a web server on port 1111? If so, there is no reason why you can't, but your visitors will of course need to specify the correct port number.

---

### Post by tinman on 2007-01-25
Yes, you are quite right :D , after a little research I figured out that I could use web forwarding with my DNS. Is this the only way with an ISP that blocks port 80?

---

### Post by kidders on 2007-01-26
Yeah, 'fraid so. :-(

Well... if you have nice friends, there are other possibilities, but it amounts to more or less the same thing. Basically, someone needs to accept connections on port 80 on your behalf and forward them to you on whatever port your web server is really running on. Whether that "someone" is your DNS provider or a friend of yours makes very little difference.

---

