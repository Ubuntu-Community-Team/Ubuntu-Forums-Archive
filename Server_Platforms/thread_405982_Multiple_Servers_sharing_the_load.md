---
title: "Multiple Servers sharing the load?"
date: 2007-04-10
forum: Server Platforms
---

### Post by U2XS on 2007-04-10
I am currently setting up a server with ubuntu.  This particular machine isn't the best and I was curious if Ubuntu allows for simple upgrades so that I can have two or more servers serving the same domain names.  Thanks

---

### Post by rgeddes on 2007-04-11
I believe there are several ways to load balance a server.  

A cheap, simple way is through dns... you can google dns and "load balancing" to find references.

Here's one to get you started:

[http://www.zytrax.com/books/dns/ch9/rr.html](http://www.zytrax.com/books/dns/ch9/rr.html)

---

### Post by U2XS on 2007-04-11
Just what the doctor ordered!  Thanks for pointing me in the right direction to start!

---

### Post by shubjero on 2007-04-11
DNS round robin is less than stellar for load balancing.

If you are a little more serious you can try setting up a load balacer (default Ubuntu install) and use ipvsadm to balance requests of whatever service you want to load balance (http, https, ftp, whatever) based on an LB algorithm of your choice (there are several) and use mon to monitor two real internal servers which will perform checks on the servers to make sure they are available, and pull a server out of the LB pool if it is not functioning as it should.

It's quite a bit complicated and I'm sorry but can't provide you with any more details but it can be done as I work on setups similar to this on a daily basis.

If you have any more questions regarding this just post a reply and I'll see if I can answer it for you.

Best of luck!

---

### Post by U2XS on 2007-04-11
Understood, thanks!  No one said it was going to be easy :)  I may not be at that step yet (as I still have a lot of learning & reading to do before I ask questions) but I wanted to know if this version of the OS was capable of handling my needs when I got to them.

---

