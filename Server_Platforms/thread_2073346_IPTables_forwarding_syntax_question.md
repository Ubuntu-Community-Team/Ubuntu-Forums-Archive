---
title: "IPTables forwarding syntax question"
date: 2012-10-19
forum: Server Platforms
---

### Post by jwright8 on 2012-10-19
I am trying to allow forwarding from a certain IP only outbound from 1024:65535.  I also want to allow any replies from these requests.  However, I don't want to allow any forwarding inbound that isn't solicited by the certain IP in question.  I tried the following rule:

```

iptables -A FORWARD -p tcp -s 10.1.10.72 --sport 1024:65535 -m state --state NEW,ESTABLISHED -j ACCEPT

```

However, when I set the DROP rule for forwarding after the line above, it still doesn't work.  For some reason, I can't use REJECT in the following line; it has to be DROP.  They essentially do the same thing I guess, so I wasn't too bothered about it.

```

iptables -P FORWARD DROP

```

Does anyone have any idea what I'm doing wrong here?  Thank you in advance for your help, as always!

---

### Post by darkod on 2012-10-19
I guess you have the POSTROUTING rule that you need for forwarding to work at all?
```
iptables -t nat -A POSTROUTING -o <ext interface> -j MASQUERADE
```

Otherwise the traffic can't be router back, which might be what is hapenning to you. Otherwise, that looks OK to me. I'm not sure if you can use NEW and ESTABLISHED with FORWARD, usually you would see that with the INPUT chain.

---

### Post by jwright8 on 2012-10-19
Actually I don't have a postrouting rule, which may be my problem.  I don't really understand too well what postrouting actually does, and I was kinda afraid to do anything that would make it behave in a way I didn't intend.

---

### Post by darkod on 2012-10-19
The MASQUERADE basically does the NAT function, replacing the internal private IP with the external public.

It doesn't matter whether this machine is actually directly on the internet or through another router, the principle is the same.

The traffic originating from your 10.1.10.72 machine has to be NAT-ed with the IP on the external interface because after it "goes out" from your router machine, the traffic can't go back using 10.1.10.72 since it's unknown on the outside.

The MASQUERADE does this function of replacing 10.1.10.72 with the external IP, and does the reverse process with the reply traffic so that it reaches back to 10.1.10.72.

You can try without any firewall as a test, you will see that you have no internet on 10.1.10.72 without the MASQUERADE.

---

### Post by jwright8 on 2012-10-19
Okay, that makes sense.  Thank you for the post.

Will enabling masquerading have any other effect on my firewall rulesets?  And should I put this before or after my default policies?

---

### Post by darkod on 2012-10-19
No, it has no effect on the firewall. It is required for the machine to be able to serve as a router at all.

There is also one more setting you need to change for forwarding traffic between the interfaces, not sure if you know it. In /etc/sysctl.conf you need to uncomment (remove the # symbol at the beginning) the line that says like:
/net/ipv4/ip_forward=1

With that line inactive, it doesn't forward packages between interfaces. So you have to activate the option.

I suggest you first make sure forwarding is working without any firewall, and only after that start to apply firewall rules. If you don't do that, you won't know whether traffic doesn't get forwarded because of the firewall or other settings.

---

### Post by jwright8 on 2012-10-19
Yeah, the ip forward was enabled and the forwarding works.  I'm not actually using the machine as a router, its more of a vpn server behind the router going directly into a switch.  The filtering and firewalling is more of an afterthought.

Thank you for all this though, just gotta play with it now and get it working like I want.  It's working now, but I don't like an ACCEPT rule for forwarding (for my purposes), no matter how heavily I filter it beforehand.

---

### Post by Doug S on 2012-10-19
To be able to set your default policy to DROP for the FORWARD path, you need to specifically provide a return path for the outgoing connection that you allowed and established:```
iptables -A FORWARD -i <external interface> -o <internal interface> -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

