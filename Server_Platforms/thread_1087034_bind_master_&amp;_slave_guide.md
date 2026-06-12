---
title: "bind master &amp; slave guide"
date: 2009-03-04
forum: Server Platforms
---

### Post by j_reacher on 2009-03-04
hi, i have to do a new system with two servers ubuntu 8.10 for dns role
I've configured with this guide
[http://www.howtoforge.com/debian_bind9_master_slave_system](http://www.howtoforge.com/debian_bind9_master_slave_system)

but i've problem with rndc and permission and more
I think this guide is optimized for old system..maybe
Does anyone suggest me a good step by step guide for installing a double server dns master/slave in replica ? 
In particular, for example i would to know why rndc.conf is non present in this guide and in my system, if i've to create and how to write in

great confusion..many trouble..if you suggest me a perfect procedure i will be a new happy fan of server ubunt and replace other server system

thanx a lot

---

### Post by jlintz on 2009-03-04
rndc-confgen > rndc.key

then in your named.conf

include "/etc/rndc.key";

or whatever path your rndc.key is at.

---

### Post by j_reacher on 2009-03-05
thanx...so you suggest me to make my configuration reading the debian's guide and include this command for the correct procedure?

---

### Post by jlintz on 2009-03-06
I'd go with BIND's manuals available on their website

---

