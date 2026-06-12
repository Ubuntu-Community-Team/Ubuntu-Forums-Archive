---
title: "pptp vpn issues with mac"
date: 2013-02-05
forum: Server Platforms
---

### Post by sbdcunha on 2013-02-05
I had recenetly setup a pptp vpn server on centos 5.8 ..
every thing is working fine. i can coonect perfect ok from a windows machine and works great

but one vpn user has a mac notebook

MacBook Pro os is X lion 10.7.5

it connects fine but I cannot do a RDP to a windows 7 machine

But if this win7 machine is given a public ip I can remote desktop from the same mac notebook  to the ip and it works fine

my error logs show

------------------

pppd 2.4.4 started by root, uid 0
Feb  4 13:32:56 kmchat pppd[14979]: Using interface ppp0
Feb  4 13:32:56 kmchat pppd[14979]: Connect: ppp0 <--> /dev/pts/1
Feb  4 13:32:59 kmchat pppd[14979]: MPPE 128-bit stateless compression enabled
Feb  4 13:32:59 kmchat pppd[14979]: Unsupported protocol 'IPv6 Control Protovol' (0x8057) received
Feb  4 13:32:59 kmchat pppd[14979]: Unsupported protocol 'Apple Client Server Protocol Control' (0x8235) received
Feb  4 13:32:59 kmchat pppd[14979]: found interface eth0 for proxy arp
Feb  4 13:32:59 kmchat pppd[14979]: local  IP address 192.168.30.3
Feb  4 13:32:59 kmchat pppd[14979]: remote IP address 192.168.30.210
Feb  4 13:32:59 kmchat pppd[14979]: pptpd-logwtmp.so ip-up ppp0 tariq 178.61.182.177
Feb  4 13:34:54 kmchat pptpd[15003]: CTRL: Client 178.61.182.179 control connection started
Feb  4 13:34:54 kmchat pptpd[15003]: CTRL: Starting call (launching pppd, opening GRE)
Feb  4 13:34:54 kmchat pppd[15004]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Feb  4 13:34:54 kmchat pppd[15004]: pptpd-logwtmp: $Version$
Feb  4 13:34:54 kmchat pppd[15004]: pppd 2.4.4 started by root, uid 0
Feb  4 13:34:54 kmchat pppd[15004]: Using interface ppp1
Feb  4 13:34:54 kmchat pppd[15004]: Connect: ppp1 <--> /dev/pts/2
Feb  4 13:34:54 kmchat pptpd[15003]: CTRL: Ignored a SET LINK INFO packet with real ACCMs!
Feb  4 13:34:54 kmchat pppd[15004]: Unsupported protocol 'IPv6 Control Protovol' (0x8057) received
Feb  4 13:34:54 kmchat pppd[15004]: MPPE 128-bit stateless compression enabled
Feb  4 13:34:56 kmchat pppd[15004]: found interface eth0 for proxy arp
Feb  4 13:34:56 kmchat pppd[15004]: local  IP address 192.168.30.3
Feb  4 13:34:56 kmchat pppd[15004]: remote IP address 192.168.30.211
Feb  4 13:34:56 kmchat pppd[15004]: pptpd-logwtmp.so ip-up ppp1 tariq 178.61.182.177
Feb  4 13:42:49 kmchat pppd[14979]: LCP terminated by peer (MPPE disabled)
Feb  4 13:42:49 kmchat pppd[14979]: pptpd-logwtmp.so ip-down ppp0
Feb  4 13:42:49 kmchat pppd[14979]: Connect time 9.9 minutes.
Feb  4 13:42:49 kmchat pppd[14979]: Sent 354 bytes, received 3900 bytes.
Feb  4 13:42:49 kmchat pptpd[14978]: CTRL: EOF or bad error reading ctrl packet length.
Feb  4 13:42:49 kmchat pptpd[14978]: CTRL: couldn't read packet header (exit)
Feb  4 13:42:49 kmchat pptpd[14978]: CTRL: CTRL read failed
Feb  4 13:42:49 kmchat pppd[14979]: Modem hangup
--------------
Is there any specific setting i need to do on the mac or on server

apprecite your kind help and advise


regards


simon

---

### Post by sbdcunha on 2013-02-07
Dear All,

I did a little investigations since i just had the look at the mac notebook today ( actually its a personal notebook of my manager) .

then i found that i was not able to ping my default gateway.
then i realized that windows VPN connection has a option... use default gateway on the remote network.
 how can i achieve the same in the mac notebook ---   MacBook Pro os is X lion 10.7.5


apprecite your help

regards

simon

---

