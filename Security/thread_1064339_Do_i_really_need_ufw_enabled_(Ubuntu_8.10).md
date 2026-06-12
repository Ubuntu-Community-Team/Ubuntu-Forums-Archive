---
title: "Do i really need ufw enabled (Ubuntu 8.10)"
date: 2009-02-08
forum: Security
---

### Post by weisel on 2009-02-08
I don't have ufw enabled do i actually need it for security reasons. I don't bank online and i know just about every site i am going to visit. Only thing i use is firefox noscript. Thanks

---

### Post by cariboo on 2009-02-08
If you haven't installed any other services besides the defaults, there is no need to run a firewall as there are no ports listening for input. If you run a port scan on your own computer the only service you will see is 631, which is cups, that can only be accessed locally.

Jim

---

### Post by brian_p on 2009-02-08
> **weisel said:**
> I don't have ufw enabled do i actually need it for security reasons. I don't bank online and i know just about every site i am going to visit. Only thing i use is firefox noscript. Thanks

For collecting mail and web browsing ufw does not add any security. It doesn't do anything for online banking either. I'd leave it alone. You won't be missing out on anything.

---

### Post by weisel on 2009-02-08
My question was answered and thanks for the replys.

---

