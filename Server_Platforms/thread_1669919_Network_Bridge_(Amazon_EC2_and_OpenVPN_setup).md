---
title: "Network Bridge (Amazon EC2 and OpenVPN setup)"
date: 2011-01-18
forum: Server Platforms
---

### Post by AndyWD on 2011-01-18
Hi there
My aim is to set up a openVPN server in an amzon ec2 instance (ubuntu 10.04 server) to have access to the internet 

I have tested setting up a VPN on my home server and would like to do so on Amazon EC2 but I am unsure of how to configure the network settings (and creating the bridge interface using bridge utils) as all the various guide I read rely on the server having a static IP address. As far as I understand every time you start an instance it is assigned a new ip address? I don't really want to keep it running constantly as i will only be using it occasionally!

As well as creating the bridge interface I am unsure how to edit the server.conf file (as i presume they rely on satic ip adresses) where it says :
"local a.b.c.d" 
"server-bridge a.b.c.d 255.255.255.0 a.b.c.e  a.b.c.f"

Also would the computer connecting be assigned an address by the amazon ec2 dhcp (or whatever they use) and would it work?

Does a bridge interface need to be created if i just need internet access?

Currently using the guide
[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

Many thanks!!! :-)

---

### Post by mixersoft on 2011-10-18
I'm using the same guide, but running into an EC2 problem -- 
I configure the bridge using this guide ([https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging)) and the following params:

```

auto br0
iface br0 inet static
        address 10.8.0.10
        network 10.8.0.0
        netmask 255.255.255.0
        broadcast 10.8.0.255
        gateway 10.8.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

But when I enable the bridge interface I find that I can no longer ssh to my EC2 instance.  
```

sudo /etc/init.d/networking restart

```
I can do a port scan and the EC2 server is no longer responding to port 22 after the network or server has restarted.


What am I doing wrong?

---

### Post by Jonathan L on 2011-10-18
> **mixersoft said:**
> I'm using the same guide, but running into an EC2 problem -- 
I configure the bridge using this guide ([https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging)) and the following params:

```

auto br0...

Hi

It's not clear why you want to bridge your network to the AWS network, instead of just routing, or perhaps using a tunnel.  For what it's worth, I use tunnels to AWS frequently, with the following commands:

T is the target machine, ie the IP address at AWS.
E is the local machine's external IP address

[CODE]ssh -i $SSHKEY ubuntu@$T \
    sudo openvpn --remote $E --dev tun1 --ifconfig 10.10.10.1 10.10.10.2 --daemon

sudo openvpn --remote $T --dev tun1 --ifconfig 10.10.10.2 10.10.10.1 --daemon
```Is that any help?

Kind regards,
Jonathan.

---

### Post by mixersoft on 2011-10-19
My goal is to be able to let a few people have accounts to access this vpn from different desktops/iPhones and to make it relatively simple. And I only need to provide internet access (via IP forwarding).

Given these requirements, is routing my best option -- and can I setup these connections using something like OpenVPN GUI?

---

### Post by Jonathan L on 2011-10-21
> **mixersoft said:**
> My goal is to be able to let a few people have accounts to access this vpn from different desktops/iPhones and to make it relatively simple. And I only need to provide internet access (via IP forwarding).

Given these requirements, is routing my best option -- and can I setup these connections using something like OpenVPN GUI?

Hi again

I'm sorry but I'm not clear what the server is doing: what sort of "access" do they need? Obviously they can ssh in if you give them accounts.  "Interent access" you can set up with IP forwarding on the server, with NAT if you want, which can be set up with iptables.

If there's only a few users, you can certainly have openvpn tunnels set up for each of them, with the commands I showed earlier or, I'm sure, its gui (though I have not experience of that).

Can I ask what it's for?  The users already have internet access if they can contact the AWS server.

Kind regards
Jonathan

---

### Post by shohoku11wrj on 2013-04-21
Hi there,I have encountered the same problem.The EC2 cannot restart again, stopped at checking 1/2, after I setting up OpenVPN bridge and start openvpn.But I have successfully make it when using routing mode on OpenVPN.In order to play LAN game via the OpenVPN (just for interests and trying setting up VPN on EC2, so, please DON'T recommand me other platform or tools),it seems only the bridge mode on OpenVPN can.I followed the guide: [https://community.openvpn.net/openvpn/wiki/OpenVPNBridging](https://community.openvpn.net/openvpn/wiki/OpenVPNBridging)  &  [http://www.server-world.info/en/note?os=CentOS_6&p=openvpn](http://www.server-world.info/en/note?os=CentOS_6&p=openvpn)

---

### Post by wildmanne39 on 2013-04-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

