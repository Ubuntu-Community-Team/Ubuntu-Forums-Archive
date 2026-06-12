---
title: "Configuring a network using kvm"
date: 2012-04-26
forum: Virtualisation
---

### Post by gerger09 on 2012-04-26
Hi I would like to know if it is possible to simulate a network using kvm running on a single machine. If it is indeed possible how does one do it?

---

### Post by zeljkojagust on 2012-04-26
How do you mean "simulate"? Can you clarify a bit what do you exactly want.

---

### Post by gerger09 on 2012-04-26
I would be using 3 guest machine 1 would act as a router to connect the other 2. I apologize for not giving enough details as this is my first time posting on a forum.

---

### Post by zeljkojagust on 2012-04-27
OK, first you need to set up network bridge on your KVM physical machine:
[http://blog.agdunn.net/?p=416](http://blog.agdunn.net/?p=416)
(Check out setting up a bridge section)

After that one is done, you create your first VM that has two network interfaces. One will be connected to your local network over bridged network interface and one will be a "virtual" interface connected to internal virtual network on which your other two guests will reside. After that by using iptables on the first guest (one with two interfaces) you need to configure a gateway/firewall so other two guests can access internet and communicate with each other. It's also nice to configure DNS/DHCP if you don't like static/manual network configuration on all of your guests.

So if your LAN has a network 192.168.1.0/24 and let's say your physical machine (the one on which KVM is installed) has IP 192.168.1.1, the network configuration of your guests can be something like this:

Guest01 - two network interaces one with IP 192.168.1.2 that has access to your LAN and other let's say 172.16.1.1 for internal virtual network. An iptables configuration that allows 172.16.1.0/24 machines access to 192.168.1.0/24 network and internet.

Guest02 - one network interface with 172.16.1.2 and 172.16.1.1 as gateway.
Guest03 - same as Guest02, except with 172.16.1.3 IP address

If you have any other questions be free to ask here or PM me directly.

---

