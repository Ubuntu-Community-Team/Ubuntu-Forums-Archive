---
title: "Email Server with out domain network only"
date: 2012-02-03
forum: Server Platforms
---

### Post by sligoman on 2012-02-03
Hi

Is it possible to setup a email server with ubuntu on localhost with users able to use email clients (thunderbird or outlook) and still be able to send emails via WAN without a domain?

If so anyone have any idea how to or a link to instructions...


Thanks in advance

---

### Post by sligoman on 2012-02-04
Take it that's a no then....

---

### Post by volkswagner on 2012-02-04
Because you did not receive a response within 12 hours does not mean it's not possible.

It is polite to allow at least 24 hours prior to bumping a thread.

I'm no expert but there are a few issues with your plan.  You also did not mention why you want this setup.

When you have a residential connection, you are likely to get a dynamic ip address from you ISP.  Most mail servers such as gmail, yahoo and isp's will reject mail coming from a dynamic ip address.  You will need a domain name with a reverse lookup as this is also tested by mail servers you will be attempting to send to.

If you really want to setup a mail server at home, you will want to use a relay such as gmail or your isp provider.

Running a mail server is not trivial nor shall it be blindly setup without understanding the impact, such as providing an open relay for spammers.

It would be best for you to offer more detail about what and why you want to setup.

---

