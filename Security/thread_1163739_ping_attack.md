---
title: "ping attack"
date: 2009-05-19
forum: Security
---

### Post by sulekha on 2009-05-19
Hi all,

  can any help/explain me to protect my ubuntu machine against 
  D.O.S ping attacks such as this

  ping ip -t -l 65500 ?

---

### Post by The Cog on 2009-05-19
I think that using a firewall like **gufw** or **guarddog** you can block incoming ping requests. You cartainly can if you configure iptables directly (gufw and guarddog are GUI front-ends for driving iptables which is a command-line firewall configurer). 

But ignoring pings won't prevent a DDOS from flooding your link with ping requests. You would need help from your ISP if that ever happened. All ignoring the pings would do is to avoid flooding your upload bandwidth with replies.

---

### Post by kryptikos on 2009-05-19
DOS are always a pain, however there are some things you can do to mitigate your machine from being drastically affected. You can use the built in UFW Ubuntu firewall, or throw on a third party one (such as Firestarter)...but you can use ipchains. 

This is an older article, but the concepts are the same and it is a good study.

[http://articles.techrepublic.com.com/5100-10878_11-1047763.html]("http://articles.techrepublic.com.com/5100-10878_11-1047763.html")

---

### Post by bodhi.zazen on 2009-05-19
DOS are easy to handle with iptables.

For ping :

```
sudo iptables -A INPUT -p icmp -m limit --limit 1/sec -j ACCEPT
```

Other tips here :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by sulekha on 2009-05-22
> **bodhi.zazen said:**
> DOS are easy to handle with iptables.

For ping :

```
sudo iptables -A INPUT -p icmp -m limit --limit 1/sec -j ACCEPT
```

Other tips here :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)



thankx a lot for that info. BTW how to block this sort of attack, without
using iptables, as a matter of fact editing files such as sysctl.conf

---

### Post by Alias1407 on 2009-05-22
65MB's aren't going to do much to your system.

I wouldn't worry too much.

If the person who is doing it keeps doing it then report their IP adress.

---

