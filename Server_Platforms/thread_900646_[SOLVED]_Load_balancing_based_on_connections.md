---
title: "[SOLVED] Load balancing based on connections"
date: 2008-08-25
forum: Server Platforms
---

### Post by xravexheavenx on 2008-08-25
I am looking into load balancing some connections and am wondering the best way to go about it.  what we are looking to do is route all traffic to one server up to about 90% of the connection limits and then re-route all other traffic to the next machine.  When the connections drop on machine 1, we want it to transfer connections from machine 2 on to machine 1 until it hits the 90% or so and then go back and forth like that.  

What would be the best way of going about that?

---

### Post by ilrudie on 2008-08-25
[http://lartc.org/](http://lartc.org/)
BAM!


But seriously its a complicated topic and reading up on it may be your best bet.  The above link can help you set up a Linux-based load balancer.  I'm sure there is some sort of appliance you can buy where someone already setup Linux or BSD to load balance for you but where's the fun in that?

---

### Post by xravexheavenx on 2008-08-26
Thanks! :)

I really didn;t have the time to do all the reading on it at the moment so I just ran "balancer" and ran it based on connections since I was at work and needed it done quickly.  Reading up on it in my free time now though! :)

---

