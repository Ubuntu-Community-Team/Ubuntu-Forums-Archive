---
title: "Different class IPs on same NIC"
date: 2012-01-16
forum: Server Platforms
---

### Post by patdundee on 2012-01-16
Hi Guys
Setting mulitple IPs is not a problem. How do you set up 2 different multiple class ips on one NIC though and do we set 2 different gateways for it to work
 
 
First IP 192.168.101.100.1/27 Gatway 192.168.1.98 Subnet 255.255.255.224
 
Second IP 192.168.250.228/24 Gatweway 192.168.250.226
 
how would we get around this one please
 
Many thanks

---

### Post by SeijiSensei on 2012-01-16
What have you tried?  Have you tried aliasing the adapter (e.g., defining an eth0:0 interface with ifconfig as well as eth0)?  I've only done this with IPs in the same CIDR block, so I don't know if it will work at all.  If you succeed in getting an alias to accept an address in the second range, you'll need to add the appropriate route commands to declare the correct gateways.

Once you get things set up as you like them, you can add the appropriate ifconfig and route commands to /etc/rc.local to ensure they will be run upon every reboot.

---

### Post by jonobr on 2012-01-16
> First IP 192.168.101.100.1/27 Gateway 192.168.1.98 Subnet 255.255.255.224


Default gateway in the above statement is in a different subnet.

Not sure how you can get to the default gateway with this?
Might be missing something though!!!

(Just wanted to add, that the topic "Different class IPs on same NIC" Im guessing the different classes relate to ip1 and ip2 not in ip1)

---

### Post by SeijiSensei on 2012-01-16
> **jonobr said:**
> Default gateway in the above statement is in a different subnet.

A host can only have one default gateway.  However he can declare a gateway for each of the address blocks in a route command. So you'd have a route for 10.10.10.0/24 via, say, 10.10.10.1, and another for 10.10.11.0/24 via 10.10.11.1.  The default gateway can be on either network as long as the gateway is visible to the host.

---

### Post by patdundee on 2012-01-17
Many thanks guys. I will give this a try. If all else fails I supose I can always put a second NIC in which will make it easier. Not one for taking the easy option, we would nover solve bigger issues if we did that lol

:)

---

### Post by jonobr on 2012-01-17
Hi there 
SeijiSensei is correct , so watch out for that, I mixed up default gateway and gateway....

What I would check on is your subnets and gateways and make sure they match with whats above

Thanks

jonobr

---

### Post by hawkmage on 2012-01-17
> First IP [COLOR=Red]192.168.101.100.1[/COLOR]/27 Gatway 192.168.1.98 Subnet 255.255.255.224
There are 5 octets in the first IP address.  

There should be no reason that you can't use different net masks as long as they are valid on your network.

It may be helpful if you included the output from ifconfig and route so we can see how things are getting setup.

---

### Post by jonobr on 2012-01-17
The 5 octet IP address may be an attempt to implement the first operational [IPV7 network]("http://ubuntuforums.org/showthread.php?p=11618612#post11618612") :)

> YKYAG when you make a joke about IPV7 in a support thread

---

### Post by HugoSerrano on 2012-01-17
Hello!

You can do what you want. But first you need to know what's that.

You can give multiple IP's to the same nic, no problem.

#ifconfig eth0 10.0.0.1 netmask 255.255.255.0
#ifconfig eth0:1 192.168.1.1 netmask 255.255.255.0
#ifconfig eth0:2 192.168.101.100 netmask 255.255.255.224

Your host, can have one default gateway.
You can add static routes if you need.

This will not work if you're trying to connect to a switch with Vlans.

Best Regards!

---

### Post by hawkmage on 2012-01-17
> **HugoSerrano said:**
> Your host, can have one default gateway.
You can add static routes if you need.
I would say that you should have only one default gateway.  You can define more than one but that can cause issues with routing.  

I have run into this when someone has created a virtual interface and just copies the whole block in the interfaces file for the primary interface that includes the creation of the default route.

---

### Post by gsgleason on 2012-01-18
I think using vlans would be a better solution than subinterfaces.

---

### Post by hawkmage on 2012-01-18
> **gsgleason said:**
> I think using vlans would be a better solution than subinterfaces.
And how do you propose supporting multiple VLANs without using virtual interfaces?

---

### Post by bab1 on 2012-01-19
> **hawkmage said:**
> And how do you propose supporting multiple VLANs without using virtual interfaces?

I don't think simple sub-interfaces are correct for vlan trunking ( IEEE 802.1q) for Ubuntu.  What is needed is the "vlan" package.

Note eth0:n sub-interface (alias) is not the same as a eth0.n vlan sub-interface (note the : vs the .).  An alias such as eth0:n is just the alias (no tags for trunking).

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.microhowto.info/howto/configure_an_ethernet_interface_as_a_vlan_trunk_on_debian.html") for a basic tutorial.

---

### Post by hawkmage on 2012-01-19
> **bab1 said:**
> I don't think simple sub-interfaces are correct for vlan trunking ( IEEE 802.1q) for Ubuntu.  What is needed is the "vlan" package.

Note eth0:n sub-interface (alias) is not the same as a eth0.n vlan sub-interface (note the : vs the .).  An alias such as eth0:n is just the alias (no tags for trunking).

See [**_[COLOR=Blue]here[/COLOR]_**]("http://www.microhowto.info/howto/configure_an_ethernet_interface_as_a_vlan_trunk_on_debian.html") for a basic tutorial.
The OP was just asking about putting multiple IPs with differnt net masks on an interface.  Someone else sugested VLANs.  If the network is not already using VLANs adding a VLAN interface will do nothing for you.  

I was asking gsgleason how they planned to implement VLANs with a virtual/sub interface.

---

### Post by gsgleason on 2012-01-19
Separating the broadcast between the two subnets would be a good idea.  Sure, you can have multiple addresses on different subnets on the same broadcast domain, but thats just abnormal.

Using vlans would require the server connected to a switch that supports vlans as well.

---

