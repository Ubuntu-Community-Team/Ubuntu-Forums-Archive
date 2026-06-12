---
title: "Help with implementing NAT64 with Tayga or Ecdysis?"
date: 2013-11-06
forum: Server Platforms
---

### Post by abradatanu on 2013-11-06
Hello
My name is Alex and I am doing my final year university project about IPV6 transition technologies and I would like to test/implement NAT64/DNS64 using either Tayga or Ecdysis, but I cannot wrap my head around how it works :)
A diagram of what I’m trying to achieve is attached
 
What I want to simulate is a v6 only host going through the tayga server which translates the v6 address of the pc to v4 and then through the cisco router which then can ping or access the “ISP’s” v4 address

Is this the correct topology that would allow me to do this?

My “internal” cisco router is a normal NAT44 router with inside interface 172.16.1.10/24 and outside interface 63.1.1.1/30 (outside interface connects to ISP router 63.1.1.2/30). The PC with tayga on it has one interface statically assigned 172.16.1.2 and can ping the ISP router 63.1.1.2 which shows up with source address of internal router meaning my NAT44 work correctly.

Now from what I understand I need to configure the other interface of the PC/tayga server with an IPv6 address and I chose 2001:abcd:1:1::1/96. I also need to give the IPv6 only PC an address and I gave it 2001:abcd:1:1::2/96 and default gateway of 2001:abcd:1:1::1/96

I compiled and installed tayga and I’m confused when I have to edit the tayga config file:

tun-device nat64
ipv4-addr 172.16.1.2                                    **should this be the PC’s v4 address of 172.16.1.2 ? **
prefix 2001:abcd:1:1::/96                             **should this be my 2001:abcd:1:1::/96 prefix ?**
dynamic-pool 10.1.1.0/24                              **can I use this pool of addresses?**
data-dir /var/db/tayga
 
# tayga --mktun
# ip link set nat64 up
# ip addr add x.x.x.x dev nat64                      **in my case what is this address supposed to be? (my cisco router’s ipv4 address?)**
# ip addr add 0:0:0:0:0:0:0:0 dev nat64           **in my case what is this address supposed to be? (my cisco router’s ipv6 address?)**
# ip route add 172.16.1.0/24 dev nat64           **Is this correct?**
# ip route add 2001:abcd:1:1::/96 dev nat64   **Is this correct?**
# tayga
 
From what I understand tayga is stateless so it should map the ipv6 address of the v6 only PC to an ipv4 address from the dynamic pool specified and then use that v4 address to reach the v4 internal cisco router and then the ISP one. Am I correct or have I got this completely the wrong way?

I know I’m doing something wrong, but just don't know what :)

Any help would be greatly appreciated  and I wish to thank you for taking the time to read my gibberish and thank you in advance for any advice and help
Alex

---

### Post by koenn on 2013-11-06
haven't done IPv6 yet myself, but i'd guess the answers to your questions are in the super-quick-start in this page : [http://www.litech.org/tayga/](http://www.litech.org/tayga/)

oh, and I can't see your attached diagram.

---

