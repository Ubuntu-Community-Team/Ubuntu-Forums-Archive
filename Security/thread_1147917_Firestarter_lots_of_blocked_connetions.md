---
title: "Firestarter lots of blocked connetions"
date: 2009-05-03
forum: Security
---

### Post by TCSnyder on 2009-05-03
i am getting 2 blocked connections from the same 2 ip addresses every second. should i be worried. they are not in my active connections, but do you think it is a bot trying to hack me?

---

### Post by lovinglinux on 2009-05-03
You didn't provide enough information to know this, but probably not.

There is not uncommon to get lots of hits, specially if you have a dynamic IP. Most people has, so when you connect to your ISP they assign you an IP number that was previously assigned to someone else. They do this because it would be much more expensive to keep a single IP for each of their costumers. Since most people don't connect all the time, they can use shared IP numbers.

So, if you get an IP that was being used by someone connected to a p2p network for examp&#314;e, the tracker responsible for connecting the peers might still have your IP listed, so everyone in the p2p swarm will try to connect to you, not knowing that you are not sharing what they need. These are called ghost connections.

Anyways, if you don't have any services listening to the port the hits are trying to connect, then there is nothing to worry about. Besides, Firestater blocked the connections anyway. You should be worried about the ones that are accepted, the ports you open and the services you have listening to those ports.

Unlike Windows, Ubuntu has no listening services by default, so you don't even need a Firewall. If you have a router, then you are probably already protected by it's own firewall.

If you install services, then you need to open the ports anyway, so people can connect to you. Who you allow to connect is another question. Then a Firewall might be useful, so you can allow only specific IPs. Nevertheless, a port open will only be a threat if the service listening to that port has some vulnerability that could be exploited.

Recommended reading - [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421)

EDIT: if you provide the port and the protocol of the connections, then we might know what are those hits.

---

### Post by ooobooontooo on 2009-05-04
I agree with lovinglinux. It's not uncommon for people to get a couple hits. The only thing that I would have to add is that I think firestarter is deprecated. In particular, it has a weird bug which makes you have to restart firestarter every time you switch from wireless to ethernet. Try "ufw".

---

### Post by TCSnyder on 2009-05-04
i found an answer, it was port 3070 or something like that, which is the xbox live port, so it only happens when i play xbox live

---

