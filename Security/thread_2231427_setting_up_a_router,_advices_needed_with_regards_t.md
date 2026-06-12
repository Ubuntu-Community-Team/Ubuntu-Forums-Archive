---
title: "setting up a router, advices needed with regards to security"
date: 2014-06-25
forum: Security
---

### Post by clearski on 2014-06-25
Hello, everyone.

I am going to replace my ISR soon. The new router at the edge of my LAN will be a host running Ubuntu 14.04 server. The WAN face of the router will not offer any services, that is all ports will be closed to absolutely any type of requests from outside. It will provide routing to WAN, DHCP and SSH services to some internal hosts, since it's a headless machine. It will also act as a firewall.

My question is: what are the important points - with regards to the security of this host - that should be taken into consideration? Please state anything that comes into your mind. To me, because services to WAN are disabled, it seems that the firewall setup & filtering is the most important piece that I should take care of. But I might not see other things, that's why I'd like to hear your opinions, based on your experience.

Thanks!

---

### Post by ian-weisser on 2014-06-25
I usually recommend against running server-services and router-services on the same system if you value your connectivity. It creates a single-point-of-failure: An unreliable service or disk problem could crash your whole network. (Happened to me)

In the past, when I put router and server on the same system, I minimized the number of services that listen. Look for listening services using netstat -tulpn.

Get to know IPtables really well, so your firewall does exactly what you want. UFW and other helpers are nice, but it's worth the time to learn the proper tool for your complex job. I used a well-documented iptables script that ran each time an interface came up.

Get the router working securely first before adding other services. Each time you add a new service, check top and free and netstat to ensure it's not a CPU or memory or port hog.

Oh, and thoroughly document how you installed each service, the permissions you grant to each user, the manual changes to made to iptables and/or port assignments and /etc files. If you uninstall a service or terminate a user, you don't want to leave holes.

---

### Post by clearski on 2014-06-26
Hi, Ian!

Thank you for your answer.

> **ian-weisser said:**
> I usually recommend against running server-services and router-services on the same system if you value your connectivity. It creates a single-point-of-failure: An unreliable service or disk problem could crash your whole network. (Happened to me)

I not a fan keeping all the eggs into the same nest, too, but I've only have two hosts here, besides the VMs I'm using to test different configurations. One of the real hosts is down most of the time. Using static IP addresses is what I do now. But sometimes, if a guest needs Internet access, DHCP provides an easy way to direct him to a different subnet and automatically assign an address. I definitely can do it without the DHCP service enabled, but I just wanted to make sure that I can install and configure this service if needed and to me it looks kinda new and fun.

> **ian-weisser said:**
> Get to know IPtables really well, so your firewall does exactly what you want. UFW and other helpers are nice, but it's worth the time to learn the proper tool for your complex job. I used a well-documented iptables script that ran each time an interface came up.

You said exactly what I was thinking. Michael Rash's book is arriving soon and I'll definitely use it for the setup.

> **ian-weisser said:**
> Oh, and thoroughly document how you installed each service, the permissions you grant to each user, the manual changes to made to iptables and/or port assignments and /etc files. If you uninstall a service or terminate a user, you don't want to leave holes.

Well, there'll be only one user account on the router, I don't see any reason for multiple accounts. This user will administer the router.

I've started to harden the operating system and the services on this host. I am keeping a detailed log of everything I do, so I can come back anytime and see what I've done if needed. This is a great idea. Actually, what I'm doing now should be done on any host as standard procedures. When everything is in place, I'll eventually post these somewhere, because this is a compilation from multiple sources.

And now I have another question. I was reading about advanced ssh server configurations and one of the things which could be done was to run sshd from (x)inetd. The setup looks simple, but should I bother with this or now? Is running from inetd more secure? One of the things I like at this is that I can setup time access tables, for example. But I'm not sure if I have to do this now, I think the ssh service is configured pretty well now, it is not a danger itself.

---

### Post by HermanAB on 2014-06-28
Note that xinetd is obsolete.

If you want to make ssh secure, set it to use keys only and disable passwords.

---

### Post by clearski on 2014-06-29
> **HermanAB said:**
> Note that xinetd is obsolete.

If you want to make ssh secure, set it to use keys only and disable passwords.

I cooled down a little bit, I think ssh is pretty secure in my case. I'm using public keys authentication everywhere with the keys stored in encrypted directories on each host (end devices only). I am also using tcp wrappers (deny hosts), different listening port numbers and IP and port filtering on firewall (ufw for now and iptables soon). I tried to setup two factor authentication using google authenticator and PAM, but it seems that it doesn't work when using public keys. But it was nice trying. :)

Thank you for your input!

---

### Post by gordintoronto on 2014-06-29
Have you looked at pfSense?

---

### Post by clearski on 2014-06-30
> **gordintoronto said:**
> Have you looked at pfSense?

I'm sorry for the late answer.

I have to say that it's the first time when pfSense came to my ears. Right now I am more interested in having less than pfSense offers, because I want to do things by myself, see how they work (or not). :) pfSense does almost everything by itself. A hardcopy of Linux Firewalls is on the way and in two weeks I'll start with IP Tables, psad and fwsnort. This project is not only about having a router/fw up and running, I already have IP tables scripts and some updated rules for NAT wouldn't be a very complicated task, but it's more about seeing and makings things work with my own hands. I have to take the narrow path for now. Anyway, thank you for your suggestion. :)

---

### Post by clearski on 2014-07-11
I am trying to insert some load connection-tracking module statements into a IP tables script.

```
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
```

I checked to see if both modules are available:

```
user@host:~/Desktop$ modprobe -c | grep ip_conn
alias ip_conntrack nf_conntrack_ipv4

```

*ip_conntrack* is available and can be loaded, but *iptable_nat* can't be found.

Any suggestions? I am on a desktop edition now, is it possible that it doesn't have the *iptable_nat* module? Does it mean that IP tables cannot use a nat table?

update: the server version returns the same results.

---

