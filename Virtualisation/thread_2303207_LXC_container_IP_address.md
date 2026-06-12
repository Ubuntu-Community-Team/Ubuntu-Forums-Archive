---
title: "LXC container IP address"
date: 2015-11-17
forum: Virtualisation
---

### Post by bobk48 on 2015-11-17
I install and run a new container on Ubuntu 15.10, with the ubuntu template, according to the excellent instructions here-
[www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/]("http://www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/")
and my home network does not see the IP address that is given by default, something like 10.0.3.1.
I have Googled how to set the bridged connection up so that I can access the container from my home network, 
but many of the instructions are either vague, or incomplete. It seems to me that such an elementary operation 
such as this, using the ubuntu template, should be very well documented, but I don't find that is true. 
After all, one of the primary purposes of deploying a container is to secure your computer by isolating specific
network traffic so that it only goes to the container.
Can anyone either point me to a direct, articulate, and applicable set of instructions that achieves connecting
the container through the host to my home network. 
Thanks!
Sincerely,
Robert M. Koretsky

---

### Post by TheFu on 2015-11-18
[https://askubuntu.com/questions/370599/forward-port-to-lxc-guest-using-ufw](https://askubuntu.com/questions/370599/forward-port-to-lxc-guest-using-ufw)

---

### Post by bobk48 on 2015-11-18
Thanks for your reply! Interesting solution, but with not many details of how to actually achieve it in the simplest, and most articulated way! If I mess with ufw or iptables, which was suggested in a few other solutions I explored before posting this, there is way more material in those facilities than would be needed in a quick fix to the problem. Not that I am not up to thoroughly looking at ufw and iptables, believe me I am! 
Initially looking at iptables, if I preroute, or port forward, port 22 on the host to send to port 22 on the LXC guest, is port 22 on the host no longer accessible? I will look at this first, and then see if I can do a ufw solution too.

The reply to this post by TheFu does not work, such as-
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 22 -j DNAT --to 10.0.3.1:22

so iptables and ufw are out for me. Furthermore, LXC user mailing list participants gave explanations of how to solve the problem that are not specific enough. In the last 2 days I've spent a lot of spare time trying various approaches to bridging lxcbr0 to my my hardware NIC, with no workable results. All the online postings of how to hook an lxc container to a network other than the subnet it is by default connected to when created lead nowhere, at least for me. Very frustrating. Without being able to face the container to my network, lxc containers are useless.

---

