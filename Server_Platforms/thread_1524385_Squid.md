---
title: "Squid"
date: 2010-07-05
forum: Server Platforms
---

### Post by Notino on 2010-07-05
Hello,

I am wanting to setup a squid server I have 50 IP addresses and would like to use nsa_auth BUT I want each IP address to be origional.

Such as user1 using 80.80.80.81 and it actually gives you that IP not the main one.
Then next user using 80.80.80.82 and it gives him/her that IP.

Using nsa_auth for username and password authentication.

Any ideas / advice?

Thanks.

---

### Post by koenn on 2010-07-05
you got  it all wrong

squid has nothing to do with assigning IP addreses to users. Not even to computers. 

you might want to explain what you're actually trying to do there.

---

### Post by infamous-online on 2010-07-09
> **Notino said:**
> Hello,

I am wanting to setup a squid server I have 50 IP addresses and would like to use nsa_auth BUT I want each IP address to be origional.

Such as user1 using 80.80.80.81 and it actually gives you that IP not the main one.
Then next user using 80.80.80.82 and it gives him/her that IP.

Using nsa_auth for username and password authentication.

Any ideas / advice?

Thanks.


You need a DNS server for that I believe, squid doesn't do what you're wanting it to do. Squid is a caching server.

---

