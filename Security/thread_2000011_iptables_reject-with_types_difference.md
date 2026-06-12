---
title: "iptables reject-with types difference"
date: 2012-06-08
forum: Security
---

### Post by codell on 2012-06-08
Hi,

I like to learn more about iptables --reject-with types. More then in the manual [http://ipset.netfilter.org/iptables.man.html](http://ipset.netfilter.org/iptables.man.html).

iptables --reject-with type
 icmp-net-unreachable
 icmp-host-unreachable
 icmp-port-unreachable
 icmp-proto-unreachable
 icmp-net-prohibited
 icmp-host-prohibited or
 icmp-admin-prohibited
 tcp-reset

What is the practical difference? Does it matter at all? Which will make applications recognizing the fail earlier? Any pros or cons?

Please provide more information.

Thanks for your efforts!

---

### Post by bodhi.zazen on 2012-06-11
There is no practical difference, it just give you the option to specify an error message as to what you are specifically rejecting.

If you are blocking ping (icmp traffic) -> icmp-admin-prohibited

If you are blocking port 80 -p -tcp --dport 80 -j REJECT , use icmp-port-unreachable

if you are blocking a host , icmp-host-unreachable ,  a subnet, icmp-net-unreachable

And on. They all do the same thing, reject, it is just specifying the error message you are sending. If you are dropping ping (icmp traffic), you have the option to specify "icmp-admin-prohibited"

---

### Post by wacky_sung on 2012-06-12
In short ICMP is simply useless [COLOR="Red"]unless[/COLOR] you are running a server/network.For me , i just block them all.

---

### Post by bodhi.zazen on 2012-06-12
> **wacky_sung said:**
> In short ICMP is simply useless [COLOR="Red"]unless[/COLOR] you are running a server/network.For me , i just block them all.

You will certainly get varying opinions, but, IMO, "just block them all" is very poor advice.

You should understand what icmp traffic is and why, or why not to block it.

There is a nice discussion here :

[http://serverfault.com/questions/84963/why-not-block-icmp](http://serverfault.com/questions/84963/why-not-block-icmp)

The general principle here is you should understand what you are doing and why before you blindly block everything "because".

---

### Post by wacky_sung on 2012-06-14
> **bodhi.zazen said:**
> You will certainly get varying opinions, but, IMO, "just block them all" is very poor advice.

You should understand what icmp traffic is and why, or why not to block it.

There is a nice discussion here :

[http://serverfault.com/questions/84963/why-not-block-icmp](http://serverfault.com/questions/84963/why-not-block-icmp)

The general principle here is you should understand what you are doing and why before you blindly block everything "because".

Oh yeah, i do aware of it and thank for sharing. That's the reason why i wanna block since it serve no purpose for me.

---

