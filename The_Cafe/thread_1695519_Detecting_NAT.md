---
title: "Detecting NAT?"
date: 2011-02-26
forum: The Cafe
---

### Post by kevin11951 on 2011-02-26
I was wondering if it is physically possible to detect an extra NAT device on a network?

In other words, you have a large **10.0.0.0/8** network, and you setup your own **192.168.1.0/24** network inside.

Can someone on the **10.0.0.0/8** network detect the NAT device as a NAT device, and not just another host?

---

### Post by down_to_earth_sort_of_guy on 2011-02-26
Here you go...

[http://www.sflow.org/detectNAT/](http://www.sflow.org/detectNAT/)

Also, looks like there is a patent application describing a method, but be careful about using patented technology .. will have the potential to go very wrong :-)

google++

---

### Post by Dr. C on 2011-02-26
But can't this be defeated by increasing the TTL of hosts behind the NAT by 1?

---

