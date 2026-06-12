---
title: "ipv6 fun."
date: 2012-02-17
forum: Server Platforms
---

### Post by jailbait on 2012-02-17
Im currently using Ubuntu as a gateway for VMs.

The IPV6s are bound to the Ubuntu, and another virtual network interface powers virtual LAN.
ipv6 currently works on ubuntu

How can I route these ipv6s to the VMs?

---

### Post by jonobr on 2012-02-17
Sounds like you know your stuff, but Ill just rhough this out there anyway.

Did you check to ensure IPv6 forwarding was enabled in /etc/sysctl.conf and ipv4 forwarding was disabled?

---

### Post by jailbait on 2012-02-17
> **jonobr said:**
> Sounds like you know your stuff, but Ill just rhough this out there anyway.

Did you check to ensure IPv6 forwarding was enabled in /etc/sysctl.conf and ipv4 forwarding was disabled?
IPV6 forwarding is enabled, but shouldn't I be capable of using dualstack?

It should work, since I configured this with an ipv6 HE tunnel before I got native ipv6, and dual stack worked just fine.

---

### Post by jonobr on 2012-02-17
Yep, I would have figured dual stack should work

heres something I found which seems to concur,
maybe run a wireshark trace to see whats going on

> Configure your Ubuntu box as a IPv6 router

    Edit /etc/sysctl.conf 

Uncomment the line which contains net.ipv6.conf.default.forwarding=1. This is a common step to enable IPv6 routing.

You can learn how to install and enable DHCPv6 on your network here.

Alternatively, if you want to use radvd which will advertise your prefix and let the network's systems select their own IP address:

    Install radvd 

sudo aptitude install radvd

    Edit /etc/radvd.conf (see following sample) 

Note: If the computer is only routing IPv6, then only uncomment net.ipv6.conf.default.forwarding=1 and leave the IPv4 stuff unchanged.

Note: /etc/radvd.conf: This file does not exist after a fresh install. You can look at the sample configuration files in usr/share/doc/radvd/examples/ for further studies.

Sample /etc/radvd.conf:

interface eth0
{
   AdvSendAdvert on;
   prefix 2001:xxxx:xxxx::/64
   {
        AdvOnLink on;
        AdvAutonomous on;
   };
};

eth0 is the interface which is used for the Router Advertising messages (RAs). If you are not sure about the interface, check with <tt>ip addr</tt> on the command line.

The prefix you have to take from the information given by the Sixxs or Hurricane Electric stuff.

Restart the router advertising daemon to propagate your IPv6 address space

sudo /etc/init.d/radvd restart

Now router should automatically send "Router Advertising Messages" to your network and your IPv6 clients should auto configure them self. 

---

### Post by Go3Team on 2012-02-17
> **jonobr said:**
> Yep, I would have figured dual stack should work

heres something I found which seems to concur,
maybe run a wireshark trace to see whats going on

I updated my connection to IPV6 earlier this week utilizing a tunnel.  I had to install radvd and use the eth1 (local network side).  Once I restarted radvd, IPV6 propagated throughout the network on its own, even the computers I have set with static IPs automatically added IPV6.

Here's my radvd.conf if you want to try it:

```

interface eth1
{
   AdvSendAdvert on;
   AdvLinkMTU 1480;
   MinRtrAdvInterval 60;
   MaxRtrAdvInterval 180;
   prefix XXXX:XXXX:XXXX:179::/64       <---- use your own prefix here.
   {
        AdvOnLink on;
        AdvAutonomous on;
        AdvOnLink on;
        AdvRouterAddr on;
        AdvPreferredLifetime 600;
        AdvValidLifetime 3600;
   };
   route ::/0 {
   };
};

```

---

### Post by jonobr on 2012-02-17
Hey

Ill try , but not sure Ill get to it soon:-(

---

### Post by jailbait on 2012-02-17
Thats exactly what I did - the ipv6s on the private LAN are private ipv6s, and the assignments work. Its just that my firewall rules are crapped out, and its not allowing me to pass on the ipv6 traffic (eth1) to my eth0 interface.
Right now, I either have two choices.


[LIST=1]
[*]Scrap the LAN ipv6s, and forward from ipv6 -> ipv4 (is that possible?)
[*]Fix the LAN ipvs6s, and foward that way.
[/LIST]

---

### Post by hawkmage on 2012-02-17
I am currently using an HE IPv6 on my firewall so from my internal network perspective its like I have a native IPv6 connection to the internet.  It is working for me but I do not rely on radvd or DHCP6.  In my Ububtu systems I explicitly set the global IPv6 address and default route in the interfaces file.

I have a few questions about your config.  

Are the VMs running on the Ubuntu server you are using for a gateway?  If so what are you using to run your VMs? KVM, VirtualBox  or something else.  Also is the interface on the VM bridged or NATed?

Can you show what your IPv6 routing table on the VM Guest.

---

### Post by jailbait on 2012-02-17
> **hawkmage said:**
> I am currently using an HE IPv6 on my firewall so from my internal network perspective its like I have a native IPv6 connection to the internet.  It is working for me but I do not rely on radvd or DHCP6.  In my Ububtu systems I explicitly set the global IPv6 address and default route in the interfaces file.

I have a few questions about your config.  

Are the VMs running on the Ubuntu server you are using for a gateway?  If so what are you using to run your VMs? KVM, VirtualBox  or something else.  Also is the interface on the VM bridged or NATed?

Can you show what your IPv6 routing table on the VM Guest.
The gateway is on the VM.

For all purposes, just pretend that the VM doesn't exist. Its easier that way, since im running ESXi, so its identical to a real-world configuration.

So if my ipv6 was 2000:db8:a:24::2/64 
and my gateway is 
2000:db8:a:24::1/64,

what would I put in:
a) The internet-facing gateway interface
b) The LAN facing gateway interface
c) The clients?

And yes, I know, those are not my real ips.

---

### Post by hawkmage on 2012-02-17
OK, I am assuming that you have more than one interface on the VM.  You should have a LAN and a WAN interface.  

Have you been given the entire 2000:db8:a:24::/64 subnet?  Or is that just the address for your WAN address?

On the VM your IPv6 default gateway sould be 2000:db8:a:24::1/64

For the clients and the LAN interface of the VM I really can't say yet.  It depends on if you are using a different subnet than 2000:db8:a:24::/64 on your internal network or not.  

If your internal network is using the 2000:db8:a:24::/64 subnet then your VM is more of a bridge than a router.  Your LAN interface would use an address like 2000:db8:a:24::3/64 and your clients would get some other address in the 2000:db8:a:24::/64 subnet and use the 2000:db8:a:24::1/64 for their default gateway.

If you are using a different subnet on your LAN then your LAN interface IPv6 Address will be your clients default gateway.

---

### Post by jailbait on 2012-02-18
> **hawkmage said:**
> OK, I am assuming that you have more than one interface on the VM.  You should have a LAN and a WAN interface.  

Have you been given the entire 2000:db8:a:24::/64 subnet?  Or is that just the address for your WAN address?

On the VM your IPv6 default gateway sould be 2000:db8:a:24::1/64

For the clients and the LAN interface of the VM I really can't say yet.  It depends on if you are using a different subnet than 2000:db8:a:24::/64 on your internal network or not.  

If your internal network is using the 2000:db8:a:24::/64 subnet then your VM is more of a bridge than a router.  Your LAN interface would use an address like 2000:db8:a:24::3/64 and your clients would get some other address in the 2000:db8:a:24::/64 subnet and use the 2000:db8:a:24::1/64 for their default gateway.

If you are using a different subnet on your LAN then your LAN interface IPv6 Address will be your clients default gateway.
Yup. One of the network cards is connected to a switch for the LAN, and the other is connected to the internet.
Yes, thats the entire subnet. Must have been a typo earlier. The LAN uses the same subnet though.

Ive tried it. The clients cannot ping the gateway.

Could it be the ip6tables rules?

---

### Post by hawkmage on 2012-02-18
Yes if you are using ip6tables you will have to let icmpv6 of type echo-request through.  

You do not want to allow all icmpv6 types through, some are used for neighbour discovery and things you probably don't want coming in or getting out through your VM.

---

### Post by jailbait on 2012-02-18
> **hawkmage said:**
> Yes if you are using ip6tables you will have to let icmpv6 of type echo-request through.  

You do not want to allow all icmpv6 types through, some are used for neighbour discovery and things you probably don't want coming in or getting out through your VM.
Ive already done that. There still seems to be something missing thats not allowing me to ping or connect to anything that deals with ipv6 from my clients, but allowing me to ping from my gateway. I can even look up the address from the client.

**Current Configuration:**

eth0 - External, connected to 1GiB/s port on Foundry BigIron 15000[INDENT]IPV6: 2604:4300:a:24::2
Netmask: 64
IPV6 Gateway:  2604:4300:a:24::1[/INDENT]eth1 - Internal Network[INDENT]IPV4: 10.0.0.1 (working)
IPV6: 2604:4300:a:24::3
Netmask: 64
IPV6 Gateway:  2604:4300:a:24::1
[/INDENT]IPV6s assigned and announced via radvd:[INDENT]```

interface eth1 {[INDENT] AdvSendAdvert on;     
MinRtrAdvInterval 3;     
MaxRtrAdvInterval 10;     

prefix 2604:4300:a:24::/64 {[INDENT]AdvOnLink on;         
AdvAutonomous on;         
[/INDENT][INDENT]AdvRouterAddr on;     
[/INDENT]}; 
[/INDENT]};
```[/INDENT]Firewall (modified stateful firewall example from sixxs)[http://www.sixxs.net/wiki/IPv6_Firewalling](http://www.sixxs.net/wiki/IPv6_Firewalling)
```
ip6tables -F
ip6tables -X

ip6tables -A INPUT -i lo -j ACCEPT
ip6tables -A OUTPUT -o lo -j ACCEPT

ip6tables -A OUTPUT -o  eth0 -j ACCEPT

ip6tables -A INPUT -i  eth1 -j ACCEPT
ip6tables -A OUTPUT -o eth1 -j ACCEPT

ip6tables -A INPUT -m rt --rt-type 0 -j DROP
ip6tables -A FORWARD -m rt --rt-type 0 -j DROP
ip6tables -A OUTPUT -m rt --rt-type 99 -j DROP

ip6tables -A INPUT -s fe80::/10 -j ACCEPT
ip6tables -A OUTPUT -s fe80::/10 -j ACCEPT

ip6tables -A INPUT -d ff00::/8 -j ACCEPT
ip6tables -A OUTPUT -d ff00::/8 -j ACCEPT

ip6tables -I INPUT -p icmpv6 -j ACCEPT
ip6tables -I OUTPUT -p icmpv6 -j ACCEPT
ip6tables -I FORWARD -o icmpv6 -j ACCEPT

ip6tables -A FORWARD -m state --state NEW -i eth1 -o eth0 -s  2604:4300:a:24::/48 -j ACCEPT

ip6tables -P INPUT DROP
ip6tables -P FORWARD DROP
ip6tables -P OUTPUT DROP
```

It might be worth noting that I cannot connect to my client ipv6s from my gateway either.

---

### Post by hawkmage on 2012-02-18
What does your IPv6 routing table look like on your VM and your clients?

---

### Post by jailbait on 2012-02-18
The formatting screws up when pasted here, so...
Gateway: [http://paste.ubuntu.com/847657/](http://paste.ubuntu.com/847657/)

Client: [http://paste.ubuntu.com/847654/](http://paste.ubuntu.com/847654/)

EDIT:
You know what?
I give up for now. Ill bind my ipv6s to the gateway, and pull them through using nginx forwarding.

---

### Post by hawkmage on 2012-02-18
OK, but it looks like it is the routing on the gateway that is getting in the way.

You have duplicate routes with the same metric on both interfaces.  The route for 2604:4300:a:24::/64 on eth1 and a route for 2604:4300:a:24::1 on eth0.

This way traffic to 2604:4300:a:24::1 goes out eth0 and everything else for 2604:4300:a:24::/64 goes to eth1.

---

### Post by jailbait on 2012-02-19
> **hawkmage said:**
> OK, but it looks like it is the routing on the gateway that is getting in the way.

You have duplicate routes with the same metric on both interfaces.  The route for 2604:4300:a:24::/64 on eth1 and a route for 2604:4300:a:24::1 on eth0.

This way traffic to 2604:4300:a:24::1 goes out eth0 and everything else for 2604:4300:a:24::/64 goes to eth1.
Hmm. lemme try this tomorow.

---

