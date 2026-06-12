---
title: "Reject vs Drop for Outbound Traffic"
date: 2011-04-15
forum: Security
---

### Post by nrundy on 2011-04-15
I understand the difference between Reject vs Drop for incoming traffic, but are there any differences between reject and drop for Outbound Traffic? Are there reasons to pick one over the other or are they functionally identical when talking about Outbound traffic?

---

### Post by bodhi.zazen on 2011-04-15
In Linux there is much less of a need, if any at all, to filter outbound traffic ;)

I will sometimes filter traffic to servers on my LAN. For example if I am running a public web server from my LAN I will sometimes filter non-http traffic from the server to other boxes on the LAN.

If you do, Reject is going to give you better performance. If yo use drop your client will make multiple attempts to make a tcp connection and take longer to time out.

---

### Post by nrundy on 2011-04-17
> **bodhi.zazen said:**
> In Linux there is much less of a need, if any at all, to filter outbound traffic ;)


I disagree. 

Off the top of my head, here are some things I use Outbound filtering for:

1.) to enforce that DNS lookups only go to the IP address that I want them to go to. I use a DNS provider that provides filtering services so that I don't have to worry as much about what sites my kids are accessing. This also is a defensive layer against DNS spoofing.

2.) It allows me to control my bandwidth usage, which is helpful when bandwidth caps are in place from my ISP. This would be more controllable though if I could filter based on application and not just port and IP address.

3.) It allows me to enforce that my email client is only operating on SSL channels. I can guard against accidental setting changes within the email client itself as well as unintended changes resulting from my kids and less experienced computer users like my parents.

4.) It also keeps me aware of what applications and processes are accessing the internet. I gain a better understanding of what applications need internet access. This would be a lot easier if filtering was done via application but it still is instructive with just port and IP.

5.) Outbound filtering can also be a good mechanism for learning what applications unnecessarily make outbound connections. It assists me in picking what applications and software I prefer to use. Those that make a lot of outgoing connections unnecessarily I choose not to use.

6.) It allows me to block ports that I never use. Ports that are commonly exploited or used to relay information to Command and Control Servers for example. If I never use the ports to begin with, it causes no disruption to my computer use whatsoever But it does provide additional security to some extent.

---

### Post by dfreer on 2011-04-17
I recently competed in the national collegiate cyber defense competition (we didn't win :( ), and ingress/egress firewall rules were pretty much mandatory on my linux boxes. If they managed to grab a foothold on my machine, they would have to spend time defeating my outbound firewall to remote back into their staged machines for scripts, tools, pedobear images (I'm not even lying, the hacking team is funny that way). Not that it would be particularly hard to compromise the firewall once they got in, but that's additional time for me to stop them.

In short, every little bit helps. Obviously this is a special case, and I tend to agree for home users there isn't much need for an egress-based firewall, but it's useful to know and good practice.

---

### Post by bodhi.zazen on 2011-04-17
Both of those are rather specialized examples.

In the first you are trying to increase privacy and IMO iptables is of fairly limited use and, as you point out, most of the configuration is with the clients, not iptables.

In the second you are discussing a highly specialized environment. As you point out, in this case iptables slowed people down but did not really prevent them from their ultimate goal.

Most desktop users, and in fact most Linux users, do not need outbound rules and in both case your iptables rules are either secondary (to properly configured clients) or ineffective. 

So while filtering outbound traffic has some utility in very specialized environments, I would not over sell those examples as somehow necessary for the vast majority of people.

Last, if you read the first post, neither of you answered the original question ;)

---

### Post by dfreer on 2011-04-17
To be fair, I pretty much said the same thing that it isn't really needed for home users, and felt you had covered the original question, so I was responding to the new topic of whether egress firewalls are useful.

Carry on :D

---

### Post by SeijiSensei on 2011-04-18
I've blocked high-port to high-port connections on some egress firewalls:

```
iptables -A OUTPUT -j REJECT -p tcp --sport 1024:65535 --dport 1024:65535
```

Most clients shouldn't be communicating with remote high ports except in very specialized cases.  Legitimate requests usually originate from a source high port to a target port in the restricted range of 0-1023.

---

