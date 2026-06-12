---
title: "Ebox OpenVPN Problem: Can't access advertised network"
date: 2010-04-30
forum: Server Platforms
---

### Post by neocheema on 2010-04-30
Hi,

I've got this ebox machine working beautifully, except for  this niggle.

Here is the situation:

Internal Lan (  192.168.1.0/24 )  
                   |
   ( Internal ip  192.168.1.1)  (eth1)
        EBOX MACHINE 
   (External ip  202.194.xxx.xxx) (eth0)
                   |
             Internet
                    |
            Client Machine

Now I've setup  VPN as follows 

vpn port : 1124
vpn address : 192.168.160.0/24  
Advertized Network : 192.168.1.0 /24
Listening to Interface :  eth0

Ofcourse, Ebox is using OpenVpn for creating vpn. 

Now this is where I'm currently stuck. From my external  machine I can connect to the EBOX machine.

The client machine  gets a default IP of 192.168.160.3
I can ping EBOX at 192.168.160.1  and Infact connect to ebox administrative interface by doing 
[https://192.168.160]("https://192.168.160/").1

But  I'm unable to connect to any machine within the advertised network.  Ebox documentation says that I need to have reverse route from internal  lan machines. I tried adding a reverse routes, but it doesn't seem to  work. 

Moreover, with what ip addresses should I try to access my  internal lan machines. For ex. if an internal lan machine has address  192.168.1.20, what would be its VPN address?

Thanks for any  inputs.

---

### Post by spynappels on 2010-04-30
You will probably have problems with the setup you are describing from a few different angles.

Firstly, with a VPN setup in routing mode, you simply enter the LAN IP of the host you want on the internal LAN. When your client connects to the VPN, the VPN server will push a route to the client saying that to route to the LAN IP, the traffic has to go through the IP address of the VPN server.
Where you will have problems is that your LAN Subnet is 192.168.1.0/24. This is the same subnet enabled by default in very many routers, so when you are conn ected to a remote network which has the same subnet, i.e 192.168.1.0/24 and the VPN server pushes a route saying all 192.168.1.0/24 traffic is to be sent through its tunnel, you will get routing conflicts and a huge amount of grief. To combat this, you may need to alter your LAN subnet to something a little less common, such as 192.168.67.0/24 or something, which is unlikely to be used in a remote LAN you might be connecting from.

As for the original problem, you need to do 2 things.

1. Enable IP forwarding in the OpenVPN server.
To set it up to happen on boot, you can edit /etc/sysctl.conf and uncomment the line: 

```
#net.ipv4.conf.default.forwarding
```

You will also need to set a return route, so all traffic for the 192.168.160.0/24 subnet gets sent with the OpenVPN server as the gateway.

---

### Post by neocheema on 2010-04-30
Thanks a lot spynappels. Its finally making sense to me now. However it will take me a while before I can convert my network to a different number. Will let you know the results.
Cheers

---

### Post by ZAKhan on 2010-07-14
I am facing exactly the same problem .. I cannot access the servers in my local network.

has someone found a solution to this

---

