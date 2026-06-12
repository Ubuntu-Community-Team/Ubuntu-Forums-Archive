---
title: "Help with setting up QOS for bittorrent and other P2P protocols"
date: 2011-03-02
forum: Server Platforms
---

### Post by Nessaja on 2011-03-02
Hi,

I'm using Ubuntu Server 10.04 for our office proxy.

I have a problem with some users using bittorrent programs, this usually uses up all the available bandwidth and causes slow response.

Blocking torrents and P2P won't help because there's always a way to get around it.

What I want to do is to throttle Bittorrent and P2P protocols to 10kbps or slower to make them think torrents still works, but have it use almost no bandwidth. I think the best way to do this is with QOS.
Can anybody please help me with setting up QOS for this cause?

---

### Post by aeiah on 2011-03-02
since this is an office environment, why dont you just block all ports except ssh, ftp, email and http(s)?

limiting P2P to 10kb/s is throttling, incidentally, not QoS, although QoS will probably provide a nicer experience for all if you still wish to enable people to use the office resources for file sharing.

QoS and the like can be done with iptables, but perhaps look at wondershaper, as it may make things simpler.

---

### Post by Nessaja on 2011-03-07
Hi,

Thanks for the reply.

We we do not want employees to use P2P at all, but I've found that, if I block all the ports, the P2P software simply starts using port 80. 

That's why I want to limit it to a speed so slow, that it's not worth downloading stuff at the office. So when it's limited, the p2p software will continue to use it's usual random ports, but will have almost no bandwidth.

If iptables can block p2p protocols on any port (even port 80), I'll rather use that ofcourse

---

### Post by BkkBonanza on 2011-03-07
That doesn't make much sense as the torrent client can't use port 80 if other clients are offering content on other ports. It could decide to listen on port 80 but that won't work without port forwarding anyway. 

My guess is this is being manually worked around and that some user has configured a tunnel out port 80 and has the torrent client go through that (which is how I do it when I need to). If that's the case then you won't be able to limit that way because when that user sees the low bandwidth you intend they'll just do the same again.

Assuming this is on a linux router/gateway/firewall then I'd use the **netstat-nat** tool to show the NAT table and determine which machine is tunnelling thru port 80 (or even for that matter doing any torrent activity) and either block or limit them specifically or give them a piece of your mind. 

That tool will show you all the active connections thru your router - each src IP and dest IP so you should be able to see right away which machine has hundreds of (high port) connections active. Iptables can be used to limit/block specific traffic and do more general controls too. It can also be used to view how much data has passed thru specific ports/IPs but it's a bit cumbersome for that.

Also, your proxy software should have some kind of status info that shows you active connections or traffic. 

If a user is tunnelling then typically they will tunnel out to some consistent outside server - which could be simply blocked.

---

### Post by Nessaja on 2011-03-15
Thank you very much for the information.

Using netstat I was able to track the person down and block all internet activity.

When he eventually reported his internet not working, I told him that it was blocked due to abuse and that further abuse could cause a written warning...

I'll continue to monitor the traffic to see if there's more people that's using this technique...

---

