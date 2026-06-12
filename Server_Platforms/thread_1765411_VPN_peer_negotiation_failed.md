---
title: "VPN peer negotiation failed"
date: 2011-05-23
forum: Server Platforms
---

### Post by tapi0n on 2011-05-23
I've followed [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) to set up vpns with some external networks. So far it worked like a charm on two of them. But when trying to connect to the third one I instantly get bumped off.

When running 
```

pon dymka debug dump logfd 2 nodetach
```I get this as part of my output 

```
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x26 <addr 192.168.0.2> <compress VJ 0f 00>]
sent [IPCP TermAck id=0x26]
rcvd [CCP ConfReq id=0x3e <mppe -H -M +S -L -D -C>]
Refusing MPPE stateful mode offered by peer
MPPE required but peer negotiation failed
sent [LCP TermReq id=0x2 "MPPE required but peer negotiation failed"]
sent [CCP ConfRej id=0x3e <mppe -H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe -H -M +S -L -D -C>]
Discarded non-LCP packet when LCP not open
rcvd [LCP TermAck id=0x66]
Connection terminated.
Waiting for 1 child processes...
  script pptp xxx.xxx.xxx.xxx--nolaunchpppd, pid 8920
Script pptp xxx.xxx.xxx.xxx --nolaunchpppd finished (pid 8920), status = 0x0
```
I've looked all over the internet but sollutions like adding mmpe-stateful to options.pptp doesn't work.

Is this a problem with the client or with the server? Because the server is configured just like the other two and they work as intended.

Edit: Seemed to be a problem on the firewall :)

---

### Post by brettg on 2011-05-23
I've written an fully interactive client for building PPP over SSH vpns. It takes 5 minutes to setup and I would appreciate some feedback. 

The server part is as simple as setting up a user account, using visudo to give the user rights to use the pppd and route commands and create a one line file where the active_routes list will be kept.

The client side is all automatic, for the first node all you need is the FQDN of the VPN server and then it configures the rest for you, including creation and transfer of ssh keys for passwordless operation. Subsequent nodes differ only in that they need to know what IP address's to use for the P2P link. I'm thinking of automating that too. 

Routes between all sites/nodes are automatically configured so that all sites can ping each other (This is updated live to by adding the "vpn check" command as a cron job) 

It's as simple as downloading the script and entering ./vpn setup

After that you can use vpn [start|stop|check|status] to manage it.

I've only just finished it in the last couple of days. If you are interested in trying it I'd really appreciate any feed back you have.

Cheers

Brett

[Five Minute VPN setup]("http://tuxnetworks.blogspot.com/2011/05/howto-easiest-vpn-setup-ever.html")

---

### Post by tapi0n on 2011-05-23
Hey brett,

I'm doing this project as part of my internship (for school). And my mentor is pretty set on using this method. 

However. I do plan on setting up a server at home this July. If you still need input at that point I'd be happy to try it :)

---

### Post by brettg on 2011-05-23
No worries mate, good luck with your project. 

Input is always welcome of course, better late than never!

---

