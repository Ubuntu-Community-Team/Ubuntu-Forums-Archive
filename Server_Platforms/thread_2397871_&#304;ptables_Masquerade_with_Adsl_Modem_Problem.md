---
title: "&#304;ptables Masquerade with Adsl Modem Problem"
date: 2018-08-04
forum: Server Platforms
---

### Post by secooonder on 2018-08-04
Hello 
i setup Ubuntu 16.04 LTS.i configured iptables.
Network schema has become like this:

Local Network-------> (    eth0)---->Firewall --->(eth1) ------->ADSL Modem.
(192.168.25.0/24)    (192.168.25.1)         (192.168.1.1)           (192.168.1.2)

Shortly;
> Local Network         :192.168.25.0/24
Firewall inbound ip  :192.168.25.1
Firewall outbound ip:192.168.1.1
Adsl Modem           : 192.168.1.2

i added > [COLOR=#242729][FONT=Consolas]echo "1" > /proc/sys/net/ipv4/ip_forward
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf[/FONT][/COLOR] 

Firstly,No rules on firewall

Question 1:

i can not ping 8.8.8.8 from Local Network.When i added  > [COLOR=#111111][FONT=Consolas]iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]  rule, i can ping 8.8.8.8
[/FONT][/COLOR]
But , Nat rule is open at Adsl Modem ? Adsl Modem came with factory settings?When both modem and Firewall nat work ,is firewall  confused ? is this operation safely?

Question 2:
Yesterday,i set up a trial firewall.Firewall has a only one interface.&#304; configured firewall.
Adsl Modem ,Firewall and Local Network connected one Switch(24 Port) 
Local Network 192.168.25.0/24 
Firewall 192.168.25.1
Adsl modem 192.168.25.2

i gave 192.168.25.1 to  gateway addresses of client computers. The firewall is running.

Which configuration is safely?

---

### Post by darkod on 2018-08-04
The masquerade rule is necessary so that your ubuntu server firewall can correctly nat traffic between the two networks. It is not confused, it is normal operation.
If your adsl modem/router has a built in firewall (they normally do), then it is enough for protecting your lan network. Don't need to complicate it by adding one more firewall especially if you are not experienced managing them.

---

### Post by The Cog on 2018-08-04
The reason that (in Q1) yuou could not ping 8.8.8.8 until you turned masquerade on is very probably that the adsl router did not know how to send the reply from 8.8.8.8 back to network 192.168.25.*. You woud have to add a static route into the ADSL router to tell it to forward traffic for 192.168.25.0/24 via 192.168.1.1 and I am guessing that you missed that step. With your firewall performing NAT, the adsl router only had to return the reply to the firewall's address on 192.168.1.1.

I agree with darkod that you probably don't really need a firewall inside, because the adsl router is performing NAT and that has much the same effect as a firewall, blocking all incoming connections (because it doesn't know which internal address to NAT the incoming connection to). I know your ADSL "modem" is doing NAT because networks starting with 192.168 are not reachable from the internet, they are reserved for private use.

---

### Post by secooonder on 2018-08-05
darkod and the cog thank you.
The cog,as you said ,when i add route to modem(return 25.0),the problem is solved.

Darkod and the cog,
i  want to setup iptables firewall,Because it is very useful.i setup squid,suricata(For deep package inspection)  etc..

i want to ask you.
Scenario 1:
Firewall has a two interfaces.
> 
[COLOR=#000000]*Local Network :192.168.25.0/24*[/COLOR]
[COLOR=#000000]*Firewall inbound ip :192.168.25.1*[/COLOR]
[COLOR=#000000]*Firewall outbound ip:192.168.1.1*[/COLOR]
[COLOR=#000000]*Adsl Modem : 192.168.1.2 *[/COLOR][COLOR=#000000][I]
And i add "[/I][/COLOR][COLOR=#111111][FONT=Consolas][I]iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE"
[/I][/FONT][/COLOR]

[COLOR=#000000][I]Scenairo 2:
[/I][/COLOR]Firewall has a two interfaces.
> 
[COLOR=#000000]*Local Network :192.168.25.0/24*[/COLOR]
[COLOR=#000000]*Firewall inbound ip :192.168.25.1*[/COLOR]
[COLOR=#000000]*Firewall outbound ip:192.168.1.1*[/COLOR]
[COLOR=#000000]*Adsl Modem : 192.168.1.2 *[/COLOR]
[COLOR=#000000]*And** i am _not_ add** "*[/COLOR][COLOR=#111111][FONT=Consolas][I]iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE"
Therefore [/I][/FONT][/COLOR] i add route to modem(return 25.0).

[COLOR=#111111][FONT=Consolas][I]Scenairo 3:

Firewall  has a one interfaces.
> [/I][/FONT][/COLOR][COLOR=#000000]Adsl Modem ,Firewall and Local Network connected one Switch(24 Port) [/COLOR]
[COLOR=#000000]Local Network 192.168.25.0/24 [/COLOR]
[COLOR=#000000]Firewall 192.168.25.1[/COLOR]
[COLOR=#000000]Adsl modem 192.168.25.2[/COLOR][COLOR=#111111][FONT=Consolas][I]
[/I][/FONT][/COLOR][COLOR=#000000][I]
i tested three scenairos,all works.
Which scenario is safely or fastly?

What would you choose if you were ?

[/I][/COLOR]
[COLOR=#000000][I]




[/I][/COLOR]

---

### Post by darkod on 2018-08-05
If you decide to keep the firewall, I like scenario 1 best. It is the firewall that is doing the routing between networks 25.0 and 1.0 so the masquerade rule should be there.

---

### Post by The Cog on 2018-08-05
If all your web access is going via squid, then you can probably use scenario 1 but with two changes:
* You don't need MASQUERADE, as the clients only talk to squid, and only squid talks to the internet
* You don't need to enable ip forwarding, for the same reason.

---

### Post by secooonder on 2018-08-05
The Cog and Dargod
i setup Firewall according to scenario 1

Thank you very much for your help

---

