---
title: "Forward a port locally"
date: 2009-02-11
forum: Server Platforms
---

### Post by _Dan on 2009-02-11
Hi, I'm not sure the correct term for this. But I am running a flash video server on port 1935 but I would also like it accessible by clients connecting to port 80 (and maybe also a few others).

So is it possible to set up so these other ports forward to the actual port the program is running on?

Thanks :)

---

### Post by JeppeM on 2009-02-11
Hey Dan,

Are you running Ubuntu server? what you're most likely looking for it port redirecting using iptables.

something like this should do it for you i think:

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 1935

make sure that it is indeed eth0 you want it to work on (this will only change if you have more than one network card in the server)

---

### Post by _Dan on 2009-02-11
Thanks Jeppe! I'll look into iptables.

---

### Post by _Dan on 2009-02-11
Ok, back again.

I'm getting this error message: ""No chain/target/match by that name"

It seems that the "Chain" PREROUTING and possibly the target REDIRECT are not installed or something.

I've googled and found suggestions that installing the module "iptable_nat" or something might be a good idea. But I can't find any instructions on how.

---

