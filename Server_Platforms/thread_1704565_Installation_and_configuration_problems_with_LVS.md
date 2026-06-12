---
title: "Installation and configuration problems with LVS"
date: 2011-03-10
forum: Server Platforms
---

### Post by tranen on 2011-03-10
Hi,

I try to install LVS and for the moment I get some problems
First how I can know if ipvs & ipvsadm are installed correctly?
I read that ipvs on linux is already install so it's no need to patch the kernel.
Then I do these commands in this order:

To know if ipvs module is already in the kernel do: 
#lsmod | grep ip_vs
ip_vs 94528  0 

$ yum install ipvsadm 
Setting up Install Process
No package ipvsadm available.
Nothing to do

$ apt-get install ipvsadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ipvsadm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.

Check that ipvsadm detects the kernel patches:
#ipvsadm
->IP Virtual Server version 1.2.1 (size=4096)
Prot LocalAddress:Port Scheduler Flags
  -> RemoteAddress:Port           Forward Weight ActiveConn InActConn

$ rpm -q ipvsadm
package ipvsadm is not installed

As you can see I have different answer about the installation of ipvsadm.
Which one is correct?

Then in my configuration I have 1 load balancer with the address 192.168.1.x
2 real servers : 192.168.1.x
I don't have IP for the Virtual IP address.
I would like to know if I need an IP that it's exist or if for example I can choose an IP like 192.168.0.x and use it?
For the moment I did like this but my real server can't ping the VIP
I'm in the NAT configuration.

My configuration is like this:
For the Load balancer
#!/bin/bash
echo "1" > /proc/sys/net/ipv4/ip_forward
sysctl -p
/sbin/iptables -F -t nat
/sbin/iptables -F INPUT
/sbin/iptables -F FORWARD
/sbin/iptables -F OUTPUT
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
ifconfig eth0:0 192.168.0.x netmask 255.255.255.0 broadcast 192.168.0.255 up
ipvsadm -C 
ipvsadm -A -t 192.168.0.x:80 -s rr
ipvsadm -a -t 192.168.0.x:80 -r 192.168.1.x1 -m 
ipvsadm -a -t 192.168.0.x:80 -r 192.168.1.x2 -m 
ipvsadm -l 

For the real server
iptables -F INPUT
iptables -F FORWARD
iptables -F OUTPUT
route add default gw 192.168.0.x

Can you tell me where is my mistake?
Thanks

---

