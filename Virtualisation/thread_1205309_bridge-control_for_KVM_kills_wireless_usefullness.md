---
title: "bridge-control for KVM kills wireless usefullness"
date: 2009-07-05
forum: Virtualisation
---

### Post by freakalad on 2009-07-05
Before starting this thread, I have to note that bodhi.zazen is doing some REALLY phenomenal work in this forums, but some of these issues seem to be inherent in the implementation. 
Check out his blog @ [http://blog.bodhizazen.net](http://blog.bodhizazen.net) for more info

The problem I've got, is that I'm able to run KVM on my laptop (MBP SR 3.1 is VT-capable), which works OK if I have a "standard" config of br0 bound to eth0, but doing this leaves my wlan0 WiFi interface out of the loop.
I can hook wlan0 into the br0 too, but this is a largely futile exercise, as the NetworkManager becomes useless once you start using static bridging, and I can't snarf AP's, authenticate or connect, nor get DHCP leases.

OTOH, the basic config of Virt-Manager allows for the "connect to any available physical interface", which is a pretty nifty trick, but it achieves this via a network-NAT configuration, which is problematic in it's own right.

I'll be happy to keep the eth0 IP static & manipulate it via the interfaces config file (yes, I know I can specify DHCP instead of a static address), but the wireless I'd like to manage through some user-friendly interface (it IS a desktop environment after all), including seeing what AP's are available & requesting connections & DHCP's

Has anyone dealt with this issue, or have some sort of way to address this?

Cheers

- J

---

