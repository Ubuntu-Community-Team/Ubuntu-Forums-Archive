---
title: "clc with single network interface"
date: 2011-05-18
forum: Ubuntu Cloud and Juju
---

### Post by madao-ansisup on 2011-05-18
i want to install uec in my network, but the problem is that all the machines i own have only a single network interface so i can't install cloud controller that to have at least 2.
is there a solution for me to install uec without buying another machine because i'm a student and i don't have much resources and i need uec for my project .
thanx in advance

---

### Post by kim0 on 2011-05-19
hmm, you could simply buy another NIC (network card) no need for a full machine. I'm not sure if you can configure with a single nic only. Another option might be to try OpenStack which can run fine on a single machine (or even inside a VM). Starting 11.04, OpenStack is shipping with Ubuntu

---

### Post by madao-ansisup on 2011-05-21
ok, so untill i get my hands on a new NIC iwant to test ubuntu 11.04 on a single machine, is there a guide on how to do it??

---

### Post by Rusty au Lait on 2011-05-21
My UEC runs on only one nic per machine. Setting up a bridge allows everyone to avoid each other.

Granted, I do not allow access to the network from anywhere outside save one. Me.

---

### Post by lemon1707 on 2011-05-24
> **Rusty au Lait said:**
> My UEC runs on only one nic per machine. Setting up a bridge allows everyone to avoid each other.

Granted, I do not allow access to the network from anywhere outside save one. Me.

Hi Rusty au LAit,
Could you talk more detail how to setup UEC runs on only one nic per machine. I need to create EBS to attact to VMs running. That make me setup UEC on 2 machine, and I have same problem with madao-insisup. I had installed many times and VMs doesn't work correctly ( It can not conect internet directly ...).

---

### Post by Rusty au Lait on 2011-05-24
I made a few assumptions about your setup.

One way you would have a problem running uec with only one nic is that you only have one IP address per machine to work with.

If that is your situation you can ask your system administrator to assign you a block of unused IP addresses. You would then instruct UEC to use that block for all your instances.

If you have one and only one IP address to work with you will have to use a router. Even your second machine will not have an IP address.

What is your network arrangement?

---

### Post by lemon1707 on 2011-05-27
Hi Rusty, Thank for your reply and I'm sorry for the delay replying to you.
My UEC configuration : I deploy UEC on 2 machines ( Dell Studio 1555 and the other id Dell Studio 1558 ), each machine just have one nic.
[B]+ On Cluster
/etc/eucalyptus/eucalyptus.conf[/B]

 VN_PUBINTERFACE = "eth0"
 VN_PRIINTERFACE = "eth0"
 VN_BRIDGE = "br0"
 VNET_MODE="MANAGE-NOVLAN"
 VNET_DNS="192.168.1.1"
 VNET_PUBLICIPS="192.168.1.100-192.168.1.200"

 **/etc/network/interfaces**
 auto lo
 iface lo inet loopback

 auto eth0
 iface eth0 inet manual

 auto br0
 iface br0 inet static
        address 192.168.1.35
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0


[B]+ On Node Controller 
 /etc/eucalyptus/eucalyptus.conf[/B]

 VN_PUBINTERFACE = "br0"
 VN_PRIINTERFACE = "br0"
 VN_BRIDGE = "br0"
 VNET_MODE="MANAGE-NOVLAN"

 **/etc/network/interfaces**
 auto lo
 iface lo inet loopback

 auto eth0
 iface eth0 inet manual

 auto br0
 iface br0 inet static
        address 192.168.1.34
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
 

 **My Problem is:**
 When I run image with Hybridfox, the instance have 2 IPs : public 192.168.1.100, private 172.19.1.2. 
The instance is always running state and I can Ping 192.168.1.100 from  the other computer, but I can not Remote Desktop Connection to the instance ( I enabled the remote desktop for image when I bundle It and open port to RDP).
 Could you correct the configuration for me or give me any solutions? I really need your help because I don't have more time to finish my thesis.
If you have any infomation, please contact with me by email [EMAIL="lemon1707@gmail.com"]lemon1707@gmail.com[/EMAIL]

---

