---
title: "Proxy/Router setup help please"
date: 2009-07-17
forum: Server Platforms
---

### Post by peekaboo on 2009-07-17
I have Ubuntu server installed and my main machine runs Windows 7.
My internet cable is connected to a switch, from which my Vonage adapter takes one ip address and my 4-port router takes another address.
My main computer, my wife's computer, a media-center computer and the server take up all 4 ports.
I have additional routers/switches lying around.

I'd like to be able to connect more computers to my network (but I'm out of router ports) and I'd also like to be able to access web-downloads that limit simultaneous downloads from the same ip address (like rapidshare) by accessing them via a proxy.

How can I set this up (Hardware connections and software)?

Thanks.

---

### Post by kustomjs on 2009-07-17
if you have a spare computer with 4 nic cards turn it into a smoothwall router and get a 16port switch then that should solve your problem.

or just get a 16port switch.

---

### Post by peekaboo on 2009-07-17
> **kustomjs said:**
> if you have a spare computer with 4 nic cards turn it into a smoothwall router and get a 16port switch then that should solve your problem.

or just get a 16port switch.

Can you elaborate please?
I'm a newbie.

---

### Post by dragos2 on 2009-07-17
> **peekaboo said:**
> I have Ubuntu server installed and my main machine runs Windows 7.
My internet cable is connected to a switch, from which my Vonage adapter takes one ip address and my 4-port router takes another address.
My main computer, my wife's computer, a media-center computer and the server take up all 4 ports.
I have additional routers/switches lying around.

I'd like to be able to connect more computers to my network (but I'm out of router ports) and I'd also like to be able to access web-downloads that limit simultaneous downloads from the same ip address (like rapidshare) by accessing them via a proxy.

How can I set this up (Hardware connections and software)?

Thanks.

Not very ubuntu related but:

- you can cascade switches from one of your 4 port router and then you can
add more computers to your network, but beware that routers split collision domains
and most of switches don't ! This translates into sharing issues across router split
computers

- for the proxy thing use tor or whatever you like

---

### Post by peekaboo on 2009-07-17
> **dragos2 said:**
> Not very ubuntu related but:

- you can cascade switches from one of your 4 port router and then you can
add more computers to your network, but beware that routers split collision domains
and most of switches don't ! This translates into sharing issues across router split
computersNot sure what this means. If I connect my switch to a router port and then 2-3 computers to the switch, will they each receive an internal ip address from the router and be able to share files with other computers on the network?

> - for the proxy thing use tor or whatever you like
What are my options?

---

### Post by dragos2 on 2009-07-17
> **peekaboo said:**
> Not sure what this means. If I connect my switch to a router port and then 2-3 computers to the switch, will they each receive an internal ip address from the router and be able to share files with other computers on the network?


What are my options?

Your 2-3 computers will see each other, and yes they will most probably get a class C ip from
the router through dhcp. But if you have another computer plugged into the router directly
it will be harder to join them in the same domain.

I told you: tor, vpn if you know to setup, there are also paid proxy and vpn solutions.

---

### Post by peekaboo on 2009-07-17
So do I have to separate issues here?
Can I not have my main computer connected to the internet through the server and still be able to access the web with 2 different ip addresses simultaneously?

---

### Post by kustomjs on 2009-07-17
there is no way to get 2 different real world ip address off of one cable modem. what you need to do is setup smoothwall so you can have 3 different internal IP address linked to your real world ip.

say like your main computer and your wife computer can be on green port on smoothwall that will get a 192.168.0.x address while your servers can be on orange and that would get a 192.168.20.x address and if you have any wireless router you would put them on purple and that would get a 192.168.30.x address.  then red port would be your outside connection coming from your cable modem.

that what I just said was a setup for smoothwall with 4 nic cards installed.

that is how I got my home network setup.


> **peekaboo said:**
> So do I have to separate issues here?
Can I not have my main computer connected to the internet through the server and still be able to access the web with 2 different ip addresses simultaneously?

---

### Post by peekaboo on 2009-07-17
My ISP supplies me with 2 IP addresses.
I use a switch and have 1 address sent to my phone adapter and 1 address sent to my router.
Can I install another NIC in my server and have it pull the 2 different IP addresses and then have different machines on my network present either of the 2 real world ip addresses according to my choosing? or have my network use either ip address at different times?

---

### Post by kustomjs on 2009-07-17
please tell me how 2 real world ip addresses can be on a one cable modem because I work for a local ISP as tech support and we deal with cable internet and far as I know cable internet only have 1 ip address with one cable modem. I could see 2 ip addresses if you had 2 cable modems but with one I dont see how that happens sorry.

its best that you setup smoothwall for your application.

---

### Post by peekaboo on 2009-07-17
I don't know how it's done. It just is.
My ISP is [Novuscom]("http://novuscom.net/"). I have an RJ45 socket in my wall to which I plug my Cat5 cable. The other end goes into my switch. If I connect two computer/devices to my switch, each has a different real world IP address. I do have to register the 2 mac addresses with my ISP that receive IP addresses.
I get 2 different IP addresses and 10 Mb download and upload. I love it.

I have no idea what you mean by smoothwall. do you mean this: [http://www.smoothwall.org/]("http://www.smoothwall.org/")?

---

### Post by kustomjs on 2009-07-18
yes I mean smoothwall.org and only problem your going to face is that your 2 IP addresses are dynamic and if your running a webserver on dynamic then you would need to get no-ip.com with smoothwall setup.

---

