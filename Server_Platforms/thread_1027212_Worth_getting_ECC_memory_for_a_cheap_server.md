---
title: "Worth getting ECC memory for a cheap server?"
date: 2009-01-01
forum: Server Platforms
---

### Post by cowmix on 2009-01-01
I'm building a cheap 1U server:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030](http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030)

.. and it says it supports ECC memory.. Should I bother buying it?
I'll be running 8.10 server and VMWare Server 2.0.

thanks!

---

### Post by windependence on 2009-01-01
Be careful, because it may REQUIRE ECC memory. Both my production servers require registered ECC and they won't run on anything else and it's damn expensive. Some servers will take ECC or regular memory and it may interest you to know that ECC is actually slower because of the error checking. If you want to try some ECC, PM me as i have some brand new ECC I bought for a server that required registered ECC and I can't use the plain ECC in it. If you are in the states, I could ship it to you if you like the price. 

As to whether it's worth it, I don't really think so, but it's common practice to use it in production servers because of the reduced chance of CRC errors. To me, I can't really tell the difference.

-Tim

---

### Post by cowmix on 2009-01-01
It says (AFAICT) that is **can** use it.. I'll have the server in a day or two and I'll let  you know if I want / need the RAM.

thanks!

> **windependence said:**
> Be careful, because it may REQUIRE ECC memory. Both my production servers require registered ECC and they won't run on anything else and it's damn expensive. Some servers will take ECC or regular memory and it may interest you to know that ECC is actually slower because of the error checking. If you want to try some ECC, PM me as i have some brand new ECC I bought for a server that required registered ECC and I can't use the plain ECC in it. If you are in the states, I could ship it to you if you like the price. 

As to whether it's worth it, I don't really think so, but it's common practice to use it in production servers because of the reduced chance of CRC errors. To me, I can't really tell the difference.

-Tim

---

