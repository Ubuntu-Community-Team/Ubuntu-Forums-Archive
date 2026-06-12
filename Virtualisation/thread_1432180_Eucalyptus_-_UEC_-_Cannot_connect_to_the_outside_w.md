---
title: "Eucalyptus - UEC - Cannot connect to the outside world from the VM-instances"
date: 2010-03-17
forum: Virtualisation
---

### Post by l3golas on 2010-03-17
Hello,

I have set a private cloud using Eucalyptus, my configuration is a frontend and 2 nodes. I started from the frontend 2 virtual machines that have Ubuntu on them. They have respectively addresses 172.19.1.2 and 172.19.1.3. I connect to each VM through SSH with no problems. Into the VM, it seems to see only the internal network, and not outside: I mean I can ping the other VMs but not external addresses, like [www.google.com](www.google.com) or 8.8.8.8 (Google DNS). I think it's not normal. How can i connect to outside (for example to update my Ubuntu in my VM)? 
I add another info: if I log into the node (not the VM) I'm able to connect to Internet, the problem is from inside the VM, it can't access the Internet... I read somewhere here on the forum that I should have a look at the firewall and NATting configuration of the front-end, because it may prevent unknown IPs from going out. But how can I do that (which commands)? Is it related to iptables?
Thanks in advance,

l3golas

---

### Post by bmullan on 2010-05-15
> **l3golas said:**
> Hello,

I have set a private cloud using Eucalyptus, my configuration is a frontend and 2 nodes. I started from the frontend 2 virtual machines that have Ubuntu on them. They have respectively addresses 172.19.1.2 and 172.19.1.3. I connect to each VM through SSH with no problems. Into the VM, it seems to see only the internal network, and not outside: I mean I can ping the other VMs but not external addresses, like [www.google.com](www.google.com) or 8.8.8.8 (Google DNS). I think it's not normal. How can i connect to outside (for example to update my Ubuntu in my VM)? 
I add another info: if I log into the node (not the VM) I'm able to connect to Internet, the problem is from inside the VM, it can't access the Internet... I read somewhere here on the forum that I should have a look at the firewall and NATting configuration of the front-end, because it may prevent unknown IPs from going out. But how can I do that (which commands)? Is it related to iptables?
Thanks in advance,

l3golas

One thing I found was the netmask of my VMs was different from my local network.

My local net is a 192.168.1.x 255.255.255.0 
The VMs were created with a 192.168.1.x 255.255.255.255 

So the VMs can't talk outside of their subnet which is behind the Bridge br0.

My suspicion is this is related to a feature read about in the UEC Enterprise Cloud Architecture document in the section titled NETWORKING.

UEC has [**3 possible networking modes**]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.ubuntu.com%2Fsystem%2Ffiles%2FUbuntuEnterpriseCloudWP-Architecture-20090820.pdf&ei=qB_vS5yjIoO88gbm6uX9Cg&usg=AFQjCNF_86QBrU-ZavDxaqghkxQcNY34Sw&sig2=hIvYZPcLOXI_hDFA2IpNIQ") you can configure for the VMs.

SYSTEM mode
STATIC mode
MANAGED mode

In the description of Managed Mode they mention that the UEC admin defines the network usually private **and unroutable**

That's what I think might be getting setup but I've not had time to check my own UEC setup yet.

---

### Post by wcorey on 2010-05-16
I am not sure this will be helpful but I had a world of trouble getting networking to work, to the extent I am still not sure it works correctly but let me explain. 

I did something a little different as I have one node and everything else on a Lucid Desktop system upgraded from a Karmic Desktop system.

The main problem I had was in the public addresses: I thought, during installation I could simply give the cluster controller install Q&A a series of addresses about what I was using, i.e. 192-168-0.1->255. This did not work but not clear why as I could ssh into the instance on the private address but not with the public one. I believe the cluster controller starts a dhcpd to manage the private address range, this is in the 172.13.1.xxx-> range. The public addresses are in the domain of your router. My was set for strictly the 192.168.0.xxx range. My next step was to give the install the 192.168.1.xxx range of addresses to use. I then discovered the router issue and expanded it to include 192.168.0.000-> 192.168.1.255. Then I could get in via the public addresses and get to the outside world from public as well. 

It is not clear to me if the public address given on describe instances is intended to be an elastic IP or simply the dns name. I believe from their wording it is the later. I thought, however, from the private addresses that it was not supposed to have access out of the subnet. 

One thing I found odd is that to get things to work I had to do a complete removal of the cluster packages and reload, otherwise it didn't install correctly. Remember, my front end was an upgrade not a fresh install. 

The default for UEC is managed-novlan.

HTH.

---

