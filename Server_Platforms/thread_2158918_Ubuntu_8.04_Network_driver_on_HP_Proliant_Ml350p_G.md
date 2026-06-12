---
title: "Ubuntu 8.04 Network driver on HP Proliant Ml350p Gen8 doesn't work"
date: 2013-07-01
forum: Server Platforms
---

### Post by jaynava0523 on 2013-07-01
hi can someone help me ...

---

### Post by coffeecat on 2013-07-01
You are trying to get a 5-year old and now obsolete and unsupported version of Ubuntu working on a server which a google search suggests is a very recent design.

I suggest you re-install with Ubuntu 12.04 and see if that detects your network card. 12.04, both server and desktop versions, will be supported until 2017.

---

### Post by jaynava0523 on 2013-07-01
> **coffeecat said:**
> You are trying to get a 5-year old and now obsolete and unsupported version of Ubuntu working on a server which a google search suggests is a very recent design.

I suggest you re-install with Ubuntu 12.04 and see if that detects your network card. 12.04, both server and desktop versions, will be supported until 2017.

i know it works fine in 12.04 but i need to know if there is any work around that we can do to make it work on 8.04 ... 

thanks any help will be much appreciated ... ;)

---

### Post by ryan516 on 2013-07-01
Could you find the driver file on the 12.04 live CD and import it into 8.04 server?

---

### Post by CharlesA on 2013-07-01
> **ryan516 said:**
> Could you find the driver file on the 12.04 live CD and import it into 8.04 server?

Doubt it.

8.04 has been End of Life for a while now and it's unlikely anything from 12.04 will work on it.

---

### Post by jaynava0523 on 2013-07-02
> **CharlesA said:**
> Doubt it.

8.04 has been End of Life for a while now and it's unlikely anything from 12.04 will work on it.

are you saying that there's no other way to make it work on 8.04 ???

---

### Post by CharlesA on 2013-07-02
New question: Why do you need it to work with 8.04?

The HP website doesn't even list anything other than 12.04 as being supported.
[http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodTypeId=15351&prodSeriesId=5177961](http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodTypeId=15351&prodSeriesId=5177961)

---

