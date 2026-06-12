---
title: "Dapper LTS Server kernel max # of eth interfaces?"
date: 2007-05-31
forum: Server Platforms
---

### Post by CounterStrike on 2007-05-31
Hello all,

I am running 2.6.15-28-amd64-xeon kernel and have two onlboard nics (e1000) and also have a quad Intel gig card (also uses e1000). I can get all of the interfaces up and configured except for eth4 (of which I don't think this particular one is significant). When trying to assign an ip via ifconfig (ifconfig eth4 10.10.1.4) i get this message eth4: ERROR while getting interface flags: No such device
   However, I just stumbled across that I can assign eth6 to it and it works. so now I have the following
eth0
eth1
eth2
eth3
eth5
eth6

Is There any rhyme or reason why eth4 can't be used in this situation? Thanks for shedding some light on this.

Thanks,

Ted

---

