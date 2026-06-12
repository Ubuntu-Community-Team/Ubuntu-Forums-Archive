---
title: "network problems 2 cards"
date: 2009-04-12
forum: Server Platforms
---

### Post by blindmist on 2009-04-12
So I have had this server for a little over 2 years now. I have never really tried to solve this problem because it hasn't been too much of a hassle to restart the server from home every once and a while. But with much traveling recently, this has become a big problem.

I am running the 8.04 version of ubuntu server edition. The set us is like this

I have 2 gigabit ethernet cards in here, I have even changed the cards and the same problem persists. On one of the cards, I have my house network, so I can access it locally. On the other card, it is a dedicated static ip line coming directly from the ISP. Now on the local card, I have no issues, but on the other card, every once and a while, it will just lose connection and I have to reboot the entire server (locally, cannot access it through the external ip) to get it back online.

I have done the usual sudo /etc/init.d/networking restart and I even restart squid as well.


I am somewhat of a newbie, and I am not to sure as to what information yall might need from me. I can get the info of all the files that yall will need, I am just not sure which files yall want.

Or maybe even this is a common issue and someone might have an answer off the top of their head.

---

### Post by dannyboy1121 on 2009-04-12
So when the connectivity to your ISP goes down - what do you get from:

```
ifconfig <INTERFACE NAME>
```

I'm wondering if the interface is going down or if there is loss of flow of traffic from the ISP end.

Have you tried a simple:

```
ifconfig <INTERFACE NAME> down
```
```
ifconfig <INTERFACE NAME> up
```

.. to bounce it?

---

### Post by blindmist on 2009-04-12
nevermind. I determined that lightning took it out this time... that was an expensive card to lose. At least it didnt take out the server, just the card.

anyone have good surge protection solutions for cat5-6 cable?

---

### Post by Iowan on 2009-04-12
I did a quick search and found several ethernet cable surge suppressors,  [this]("http://www.google.com/products?q=ethernet+surge+suppressor&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&ei=BYjiSaaQOaDunQecpLCtCQ&sa=X&oi=product_result_group&resnum=1&ct=title") being only the first one I found. I don't know what the warranty/guarantee is like - or if anything will STOP lightning...

---

