---
title: "Want to setup either tunnel or vpn server on my machine"
date: 2012-11-06
forum: Server Platforms
---

### Post by jasonto on 2012-11-06
I want to utilize my ubuntu machine to route my traffic through my home IP when I'm away from home.  I've looked into this and it seems I can either just set up a tunnel or a VPN (pptp probably).

Question 1:
What is your opinion on tunnel vs a full VPN?

If I setup a VPN I would want to restrict access to only routing traffic through the machine.  I would not want the user to have any kind of permissions to my internal network nor even the ubuntu machine (aside from what's necessary).  

Question 2:
Are there any guides available for accomplishing that?

---

### Post by sandyd on 2012-11-07
> **jasonto said:**
> I want to utilize my ubuntu machine to route my traffic through my home IP when I'm away from home.  I've looked into this and it seems I can either just set up a tunnel or a VPN (pptp probably).

Question 1:
What is your opinion on tunnel vs a full VPN?

If I setup a VPN I would want to restrict access to only routing traffic through the machine.  I would not want the user to have any kind of permissions to my internal network nor even the ubuntu machine (aside from what's necessary).  

Question 2:
Are there any guides available for accomplishing that?
I would reccomend using OpenVPN over PPTP - has higher performance

1.

When creating a VPN, you technically create a gateway server on the host computer. As a result, with some configurations, your network is accessable when using the VPN.

You can probably create a Iptables rule like
```

iptables -A OUTPUT  -p tcp -i [name of VPN Tunnel, i.e. tun0]  -d [home router ip] -j ALLOW
iptables -A OUTPUT  -p tcp -i [name of VPN Tunnel, i.e. tun0]  -d [your home subnet]/24 -j DROP
```
To block it.

2. I don't have time to search on the net right now, but most of the ones that you will find that use TUN, and not TAP will work well. Make sure it uses push "redirect-gateway def1" in the guide.

Note: You can also use SSH Tunneling, which would be much less complicated methinks

---

### Post by SeijiSensei on 2012-11-08
> **sandyd said:**
> I would reccomend using OpenVPN over PPTP - has higher performance

Not to mention that PPTP is known to be an [insecure protocol]("http://www.schneier.com/blog/archives/2012/08/breaking_micros.html").

---

### Post by jasonto on 2012-11-09
Thanks for the replies.  I know that PPTP is not absolutely secure, but I'm not too concerned about my one little VPN.  I'm going to try to connect my iOS devices so my only options are PPTP, IPSec, and L2TP - which of those would you suggest?

Also, I imagine I would just want to use an SSH tunnel were I to want to use a tunnel.  Are there any good guides on the net for setting one up?

Thanks again.

---

