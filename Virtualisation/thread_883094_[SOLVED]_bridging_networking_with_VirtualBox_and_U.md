---
title: "[SOLVED] bridging networking with VirtualBox and Ubuntu"
date: 2008-08-07
forum: Virtualisation
---

### Post by herbert tamayo on 2008-08-07
Hi, I'm using ubuntu 8.04 and virtualbox 1.6.2. I'm trying to bridge networking between my host OS and the guest OS, so I'm following a how-to that I found and it was written using exactly the same version of virtualbox and ubuntu.


So, when I do the follow steps:
```

sudo invoke-rc.d networking stop

sudo nano /etc/network/interfaces

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
address       192.168.1.2
netmask       255.255.255.0
broadcast     192.168.1.255
gateway       192.168.1.1

bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

auto eth0
iface eth0 inet dhcp

sudo /etc/init.d/networking restart

```

In fact, I obtained my IP from the dhcp and also the bridge got the ip static that I want, but I just lost internet conecction, it seems that I'm out of the network services, if I tried to use the internet I received a message from my browser that the proxy is rejecting connection.

My network enviroment is:
-Squid for authentication and access to the internet
-Astaro for web filter
-the network is "A" class
-dhcp

My questions are:
-how can I create my bridge object --for networking between host and guest OS-- and at the same time keep my network services? such as internet

-why the br0 object creates a conflict between the internet connection?

-Do i have to use a Class A ip for br0 setting or can I use the setting that I decide to use? (address 192.168.1.2, netmask 255.255.255.0 ....)

Regards

---

### Post by herbert tamayo on 2008-08-08
When I posted that message I had big confussions with almost all terms related to bridge networking.

For questions 1 and 2, the answer is that I was trying to manage the bridge and the eth0 as separated objects, I read that the bridge manage the eth0 and the virtual devices, through the bridge the eth0 and the virtual devices will acquire network services, such as internet, printing, etc.

So, the final configuration that It works for me is:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

also, these links help me a lot:
[http://www.linuxfoundation.org/en/Net:Bridge](http://www.linuxfoundation.org/en/Net:Bridge)
[http://www.tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO.html](http://www.tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO.html)

Regards

---

### Post by crewmanjoo on 2008-08-08
Hi herbert,

I am trying to do the same thing on virtualbox but our scenarios might be different.

We cannot get our virtual machine to get on the internet or ping it on our network. We can ping the host no problem.

In your setup are you using DHCP for the host and virtualmachine? In our case we are using a static IP for Host and another for the guest. We are trying to setup the bridge so we can see the host as a seperate IP on the network and the guest as a seperate IP.

In your file config there is no static IP set for the host? Im confused.

Can you post what you setup for the guest (virtualmachine) in your network config.

---

### Post by herbert tamayo on 2008-08-08
crewmanjoo:

In fact, your scenario is my "new scenario" since I figured out that I took another ip from the dhcp server for the br0, that is not right because the system administrator needs as many free ip as he can, so that is not acceptable to take more than one ip. I'm trying to work with one ip from the dhcp and then re-create a virtual network inside my linux box; at this time I'm working wih dnsmasq to help to forward the new ip's, when I get these all work I will let you know.

About your questions:
My eth0 has a dynamic ip, but if I want to the br0 works I have to drop that ip and let the br0 works as dynamic, something like:

```

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

ques 2: for my guest I used this code:
```

sudo VBoxAddIF vbox0 `whoami` br0
VBoxManage modifyvm "WRITE THE NAME OF THE GUEST" -hostifdev1 vbox0
sudo chmod 0666 /dev/net/tun

```

When I get new scenario work I'll post.

Regards

---

