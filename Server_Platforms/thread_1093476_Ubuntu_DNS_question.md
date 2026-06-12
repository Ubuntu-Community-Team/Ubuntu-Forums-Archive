---
title: "Ubuntu DNS question"
date: 2009-03-11
forum: Server Platforms
---

### Post by grimm08 on 2009-03-11
I have been using Ubuntu desktop for over three months and decided to take a crack at Ubuntu server.  I installed Bind and was able to get it working, but having minor problems geting it to work with my Windows DNS server at work.  My question is I know with Windows creating reverse lookup zone you specify the subnet down to the third octet.  Do you do the same with Bind or go all the way to the forth octet when creating your zones?

---

### Post by wdaly on 2009-03-11
yes it's 3 octets. (reversed:)

think this is what your looking for
[http://www.zytrax.com/books/dns/ch3/]("http://www.zytrax.com/books/dns/ch3/")

---

### Post by grimm08 on 2009-03-12
Thanks appreciate it.

---

