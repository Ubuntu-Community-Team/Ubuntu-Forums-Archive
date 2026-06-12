---
title: "Openswan is Driving Me Insane! - Port 1701 Open or Not?"
date: 2014-02-09
forum: Server Platforms
---

### Post by r1ckh on 2014-02-09
I have installed Open Swan on 12.04 (server) and finally got it working - this took a while! 

I have it configured for IPSec/L2TP using a PSK. The server is sat behind a router with a single public IP, so all ports have to be forwarded to the the internal server address. I have also enabled NAT-T in one of the conf files. In Ubuntu's firewall I believe, from what I have read, ports UDP 4500 and 500 need to be open and I believe port UDP 1701 needs to be open but only accept traffic from IPSec (I'm not sure if this right or wrong), these are the commands I have used to configure the firewall:

sudo ufw allow proto udp from any to any port 500
sudo ufw allow proto udp from any to any port 4500
in /etc/ufw/before.rules
-A ufw-before-input -m policy --dir in --pol ipsec -p udp --dport 1701 -j ACCEPT

Logic would suggest that I only need to forward ports 4500 and 500 on my router to the internal address. But if I don't forward 1701, my built in Windows and iPhone VPN clients wont connect, so I have forwarded 1701 to make it work. 
However, I have read that port 1701 should not be exposed in this way, as it is used by L2TP and it is normally encapsulated in IPSec therefore is only used internally. What I don't get is most servers would be in a DMZ and that port would be exposed in the same way as me forwarding it?
I have also read that the Windows VPN client will not touch port 1701 when using the IPSec/L2TP option, which confuses matters further as it wont work if this port is not forwarded on my router!

So my question is, port 1701, to be or not to be....... forwarded?

If not, can anyone tell me what may be wrong with my Openswan setup?

Thanks,

Rick

---

