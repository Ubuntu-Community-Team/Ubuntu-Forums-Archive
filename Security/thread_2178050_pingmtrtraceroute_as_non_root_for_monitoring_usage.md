---
title: "ping/mtr/traceroute as non root for monitoring usage"
date: 2013-10-01
forum: Security
---

### Post by zyHEpEJ on 2013-10-01
Hello,

I wanted to have a user for monitoring routings. I am using iptables mangle for this, for example for a proxy I use it this way (tcp instead of icmp):

[FONT=Verdana]iptables -t mangle -N TUNMARK[/FONT]
[FONT=Verdana]iptables -t mangle -A TUNMARK -j MARK --set-mark 2[/FONT]
[FONT=Verdana]iptables -t mangle -A TUNMARK -j CONNMARK --save-mark[/FONT]
[FONT=Verdana]iptables -t mangle -N RESTOREMARK[/FONT]
[FONT=Verdana]iptables -t mangle -A RESTOREMARK -j CONNMARK --restore-mark[/FONT]
[FONT=Verdana]iptables -t mangle -A OUTPUT -p [/FONT]icmp [FONT=Verdana]-m state --state NEW -m owner --uid-owner 1001 -j TUNMARK[/FONT]
[FONT=Verdana]iptables -t mangle -A OUTPUT -p [/FONT]icmp [FONT=Verdana]-m state --state ESTABLISHED,RELATED -m owner --uid-owner 1001 -j RESTOREMARK

Where 1001 is the uid of that user running the proxy (or in this case screen as non root, or logged in as non root).

The problem is, I cant use ping, mtr, traceroute and so on because they seem to need root, because of how they work (read it somewhere else already). They seem to need raw socket access or something like this, which just root can provide.

So I got the idea of using [/FONT][FONT=Verdana]--pid-owner instead, but it seems not be supported anymore? I read about it here: [/FONT][http://ubuntuforums.org/archive/index.php/t-1591433.html](http://ubuntuforums.org/archive/index.php/t-1591433.html)
[FONT=verdana]
So what do I do now? Is there any way in getting what I want to do? Is there maybe a better way and I am thinking it wrong? All I want is to use some monitoring tools like ping, traceroute, mtr, and they should be forced to go through the right gateway/vpn.[/FONT]

---

### Post by SeijiSensei on 2013-10-01
All users can run ping and traceroute.  If you want to force ping to use a particular interface, use the -I switch like this:

```
$ ping -I eth1 10.10.10.10
```

---

### Post by zyHEpEJ on 2013-10-01
> **SeijiSensei said:**
> All users can run ping and traceroute.

But just because it is running always as root. It doesnt helpt me of what I want to do, forcing the traffic of these programs through a specific mangle option.

---

### Post by SeijiSensei on 2013-10-03
> All I want is to use some monitoring tools like ping, traceroute, mtr, and they should be forced to go through the right gateway/vpn.

My point is that have them go through the right gateway, you simply need to select the appropriate interface for ping to use.  Say, for instance, you have an OpenVPN tunnel using the tun interface.  Then to send traffic that way, you would use "ping -I tun0 target".

---

### Post by SeijiSensei on 2013-10-03
> All I want is to use some monitoring tools like ping, traceroute, mtr, and they should be forced to go through the right gateway/vpn.

My point is that have them go through the right gateway, you simply need to select the appropriate interface for ping to use.  Say, for instance, you have an OpenVPN tunnel using the tun interface.  Then to send traffic that way, you would use "ping -I tun0 target".  Perhaps you have some other need for all that mangling, but you don't need it to ping via a specific connection.

---

