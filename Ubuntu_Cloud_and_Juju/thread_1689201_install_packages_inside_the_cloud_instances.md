---
title: "install packages inside the cloud instances"
date: 2011-02-16
forum: Ubuntu Cloud and Juju
---

### Post by selvawithcommunity on 2011-02-16
hi my frineds,

by your help i successfully setup the private cloud and i can login in to the cloud instances as ubuntu user..

now i want to run the simple web application called compiler on the cloud instances..

so i need to run the apache server inside the cloud instance(ubuntu 10.04 server).. i downloaded ubuntu image from ubuntu store.(this is not GUI. fully command orineted)

_**questions:**_

**1. in the cloud image there is no apache server(lamp server) available. and i try to download from the tasksel using apt-get method.. but apt-get method not working for me. how to make apt-get metod working?** when i am trying the apt-get method it shows as: 
ubuntu@ip-172-19-1-2:~$ sudo tasksel install lamp-server
sudo: unable to resolve host ip-172-19-1-2
tasksel: aptitude failed (100)

2.** actually my instances ip i allocated is 10.1.7.105. but it shows the ip address is 172.19.1.2. so how to access apache server using  ip address whether 10.1.7.105 or 172.19.1.2?**

3[B]. i cannot ping the ip address 10.1.7.105( where the cloud instances is running.) from the ip 10.1.7.104(node controller running) but inside the cloud instance i can ping the ip address 10.1.7.1(proxy server) and 10.1.7.103(CC,CLC,SC is running ) and 10.1.7.104(node controller is running) . what i have to do? 
[/B]
_**INFORMATION:**_

my proxy server IP:10.1.7.1
a. my cloudcontroller,cluster controller, storage controller run on the IP:10.1.7.103

b. my node controller running on the IP:10.1.7.104 (here i can use apt-get method to download package by specifying the proxy setting in the SYSTEM->ADMINSTRATION->NETWORK PROXY)

c. my cloud instances(this UBUNTU SERVER is not having GUI. fully command orineted) running on the IP:10.1.7.105? 

d. i am Put the following into your /etc/bash.bashrc file. eventhough apt-get not working.
export http_proxy=http://10.1.7.1:8080/

e.** i opened the ports 22,23,80 using the following commands:**
euca-authorize default -P tcp -p 22 -s 0.0.0.0/0[FONT=Verdana]
[/FONT]euca-authorize default -P tcp -p 23 -s 0.0.0.0/0
euca-authorize default -P tcp -p 80 -s 0.0.0.0/0

f. **my netstat command output**

ubuntu@ip-172-19-1-2:~$ **netstat -a**
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0     48 172.19.1.2:ssh          10.1.7.104:42796        ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
udp        0      0 *:bootpc                *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     1038     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    1144     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     2456     /var/run/dbus/system_bus_socket
unix  4      [ ]         DGRAM                    2784     /dev/log
unix  2      [ ]         DGRAM                    3638     
unix  3      [ ]         STREAM     CONNECTED     3273     
unix  3      [ ]         STREAM     CONNECTED     3272     
unix  3      [ ]         STREAM     CONNECTED     2873     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     2872     
unix  3      [ ]         STREAM     CONNECTED     2848     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     2847     
unix  3      [ ]         STREAM     CONNECTED     2835     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     2834     
unix  2      [ ]         DGRAM                    2833     
unix  3      [ ]         STREAM     CONNECTED     2475     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     2474     
unix  3      [ ]         STREAM     CONNECTED     2461     
unix  3      [ ]         STREAM     CONNECTED     2460     
unix  3      [ ]         DGRAM                    1147     
unix  3      [ ]         DGRAM                    1146     
unix  3      [ ]         STREAM     CONNECTED     1127     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     1126     



ubuntu@ip-172-19-1-2:~$** netstat -ta**
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0     48 172.19.1.2:ssh          10.1.7.104:42796        ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN    



ubuntu@ip-172-19-1-2:~$ **netstat -r**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.19.1.0      *               255.255.255.224 U         0 0          0 eth0
default         172.19.1.1      0.0.0.0         UG        0 0          0 eth0

g.** MY _ifconfig_ output is **

ubuntu@ip-172-19-1-2:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr d0:0d:4a:24:08:7d  
          inet addr:172.19.1.2  Bcast:172.19.1.31  Mask:255.255.255.224
          inet6 addr: fe80::d20d:4aff:fe24:87d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:666166 (666.1 KB)  TX bytes:76640 (76.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8360 (8.3 KB)  TX bytes:8360 (8.3 KB)
[B]
h. my network interface [/B]**_ /etc/network/interfaces_**** containg**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
**help me frineds. thank you...**

---

### Post by Rusty au Lait on 2011-02-16
Here's my $0.02,
Ignore the 172.19.1.0 network.

You are not using a bridge. Good or bad? I don't know. I do not work with a proxy. What Eucalyptus network node are you using? (System, static, managed, or novlan)

At the very least, from the CLC (.103) if you get a ping response from the NC server (.104) then you should be able to get a ping response from the instance (.105). The instance may not respond to pinging.

Can you ping yahoo.com (or any outside server) from the instance?

When you do get apache loaded into your instance you will access it through the 10.1.7.105 IP address.

Why do you set your instances's ip address so close to your servers? You should use a range of ip's seperate from your servers ip range. What will the second NC server's address be? What will the second instances's ip address be?

I believe all your instances's ip traffic still goes through the CL server (.104). Are your iptables setup?

Ciao

---

### Post by kim0 on 2011-02-17
Indeed I think all traffic goes thru CLC, so you need to setup iptables for masquerading

---

### Post by selvawithcommunity on 2011-02-17
i am using MANAGED-NO VLAN and  
i didn't setup any iptables for masquerading.

---

### Post by raymdt on 2011-02-18
Hi,
we have already resolved this issue here. Please use the search function to find the Post.

It is something like
```

echo 1 > /proc/sys/net/ipv4/ip_forward
sudo iptables -P FORWARD ACCEPT
sudo iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

```

---

