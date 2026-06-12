---
title: "One NIC Two IPs as router"
date: 2008-06-04
forum: Server Platforms
---

### Post by computerwolf on 2008-06-04
I am attempting to use ubuntu as a router for the rest of my network. My ISP provides 2 IPs through one line. What I am wanting to do is use one of the IPs to act as the IP for only one of the connected computers or at least have certain ports use that IP for only one computer. All the rest will fall under the other IP, but I can't seem to get the configuration right with setting up the interfaces and dnsmasq and my iptables. I have everything functioning when it isn't doing any routing, but it is only using one IP at that point and i'm not even sure how to get it to recognize the other.

---

### Post by rickyjones on 2008-06-04
> **computerwolf said:**
> I am attempting to use ubuntu as a router for the rest of my network. My ISP provides 2 IPs through one line. What I am wanting to do is use one of the IPs to act as the IP for only one of the connected computers or at least have certain ports use that IP for only one computer. All the rest will fall under the other IP, but I can't seem to get the configuration right with setting up the interfaces and dnsmasq and my iptables. I have everything functioning when it isn't doing any routing, but it is only using one IP at that point and i'm not even sure how to get it to recognize the other.

Your topic sounds a little confusing, let me tell you what I'm getting from it and I want you to tell me if I'm correct.

1. Your ISP assigned you two public IP addresses.
2. You want one computer on your LAN to have that IP assigned and the other IP will be shared by the rest of your LAN, most likely via NAT.
3. You have a server that you wish to use to control all of this, but it only has one NIC.

Am I correct so far? If so then this is NOT going to work (if I recall correctly).

I have a friend that used to be in a similar situation. He runs a business and his T1 line has 5 available IP addresses. He wanted to use one specifically for the LAN (NAT'ed) and 1 specifically for his single mail/web server. His T1 line terminates at a standard CAT5 jack. Here is what he did, and I recommend the same solution if you can.

1. Pick up a standard 10/100 5 port network switch.
2. Connect internet line to port 1 of switch.
3. Connect your single server to switch. On the server assign one of your public IPs to it's NIC. Verify connection.
4. Pick up a standard cable/dsl router/gateway. Plug the internet (WAN) port into the switch. Manually assign the router's WAN interface another public IP address. Connect your normal LAN switch to the LAN side of the router.

Now your server is on the 'net without any firewall using a public IP. Your LAN is on the 'net behind a router firewall using a different public IP.

Your mileage may vary but if your internet connection is anything like a T1 then this should work without issue.

Sincerely,
Richard

---

### Post by computerwolf on 2008-06-04
Sorry my post was so confusing, let me explain a little better.

1. The server has 2 NICs, one going to a switch which contains the rest of the network, the other receives the incoming internet data.

2. The incoming internet line supplies 2 public IPs.

3. I would like the server to be able to distribute the IPs via NAT at my discretion to the rest of the network.

4. One computer connected to the switch is to use one of the IPs specifically, the rest of the network is to use the other.

Hopefully this clears things up, and hopefully there is an answer to my dilemma!

---

