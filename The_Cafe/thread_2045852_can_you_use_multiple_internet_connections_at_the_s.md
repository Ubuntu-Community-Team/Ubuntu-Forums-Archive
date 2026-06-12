---
title: "can you use multiple internet connections at the same time on linux?"
date: 2012-08-22
forum: The Cafe
---

### Post by madjr on 2012-08-22
This [kickstarter]("http://www.kickstarter.com/projects/523076551/dispatch-the-internet-faster") (aka "dispatch") claims you can use like 10 Internet connections at the same time.

Not sure if with some secret setting something like this is possible under linux or it would be good idea for the dev of that software to consider linux support?

for me however the best scenario would be to have an open source alternative :)

---

### Post by mips on 2012-08-22
You can but it does not work that well, especially over different technologies. I suspect they are probably just assigning different apps/sessions to different links in some crude load balancing scheme.

For linux have a look at [http://www.zeroshell.net/eng/](http://www.zeroshell.net/eng/) which is pretty cool.

---

### Post by sanderj on 2012-08-22
> **madjr said:**
> This [kickstarter]("http://www.kickstarter.com/projects/523076551/dispatch-the-internet-faster") (aka "dispatch") claims you can use like 10 Internet connections at the same time.

Not sure if with some secret setting something like this is possible under linux or it would be good idea for the dev of that software to consider linux support?

for me however the best scenario would be to have an open source alternative :)

You can do this with a plain Ubuntu install:

1) get a lot of connections and set them up individually
2) set up Ubuntu's routing table a random way to distribute network traffic over the different connections
3) use applications like bittorrent to get a higher speed. Reason: using just one IP destination will not be faster by this load balancing solution...


So ... step 1: do you have multiple connections? If not, are you willing to buy them? Because that part of the problem is *NOT* solved by the "Dispatch" kickstarter product ... :-)

---

### Post by madjr on 2012-08-22
> **sanderj said:**
> So ... step 1: do you have multiple connections? If not, are you willing to buy them? Because that part of the problem is *NOT* solved by the "Dispatch" kickstarter product ... :-)

As seen on the ks page i don't think is about "buying" more connections, but using the public ones simultaneously as you come across them as well as your own 3/4g from your cellphone.

---

### Post by Dragonbite on 2012-08-22
> **sanderj said:**
> So ... step 1: do you have multiple connections? If not, are you willing to buy them? Because that part of the problem is *NOT* solved by the "Dispatch" kickstarter product ... :-)

And I imagine using your wireless and wired NIC to connect to the same router isn't going to produce much of an increase. At least with Internet because I don't think many Internet connections go faster than the max rating of G & N wireless connections or a 100/1000 NIC.

---

### Post by ssam on 2012-08-22
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by Primefalcon on 2012-08-22
> **ssam said:**
> [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)
ha! that rocks

---

### Post by Lucradia on 2012-08-23
> **ssam said:**
> [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

Can it bond two wireless adapters?

---

