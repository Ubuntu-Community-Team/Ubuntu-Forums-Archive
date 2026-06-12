---
title: "Port Forwarding Issues"
date: 2017-07-27
forum: Virtualisation
---

### Post by gordonmoore on 2017-07-27
This might take a while to explain, but the TLD:DR is as follows.

[I]I'm trying to setup port forwarding so that I can access some services while I am away from home.  The forwarding seems to work fine for every host in my local lan EXCEPT for host that are virtual machines on my KVM server.
[/I]
The details.

KVM Server - Setup with a single bridge (br0) interface.  
KVM Guests - VM's that get spun up receive an IP address from DHCP that is part of the local network (192.168.1.0/24) 
Laptop - I am able to ping / ssh into any of VMs using their IP address that they receive from DHCP
Router - The KVM guest appear in the client table

Testing -


1. I can ssh from my laptop to any KVM guest

2.  When I setup port forwarding on my router to any IP address except the KVM guest, the ports are forwarded correctly.

3. When I try to ssh remotely 

```
ssh user@publicIP -P external port
``` I get a connection time out.

4. When I run tcpdump on the guest VM that I am trying to ssh into... I can see the syn packet, with the correct source (external ip) and destination (VM guest IP, correct MAC address as well).. but the guest VM does not respond to the SYN packet.

5. Doing an nmap on the public ip address shows the external port as 'filtered' (which matches well with the behavior described in test 4)

6. I am certain firewalld is not running on the guest VM.

Any other thoughts!??

---

### Post by papibe on 2017-07-27
Hi gordonmoore.

> **gordonmoore said:**
> 3. When I try to ssh remotely 

```
ssh user@publicIP -P external port
``` I get a connection time out.
Is this test actually being done remotely? or is it from the same LAN?

Regards.

---

### Post by gordonmoore on 2017-07-28
> **papibe said:**
> Hi gordonmoore.


Is this test actually being done remotely? or is it from the same LAN?

Regards.

Interesting distinction.  I was actually testing from within my own network... but I just tested from "actually outside" and I experience the same behavior... ssh  fails (although SYN port 22 packets make it to the client VM), but ssh works for all non VM hosts.

---

### Post by papibe on 2017-07-28
OK, thanks.

Unless your router supports NAT loopback, you can't go from inside your network and reach your own public IP.

Does it work, just inside your network? that is, from LAN IP to LAN IP? can you reach your KVM guests?

Regards.

---

### Post by gordonmoore on 2017-07-29
> **papibe said:**
> OK, thanks.

Unless your router supports NAT loopback, you can't go from inside your network and reach your own public IP.

Does it work, just inside your network? that is, from LAN IP to LAN IP? can you reach your KVM guests?

Regards.

I can reach my KVM guests just fine form LAN IP to LAN IP.  

Whether I am inside our outside of my network, and use my public IP address... I am able to successfully connect (via port forwarding) to any host that is NOT a KVM guest.

Basically.. if I setup the port forwarding rules to have external port 53535 -> KVM host on 22... when I do 

```
ssh user@publicIP -p 53535
```

That will work.  But if I change the port forwarding rules to port 53535 -> KVM guest on 22.. then the exact same command

```
ssh user@publicIP -p 53535
``` 

fails.

---

### Post by TheFu on 2017-07-30
Use static IPs for the KVM hosts.
The KVM hosts should be on the same subnet as all the non-KVM machines.

This stuff sorta just works then.  Not that it matters, but I've always done **ssh  -p 53535 user@publicIP**. If you look at the manpage, there is an order for arguments with the user@host last unless there is a command to be run on the remote system.

---

### Post by gordonmoore on 2017-07-31
> **TheFu said:**
> Use static IPs for the KVM hosts.
The KVM hosts should be on the same subnet as all the non-KVM machines.

This stuff sorta just works then.  Not that it matters, but I've always done **ssh  -p 53535 user@publicIP**. If you look at the manpage, there is an order for arguments with the user@host last unless there is a command to be run on the remote system.

The KVM hosts are all on the same subnet, and instead of static IPs.. I have reserved DHCP leases based on MAC address... because I dynamically create a lot of VMs and it helps when I know which IP address each VM will get assigned ahead of time.
 
Everything connects fine locally.. the only issue arrises when I try to login externally through my router via forwarded parts.

---

### Post by TheFu on 2017-07-31
Are the KVM guests on the same subnet as the hosts?
What do the log files say for ssh connections?  Is the connect even getting that far?
What does the verbose ssh client connection show?
**ssh -vvv -p 53535 user@publicIP**

What do the router logs show?

---

### Post by gordonmoore on 2017-07-31
> **TheFu said:**
> Are the KVM guests on the same subnet as the hosts?
What do the log files say for ssh connections?  Is the connect even getting that far?
What does the verbose ssh client connection show?
**ssh -vvv -p 53535 user@publicIP**

What do the router logs show?

[B]Are the KVM guests on the same subnet as the hosts?
[/B]
They are Vagrant provisioned VMs.  They have two interfaces

eth0 --> used by Vagrant.. on the 192.168.121.0/24 subnet.. and only used by vagrant
eth1 --> used by me, on the 192.168.1.0 subnet, same subnet as everything else on my LAN (including the KVM server), default route of 192.168.1.104 (my router), they get their IP from DHCP

[B]What do the log files say for the ssh connection
[/B]
It is not getting that far, nothing in the ssh/auth/secure logs. The only evidence I see of my attempt to ssh, is when I run tcpdump -i eth1 dst port 22 .... in which case I see the TCP SYNs being sent from a source address (the public IP) to the destination address (IP address of the guest VM I'm trying to connect to).. but the connection never gets established.  This also happens when trying to connect to a web server I have running on different port.. I see the SYNs.. but not able to connect.  

```

tcpdump -i eth1 dst port 22 and src 11.11.11.11
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
14:51:02.610222 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196254597 ecr 0,sackOK,eol], length 0
14:51:03.611914 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196255597 ecr 0,sackOK,eol], length 0
14:51:04.629748 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196256597 ecr 0,sackOK,eol], length 0
14:51:05.631286 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196257597 ecr 0,sackOK,eol], length 0
14:51:06.632037 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196258597 ecr 0,sackOK,eol], length 0
14:51:07.647499 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196259598 ecr 0,sackOK,eol], length 0
14:51:09.649383 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196261598 ecr 0,sackOK,eol], length 0
14:51:13.681831 IP c-11.11.11.11.hsd1.comcast.net.64206 > director.localdomain.ssh: Flags [S], seq 1170990294, win 65535, options [mss 1460,nop,wscale 5,nop,nop,TS val 196265598 ecr 0,sackOK,eol], length

```
[B]
What does the verbose ssh client connection show?

[/B]```

ssh root@11.111.11.11 -p 53536 -vv                                                                                                                             
OpenSSH_7.4p1, LibreSSL 2.5.0
debug1: Reading configuration data /Users/myname/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: resolving "11.11.11.1" port 53536
debug2: ssh_connect_direct: needpriv 0

debug1: Connecting to 11.11.11.11 [11.11.111.11] port 53536.
ssh: connect to host 11.11.11.11 port 53536: Operation timed out

```

---

### Post by TheFu on 2017-07-31
Looks like a router issue - whoa - you are trying to connect as root and using that account works locally?  Ubuntu doesn't allow remote root connections by default. Did you fix that everywhere it is needed?

Easier to use a different account.

Also ... do me a favor and **always** put the user@IP as the last part of the ssh command. This is how the manpage shows it.

I'm on a comcast biz connection and use their router in bridge-only mode for my public subnet. My pf router handles the 172.x.x.x --> 50.x.x.x --> 172.x.x.y ssh connections no problem. I've used openwrt/dd-wrt and tomato similarly.  I can connect on the LAN or over the WAN interface without issue.  Never remember having any issues.  I only allow direct ssh into 1 VM and 1 host.  From those, I can jump almost anywhere else on the network across 3 subnets that are managed by my router.

To deal with odd ports, I use the ~/.ssh/config file.  Makes remembering which port is needed for which host for any libssh commands unnecessary.  Every tool that uses libssh automatically uses the config file - userid, real IP/hostname, port and other connection settings in that file.

I do not use root logins on any of my Ubuntu systems.  Remote root is disabled by default.

---

### Post by gordonmoore on 2017-07-31
> **TheFu said:**
> Looks like a router issue 


Hmm... I was thinking it wasn't a router issue because when I setup the port forwarding to forward to any other machine on my network that is not a KVM guest machine.. it works fine.  Plus.. as TCP Dump shows.. the packets are making it to the guest VM... so I think it is a routing / config issue  either on the KVM Host or the KVM Guest.

> 
you are trying to connect as root and using that account works locally?


Yes... all of these VMs are automatically provisioned and enabling ssh root login is part of the bootstrap process (these are VMs for Development purposes)

> 
Also ... do me a favor and **always** put the user@IP as the last part of the ssh command. This is how the manpage shows it.


Ok.  I'll be sure to put the the user@IP last from now on :-)

---

### Post by TheFu on 2017-07-31
Guess your IP search and replace is confusing me. Sorry.

Perhaps if you post the routing table for the client and the server you are hoping to connect?

---

### Post by gordonmoore on 2017-07-31
> **TheFu said:**
> Guess your IP search and replace is confusing me. Sorry.

Perhaps if you post the routing table for the client and the server you are hoping to connect?

Glad to!

From the KVM Server

```
root@kvmServer:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.104   0.0.0.0         UG    0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.121.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr1
```

From the KVM Guest
```
root@kvmGuest ~]# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.121.1   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.1.104   0.0.0.0         UG    101    0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth1
192.168.121.0   0.0.0.0         255.255.255.0   U     100    0        0 eth0
```

---

### Post by TheFu on 2017-07-31
```

0.0.0.0         192.168.121.1   0.0.0.0         UG    100    0        0 eth0
```
is an issue. There may still be others.  That route has a higher priority than the gateway you want, 192.168.1.104. If you don't need to access anything outside the 192.168.121.0/24 network via eth0, then you don't need any gateway setup.  Best to just remove it.

---

### Post by gordonmoore on 2017-07-31
> **gordonmoore said:**
> Glad to!

From the KVM Server

```
root@kvmServer:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.104   0.0.0.0         UG    0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.121.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr1
```

From the KVM Guest
```
root@kvmGuest ~]# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.121.1   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.1.104   0.0.0.0         UG    101    0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth1
192.168.121.0   0.0.0.0         255.255.255.0   U     100    0        0 eth0
```

Ugh... So I got it to work! (finally)

After staring at the 2nd routing table.. I figured I'd remove the first default route because I didn't want it being used.. and thought maybe that the overlapping default routes might cause problems even though they are using different interfaces..

So once I remove the first line in the KVM guests routing table.. everything works.

Thanks all!

---

