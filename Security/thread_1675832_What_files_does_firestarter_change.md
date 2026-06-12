---
title: "What files does firestarter change?"
date: 2011-01-26
forum: Security
---

### Post by panners on 2011-01-26
Can anyone tell me what files does firestarter change? I would like to know so I can look at the files so I can learn to do the same thing without firestarter.

Thanks

p

---

### Post by amra.sonntag on 2011-01-26
Since firestarter uses iptables - you should be able to see the rules set using:
```
iptables --list
```

However the output might be really difficult to use. If you want to get a better understanding of the firewall - i recommand reading the ufw manual. (ufw is a cli for iptables) The manual is good to understand and comes with several examples on how to use it.

---

### Post by bodhi.zazen on 2011-01-26
> **panners said:**
> Can anyone tell me what files does firestarter change? I would like to know so I can look at the files so I can learn to do the same thing without firestarter.

Thanks

p

That is likely the hard way to learn iptables.

I suggest you learn the syntax for ufw, syntax for iptables is similar.

iptables is actually very straight forward, but you need to understand networking.

See if these links help :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by panners on 2011-01-26
Thanks for those links just what I was looking for. Very good

---

