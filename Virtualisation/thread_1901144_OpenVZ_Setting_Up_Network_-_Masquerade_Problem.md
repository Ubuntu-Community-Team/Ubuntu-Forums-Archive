---
title: "OpenVZ Setting Up Network - Masquerade Problem"
date: 2011-12-27
forum: Virtualisation
---

### Post by held7over on 2011-12-27
Debian 6 Host Node and Devian6-Ubuntu 10.04 VE Containers

This is just a basic OpenVZ venet network.

My Host Node 192.168.2.100 sets on my local network subnet 192.168.2.0/24 at home.

My HN (the actual hardware of the box) has only one physical connection device:  eth0

I have two freshly created containers which have a different subnet in the 192.168.3.0/24 range, just as the instructions I found said to use:
        CT-101 is 192.168.3.101
        CT-102 is 192.168.3.102

Right now, the HN can ping anything on the Internet, plus the HN can also ping both containers, and both containers can ping the HN.

However, my problem is, neither container can ping the other, nor can they ping anything on the Internet which means I can't add packages via apt-get.

I found these instructions for setting up Private VEs ( which are not directly visible from the LAN) which are to communicate through the HN's IP address on the LAN and they say:

        -To allow the VE to access the rest of the LAN we must
         enable forwarding and masquerading, as all activity on 
         the LAN must look like it is coming directly from the
         host (with its IP address).
            [host-node]# echo 1 > /proc/sys/net/ipv4/ip_forward
            [host-node]# iptables -t nat -A POSTROUTING -o eth0 -j 
                         MASQUERADE

Great! As this is what I wanted, BUT....this doesn't seem to work, as from within the containers I still can't access the Internet through the HN's subnet IP address or ping another container on the same subnet.

What do I need to do to get my network communications up and how do I do it???

Thanks!

---

### Post by bodhi.zazen on 2011-12-28
Easiest method is to assign the guests an ip on the same netmask as the host.

If you really want a separate subnet, see the openvz wiki

[http://wiki.openvz.org/Common_Networking_HOWTOs#Private_VEs_.28not_directly_visible_from_the_LAN.29](http://wiki.openvz.org/Common_Networking_HOWTOs#Private_VEs_.28not_directly_visible_from_the_LAN.29)

[http://wiki.openvz.org/VEs_and_HNs_in_different_subnets#Putting_containers_to_different_subnetworks](http://wiki.openvz.org/VEs_and_HNs_in_different_subnets#Putting_containers_to_different_subnetworks)

---

### Post by bodhi.zazen on 2011-12-28
*Thread moved to **Virtualization**.*

---

### Post by held7over on 2011-12-28
Thanks for responding bodhi.zazen.

Actually, I am all for simple, and I originally tried putting the guests on the same subnet first and got the same
problem. However, I just now re-did it, and put my guests again on the same subnet with my host node. Below is the
sequence of commands I used:

[host-node]# vzctl create 101 --ostemplate debian-6.0-amd64-minimal --config basic
[host-node]# vzctl set 101 --onboot yes --save
[host-node]# vzctl set 101 --hostname server101.xxxxxa.com --save
[host-node]# vzctl set 101 --ipadd 192.168.2.101 --save
[host-node]# vzctl set 101 --numothersock 120 --save
[host-node]# vzctl set 101 --nameserver 192.168.2.1 --save
[host-node]# vzctl start 101
[host-node]# vzctl exec 101 passwd

Then I did it for guest 102, and tested it:
# vzlist
      CTID      NPROC STATUS    IP_ADDR         HOSTNAME
       101          6 running   192.168.2.101   server101.xxxxxa.com
       102          6 running   192.168.2.102   server102.xxxxxb.com

I then ENTER-ed guest 102, and tried to ping openvz.org on the Internet....but no luck.
So, I EXIT-ed the guest and gave these commands again on the host node--

[host-node] #  echo 1 > /proc/sys/net/ipv4/ip_forward
[host-node] #  iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

I re-entered the guest and attempted to ping an address on the Internet--

root@server102:/# ping  openvz.org
^C
root@server102:/#

Maybe I have messed up my IPtables in all of this, but you would think if I had, my host node wouldn't be able to see the Internet either then...and it can. What do you think?

Thanks!

---

### Post by bodhi.zazen on 2011-12-28
Looks good, you do not need any special iptables configuration with openvz guests.

Enter the guest and run ifconfig

What kernel are you running and what host ?

What security do you have on your router ?

Can you ping one guest from the other ?

You can also try a network debugging tool

```
tracepath openvz.org
```

---

### Post by held7over on 2011-12-28
Answers:

**Enter the guest and run ifconfig:**

root@HostNode:~# vzctl enter 102
entered into CT 102
root@server102:/# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:420 (420.0 B)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.2.102  P-t-P:192.168.2.102  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

**What kernel are you running and what host ?**

root@HostNode:~# uname -r
2.6.32-5-openvz-amd64   <----debian on host node

Guest:
root@server102:/# uname -r
2.6.32-5-openvz-amd64   <----debian in Containers 101 & 102

**What security do you have on your router ?**

The router is a Linksys WRT54G/GL/GS running WW-DRT. 
My server machine is directly hardwired behind this router along with 3 other hardwired machines which are directly attached to the router's Ethernet Ports. 

The WW-DRT SPI Firewall on the router is enabled.

I have assumed that my Containers are communicating through my Host Node's Static IP Address, so, I have not tried to do anything with the router to recognize the Container's own unique Private IP numbers.

Under WAN REQUESTS, Block Anonymous WAN Requests (ping), Filter Multicast, and Filter IDENT (113) are enabled.

The WW-DRT driver on the router is pretty much in it's default state.

**Can you ping one guest from the other ?**

No, I can not ping another guest from within a guest. Nor can I ping the Host Node's gateway address 192.168.2.1


**You can also try a network debugging tool:**

root@server102:/# tracepath openvz.org
-bash: tracepath: command not found

root@server102:/# ip route show
192.0.2.1 dev venet0  scope link
default via 192.0.2.1 dev venet0  src 192.168.2.102

root@server102:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.0.2.1       0.0.0.0         255.255.255.255 UH    0      0        0 venet0
0.0.0.0         192.0.2.1       0.0.0.0         UG    0      0        0 venet0

root@HostNode:~# ip route show
192.168.2.102 dev venet0  scope link
192.168.2.101 dev venet0  scope link
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.100
default via 192.168.2.1 dev eth0

root@HostNode:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.102   0.0.0.0         255.255.255.255 UH    0      0        0 venet0
192.168.2.101   0.0.0.0         255.255.255.255 UH    0      0        0 venet0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by held7over on 2011-12-29
Ugh! 

It's my UFW firewall on my Host Node! I disabled it this morning, rebooted, checked the status that it was indeed disabled, and I was then able to ping from within the guest container both the internet and other guests! 

This was my first non-graphical firewall since my server is non graphical.....and I can't say that I know that much about it. I had given commands that I had found in an example that I hoped would transfer all port 80 and 443 traffic to my first guest for processing. Evidently, my efforts here had major unintended effects.

I really need to master Shorewall instead. What do you recommend a beginner wanting to learn to set up his own firewall in this area study in order to be able to accomplish these things? None of these firewalls that I have looked at seem to come with the education I need to really understand and utilize them...and I am kind of lost in this area...

Thanks!

---

