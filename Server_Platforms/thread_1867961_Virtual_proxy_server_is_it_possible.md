---
title: "Virtual proxy server is it possible"
date: 2011-10-23
forum: Server Platforms
---

### Post by w1d3 on 2011-10-23
is there a way to make a virtual server act like a proxy for the system the virtual server is running on

---

### Post by koenn on 2011-10-23
sure

---

### Post by w1d3 on 2011-10-24
> **koenn said:**
> sure
so can you help me setup one ?
i have ubuntu server 10.04 installed as the virtual machine i tried to setup ssh but i cant get connected to the server and i thought it wasn't possible to get it done on 1 machine ..

---

### Post by koenn on 2011-10-24
the thing with virtual machines is that they're just like "real" machines if you treat them as such.

the tricky part is the virtual machine configuration, especially, in cases like this, how the virtual machine connects to the (real) network.

There's roughly 2 ways of doing that, 
- whit NAT (where the physical machine, a.k.a. the host, uses routing and NAT to provide network to the virtual machine, a.k.a. the guest)
- "bridged", where the NIC of the guest is virtually linked to the NIC of the host, and is visible on your network with its own IP address, indistinguishable from a 'real' computer.
- (there's also "host only", you don't want that)

In the bridged case, you can reach the VM through its IP address and any service running there (proxy, ssh-server, web server, ...) can be connected to

in the NAT case, the NAT prevents connections from outside towards the guest (just as a broadband router prevents incoming connections to a private LAN because it NATs the private addresses)

in short : have your virtual machine configured for non-NAT networking, and treat it as a real server (this simply means that you have to configure its NIC correctly, and install the services you want to use)

How you do this depends on what you use for virtualization. I've done it with VMware Server, and Virtualbox-OSE. I have no experience with other solutions, but I assume they work in a similar manner.

---

### Post by w1d3 on 2011-10-24
> **koenn said:**
> the thing with virtual machines is that they're just like "real" machines if you treat them as such.

the tricky part is the virtual machine configuration, especially, in cases like this, how the virtual machine connects to the (real) network.

There's roughly 2 ways of doing that, 
- whit NAT (where the physical machine, a.k.a. the host, uses routing and NAT to provide network to the virtual machine, a.k.a. the guest)
- "bridged", where the NIC of the guest is virtually linked to the NIC of the host, and is visible on your network with its own IP address, indistinguishable from a 'real' computer.
- (there's also "host only", you don't want that)

In the bridged case, you can reach the VM through its IP address and any service running there (proxy, ssh-server, web server, ...) can be connected to

in the NAT case, the NAT prevents connections from outside towards the guest (just as a broadband router prevents incoming connections to a private LAN because it NATs the private addresses)

in short : have your virtual machine configured for non-NAT networking, and treat it as a real server (this simply means that you have to configure its NIC correctly, and install the services you want to use)

How you do this depends on what you use for virtualization. I've done it with VMware Server, and Virtualbox-OSE. I have no experience with other solutions, but I assume they work in a similar manner.
that was exactly what i needed to know THANKS ((:

---

### Post by koenn on 2011-10-25
> **w1d3 said:**
> that was exactly what i needed to know THANKS ((:

you're welcome, 

have fun.

---

### Post by w1d3 on 2011-10-25
OK so i got connected to the VM and when i changed my web browsers proxy settings to connect to my server every time i try to load a page in the browser i get this:


```
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7Protocol mismatch.
```And this is what i did:

1. Installed Ubuntu Server 10.04 with ssh
2. Configured **/etc/ssh/sshd_config** i changed the port and a few other things added users and made a password 
3. Installed and configured Squid changed some settings in** /etc/squid/squid.conf** for anonymous proxy

---

### Post by koenn on 2011-10-25
> **w1d3 said:**
> OK so i got connected to the VM and when i changed my web browsers proxy settings to connect to my server every time i try to load a page in the browser i get this:


```
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7Protocol mismatch.
```And this is what i did:

1. Installed Ubuntu Server 10.04 with ssh
2. Configured **/etc/ssh/sshd_config** i changed the port and a few other things added users and made a password 
3. Installed and configured Squid changed some settings in** /etc/squid/squid.conf** for anonymous proxy

okay .....

it's not really clear to me what you're trying to do : you get an ssh protocol mismatch in a *browser* ? Are you trying ssh through a browser and an anonymous proxy ? Why on earth would you try to do that ? 
Did you set ssh to listen on port 80 ? What would you hope to accomplish with that ?

Or are you just very confused and you think that ssh is a requirement for running a proxy ?

---

### Post by w1d3 on 2011-10-25
> **koenn said:**
> okay .....

it's not really clear to me what you're trying to do : you get an ssh protocol mismatch in a *browser* ? Are you trying ssh through a browser and an anonymous proxy ? Why on earth would you try to do that ? 
Did you set ssh to listen on port 80 ? What would you hope to accomplish with that ?

Or are you just very confused and you think that ssh is a requirement for running a proxy ?

Im using ssh so that the connection from the client to the host can be encrypted and yes im a little confused

---

### Post by koenn on 2011-10-25
that's a whole different problem than setting up  a proxy server on a VM

I suggest you 
1. check that the proxy works for normal browsing etc (squid requires a bit of configuration)
2. check that ssh works. Set its config back to defaults so you don't confuse people when you ask for help
3. use separate threats if you need help with any of the above
4. when you're sure you have a working proxy and a working ssh, make a new thread about how to tunnel your proxy connection through ssh

---

### Post by w1d3 on 2011-10-25
> **koenn said:**
> that's a whole different problem than setting up  a proxy server on a VM

I suggest you 
1. check that the proxy works for normal browsing etc (squid requires a bit of configuration)
2. check that ssh works. Set its config back to defaults so you don't confuse people when you ask for help
3. use separate threats if you need help with any of the above
4. when you're sure you have a working proxy and a working ssh, make a new thread about how to tunnel your proxy connection through ssh
ok ill see what i can do

---

### Post by headvampyre@hotmail.co.uk on 2011-10-26
By "Virtual proxy server" do you mean accessing a proxy in another location (A forwarding proxy (Like at schools and workplaces))?

If so, you may want to look into using OpenVPN or another VPN solution.

If your looking to use a proxy with encryption, I'd continue to look at Squid as I'm sure that supports SSL/TLS encryption.

If your looking to use a reverse proxy( Like anonymouse.org) with encryption, look at using a proxy with TOR support (Onion routing, basically where the data is encrypted multiple times, extremely difficult to decrypt if configured correctly, but please, don't go watching kiddie porn.).

Hope this helps.

---

### Post by collisionystm on 2011-10-26
What platform are you using to Virtualize? Virtualbox?

If you are looking to build a Proxy server quickly and efficiently, use Zentyal. It is based on Ubuntu 10.04 and you can do it all via a nice web interface.

As far as your network connections.. that is pretty easy. You will however PROBABLY need 2 PHYSICAL nic cards... but you might be able to get away with one depending on the router.
Either way, your virtual machine needs to have 2 NIC cards. Set them to bridged, as suggested. Not NAT.

When you bridge the virtual interfaces, you can choose what physical adapter you want to hook it to. The way I imagine the setup is, 2 Physical NIC's. One plugging into the local network, the other into the Internet router.

Local traffic hits NIC 1, filters in proxy, goes out NIC 2.

If this is in your house and you just have some kind of linksys router, you can get away with 1 nic card. You still need 2 virtual adapters though. One in and one out.

---

