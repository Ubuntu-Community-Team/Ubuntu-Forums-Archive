---
title: "AppArmor -- basic question"
date: 2010-09-02
forum: Security
---

### Post by Gurtz on 2010-09-02
Hi all,

Forgive this very rudimentary question. I know AppArmor can be used to lock down access to parts of the file system, but can it also restrict network access? For example, can I use it to restrict an application (like Firefox) to ONLY use a particular host and port (like a local proxy) for network access? [So, any plug-in attempting to circumvent the proxy would be blocked...]

Is this relatively easy to do within a profile, or does it require a lot of profile knowledge? [I'm definitely very new to this, and a little overwhelmed.]

Thanks much,
Gurtz

---

### Post by bodhi.zazen on 2010-09-02
> **Gurtz said:**
> Hi all,

Forgive this very rudimentary question. I know AppArmor can be used to lock down access to parts of the file system, but can it also restrict network access? For example, can I use it to restrict an application (like Firefox) to ONLY use a particular host and port (like a local proxy) for network access? [So, any plug-in attempting to circumvent the proxy would be blocked...]

Is this relatively easy to do within a profile, or does it require a lot of profile knowledge? [I'm definitely very new to this, and a little overwhelmed.]

Thanks much,
Gurtz

You are best off, IMO, using iptables.

See this post :

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

You may not use privoxy or dansguardian, but the iptables rules will point you in the right direction.

---

### Post by Gurtz on 2010-09-02
> **bodhi.zazen said:**
> You are best off, IMO, using iptables.


Thanks for the info! However, will this allow me to enforce a proxy on JUST Firefox? I wouldn't want to do so on the system as a whole. Since I was planning to enable an AppArmor profile for Firefox anyway, I figured I might be able to restrict network access using AppArmor, too.

Is this impossible ... or just particularly difficult? 

Thanks,
Gurtz

---

### Post by bodhi.zazen on 2010-09-02
> **Gurtz said:**
> Thanks for the info! However, will this allow me to enforce a proxy on JUST Firefox? I wouldn't want to do so on the system as a whole. Since I was planning to enable an AppArmor profile for Firefox anyway, I figured I might be able to restrict network access using AppArmor, too.

Is this impossible ... or just particularly difficult? 

Thanks,
Gurtz

I am not aware of any easy way to do what you want - restrict a single application to a port range . I do not think you can specify a port range or host name to connect to with apparmor and iptables is not application specific.

---

### Post by Gurtz on 2010-09-02
Oh, well it was worth asking. Thanks so much for the replies!

All the best,
Gurtz

---

### Post by BkkBonanza on 2010-09-03
You might look at iptables using the owner (uid,gui) as matching pattern. This wouldn't be for a program but could prevent certain users from accessing anything but a proxy.

There is --cmd-owner (for an application) as well but only if the kernel has that compiled in and I don't know if Ubuntu does. Probably not.

Edit: Further checking shows --cmd-owner was removed in 2.6.14 due to problems with SMP.

eg. this works,

iptables -A OUTPUT -m owner --uid-owner 0 -j ACCEPT
iptables -A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 8080 -j ACCEPT
iptables -A OUTPUT -j REJECT

Tested this with Firefox and regular users can only access web through proxy at localhost:8080. Of course, this affects the whole system and users not just Firefox.

One way to narrow this down would be to add a new group that is allowed more access and then add a rule for users who aren't in that group preventing them from doing anything but using the proxy. Or whatever variant of this works.

---

### Post by Gurtz on 2010-09-03
Thanks for all the research, BkkBonanza. I appreciate it!

Gurtz

---

### Post by bodhi.zazen on 2010-09-03
> **BkkBonaza said:**
> You might look at iptables using the owner (uid,gui) as matching pattern. This wouldn't be for a program but could prevent certain users from accessing anything but a proxy.

There is --cmd-owner (for an application) as well but only if the kernel has that compiled in and I don't know if Ubuntu does. Probably not.

Edit: Further checking shows --cmd-owner was removed in 2.6.14 due to problems with SMP.

eg. this works,

iptables -A OUTPUT -m owner --uid-owner 0 -j ACCEPT
iptables -A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 8080 -j ACCEPT
iptables -A OUTPUT -j REJECT

Tested this with Firefox and regular users can only access web through proxy at localhost:8080. Of course, this affects the whole system and users not just Firefox.

One way to narrow this down would be to add a new group that is allowed more access and then add a rule for users who aren't in that group preventing them from doing anything but using the proxy. Or whatever variant of this works.

Try:

```
iptables -t nat -A OUTPUT -p tcp --dport 80 - m owner ! --uid-owner proxy -j REDIRECT --to-port 8080
```

:twisted:

Change "proxy" to the owner of the proxy, it is privoxy with privoxy, I think proxy with polipo, just check with a simple ps aux

Of course keep the -m owner --uid-owner root -j ACCEPT ;)

---

### Post by BkkBonanza on 2010-09-03
Ah, yes. I see that would be smarter for typical use. I was interested in trying this because I use ssh as a SOCKS proxy and wanted to see if I could easily block traffic not through the proxy. With my rules it works for any protocol being routed thru ssh.

Well not entirely. I would need to add a udp rule. 

And now thinking about this it seems like it would be useful if there was an iptables module that could prefix any matching traffic with SOCKS commands that could be routed to an address/port.

---

### Post by Gurtz on 2010-09-03
You guys are so far out of my league, it's ridiculous :-)

But the info's great. Even though I can't claim to understand it all, it does give me some ideas to follow ... and I'm sure I'll learn a lot.

Thanks much,
Gurtz

---

### Post by bodhi.zazen on 2010-09-04
> **Gurtz said:**
> You guys are so far out of my league, it's ridiculous :-)


LOL !!!

Keep reading , you will learn ...

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

