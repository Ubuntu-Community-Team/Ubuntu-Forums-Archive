---
title: "Firewall recommendations"
date: 2015-02-09
forum: Security
---

### Post by zoomiest2 on 2015-02-09
I looking for a solid firewall that will allow me to block "all websites" except for a list. I just went through a variety of attempts with ClearOS, and couldn't get it right (was also wrecked by the power management wrecking the screen after 5 minutes, so I am happy to go for a GUI-less firewall.

Why didn't it work? I had:
eth0: dhcp (range was 192.168.0.x)
eth1: static 192.168.1.2 (when the Linksys wifi router was 192.168.1.1)

My set up was: 

PROVIDER > cable modem > ClearOS box 6.5 (community)> Linksys router with wifi 
(Looks okay to me, but I couldn't get traffic through it).

PROBLEM: 
I have looked at a number of the "firewalls" imbedded in devices and found that none have the ability to block all traffic except an exception list. 

QUESTION:
Do you recommend any linux firewalls that will allow blocking all traffic except an easily edited exception list?

---

### Post by TheFu on 2015-02-09
First, there is only 1 firewall for Linux - iptables. All "firewalls" are just interfaces over iptables - ufw, gufw, etc ... just manage iptables.

Soon-ish, the linux firewall will be swapped out with a replacement that merges about 4-6 commands into a single tool. Don't know exactly when this will end up in Debian/Ubuntu releases.

I think you really don't want to use a firewall for this, rather using a proxy server like squid which is designed for this might be better.  Firewalls work on IPs and subnets. They aren't designed to work on domainnames since the DNS to IP mapping can change minute by minute.

It may be easier to work with a release like DansGuadian to get what you want working.

Also - the internet isn't just web traffic. If you don't control all the traffic, then smart people WILL FIND AWAY AROUND your protections.  It is best to not allow desktops to have access to either a default route or to external DNS at all. Force them to use the proxy server to get outside.  If you need a transparent proxy, which might be what you want, there are how-to guides for that.

Another way to solve this is to disable DNS on all the client machines and manage the /etc/hosts file with the domainnames you want white listed. For small children, this could be sufficient.  If there are more than a few machines involved, using something like ansible to manage the hosts files would be relatively easy.

I hope this is helpful for whatever the end goal is.  There must be a few other ways to accomplish this as well.

---

### Post by zoomiest2 on 2015-02-09
TheFu, *much* appreciated. DansGuardian sounds like a great path. 
Goal: This is to keep an 18 year old son from a pornographic addiction. Its very debilitating to him... can't finish high school, etc. We blocked the Internet and after a few weeks, we started to see our son again... very eerie.

BTW, I started using the HOSTS file, but I want to block wifi too, so I thought I would go at the source. Proxy management might be a better approach.

You mentioned that there were other ways to do this? I am willing to consider any ideas, at this point. I have started looking at IPCop... seemed to be running squid.

---

### Post by MrSteve on 2015-02-09
have a look at openDNS
it is a free dns service with the ability to block sites and is very easy to setup
also it is managed off site ...

---

### Post by sandyd on 2015-02-09
> **MrSteve said:**
> have a look at openDNS
it is a free dns service with the ability to block sites and is very easy to setup
also it is managed off site ...

OpenDNS only blocks when you have forced the firewall to reject any connections to any DNS server other than its own.

> **zoomiest2 said:**
> TheFu, *much* appreciated. DansGuardian sounds like a great path. 
Goal: This is to keep an 18 year old son from a pornographic addiction. Its very debilitating to him... can't finish high school, etc. We blocked the Internet and after a few weeks, we started to see our son again... very eerie.

BTW, I started using the HOSTS file, but I want to block wifi too, so I thought I would go at the source. Proxy management might be a better approach.

You mentioned that there were other ways to do this? I am willing to consider any ideas, at this point. I have started looking at IPCop... seemed to be running squid.

Some tips, depending on your son's tech-savvy-ness
Make sure all traffic other than the regular stuff, (https, http, SMTP, SMTPS/etc) is blocked. There are still multiple issues not fixed by this, mainly for the fact that stunnel and openvpn can be used over http/https. DNS should be restricted so that the clients can only connect to the gateway, nothing else. There are ways to setup a VPN over DNS

If you want https with squid (without letting your son remove the proxy), you will have to install a SSL certificate on his computer so that the computer stops thinking there are Man In the Middle Attacks going on.

Do not know if Squid will actually enable stunnel/openvpn to continue connecting or not.

---

