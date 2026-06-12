---
title: "ipblock"
date: 2009-09-03
forum: Security
---

### Post by loosescrew on 2009-09-03
Hello, I'm new to ubuntu. I have installed host files from [http://www.mvps.org/winhelp2002/hosts.htm.]("http://www.mvps.org/winhelp2002/hosts.htm")
I have been browsing thru the forums and came across ipblock. My ?, is that basically the same as the host files or is it worth installing also. Thanks joe

---

### Post by lovinglinux on 2009-09-03
I never used host files, but as far as I understand, it only redirects outgoing connections. Iplist is an ip blocker, that uses one or more lists of known bad IP numbers and prevent your machine to connecting to them or them to your machine. It has the ability to filter traffic only on specific ports and is very flexible. 

Iplist is more like a firewall manager. In fact, what it does is to create iptables rules to diverge all traffic to a special chain, where it can check if the connection comes from a blocked IP or not, then drop or accept the connection accordingly. If accepted, it returns the packet to the regular iptables chains. 

[Mobock](http://moblock-deb.sourceforge.net/), which is another popular ip blocker, can also handle regular iptables rules, so you can use it as a firewall manager. That's what I do.

---

### Post by loosescrew on 2009-09-03
Thanks, lovinglinux. I appreciate you taking the time to explain. I went ahead and installed ipblock. I currently use gufw. But I will look into moblock. I'm still trying to figure out the firewall.I have gotten as far as denying all inbound packets. So that will have to be enough for now. Thanks again,Joe

---

