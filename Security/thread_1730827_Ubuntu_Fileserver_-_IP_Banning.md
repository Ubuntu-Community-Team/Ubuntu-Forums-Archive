---
title: "Ubuntu Fileserver - IP Banning"
date: 2011-04-16
forum: Security
---

### Post by Jimbo8098 on 2011-04-16
Hi all!

Im looking to step up security for a variety of tasks that i use my server for , one of which is my fileserver. Im interested in finsing out how to:

1) block all ips not on my home LAN (wired and wireless)
2) block single ips when the server is open to internet. 
3) block all ips BUT certain ips 

Any ideas?

---

### Post by dfreer on 2011-04-17
(1). This iptables command *technically* does block all IP's not on your local LAN.
```
## Drops all incoming connections NOT from the local LAN
iptables -A INPUT -i **eth0** ! -s **192.168.1.0/24** -j DROP
```
Replace the interface name and network address as needed of course. But since all traffic coming in from the internet is likely coming from your router (which is on the local LAN), this won't help much. The router firewall would be a better place to stop this. Actually, a better idea would be to block the router's internal LAN IP, just for the services you don't want accessible from the internet. You could, of course, do a combination of the two.

(2). This should also block single IP addresses, just make sure they are at the top of your rule list.
```
iptables -A input -s 10.0.0.8 -j DROP
```

(3). As for block all IPS but a certain IP, I'm pretty sure this is what you would need, example for SSH:
```
## SSH IN, for only one IP address, using states (if you don't want to use stateful firewall, take out the **bolded** part
iptables -A INPUT -i eth0 -s 172.168.20.1 -p tcp --dport 22 **--syn -m state --state NEW** -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 22 -j DROP
```

In short, iptables is a pretty awesome firewall, and if your server is open to the internet you should already be using it. I like ipf on freebsd too, not sure which I like better.

---

### Post by bodhi.zazen on 2011-04-18
You can also use tcpwrapper (hosts.allow / hosts.deny).

What protocol are you using to share files ?

---

