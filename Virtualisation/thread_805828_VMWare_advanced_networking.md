---
title: "VMWare advanced networking"
date: 2008-05-24
forum: Virtualisation
---

### Post by sveinh on 2008-05-24
Hi all

I have some questions I hope you can help me with.

[IMG]http://www.nievs.com/bucket/vmware-setup.jpg[/IMG]

The questions I have is security related on how to set this up on vmware server.

Requirements / wishes:
1) I would like vm3 and vm4 to be able to get their ip addresses from the isp dhcp server. 
2) eth1 should not accept any trafic from the internet (it already runs sshd,httpd, which should only be available on eth0
3) If a user has shell access to vm3 or vm4, this user should not have network access to the host or any other machines on the internal network.

Does anyone have any ideas on how I can accomplish this? How would I configure the host-machine? How would I define networking in vmware server?

I'm running Ubuntu 8.04 on the host, vmware server 1.05 on the host. vm1..4 should run Ubuntu 8.04 also.

In advance, thanks for any input.

-sveinh

---

### Post by bradmkjr on 2008-05-24
Very nice diagram, without it I doubt you would get any answers.

VM3 and VM4 should be using bridge networking to eth1.
VM1 and VM2 should be using bridge networking to eth0 or VM3 and VM4 could be using nat networking to eth1, but I think bridge would better serve you, it makes them much easier to access on the local network the could be .0.14 and .0.15.

I hope you have the isp allowing you to get 4 public ips. 1 for the nat, 1 for eth1 and 1 for vm3 and 1 for vm4?

> 2) eth1 should not accept any traffic from the internet (it already runs sshd,httpd, which should only be available on eth0

what you mean to say is.. sshd, httpd should not be accessible on eth1 from the internet, you could say this: port 22 and 443 only allow from 192.168.*.*? that would disallow internet access to those two ports, which are your services of concern. I don't think it is possible to "not accept" traffic from the internet as you want the VMs to be able to receive traffic from the  internet. this should be doable either as a firewall rule or part of the configuration of the services depending on your preference.

> 3) If a user has shell access to vm3 or vm4, this user should not have network access to the host or any other machines on the internal network.

simple, give them shell accounts on the VM. they don't need any account on the vm host or the other machines, if they can ssh into the actual vm then that part is secure.

Hope this jumpstarts a good discussion,
Bradford Knowlton
[http://x86v.com/](http://x86v.com/)

---

### Post by sveinh on 2008-05-24
[QUOTE=bradmkjr]Very nice diagram, without it I doubt you would get any answers.
[/QUOTE]
Thanks, I hoped it was useful. It's quite difficult to discuss these things without a diagram :-)

[QUOTE=bradmkjr]
VM3 and VM4 should be using bridge networking to eth1.
VM1 and VM2 should be using bridge networking to eth0 or VM3 and VM4 could be using nat networking to eth1, but I think bridge would better serve you, it makes them much easier to access on the local network the could be .0.14 and .0.15.
[/QUOTE]
After installing nic #2 and ran vmware-config, it created a new bridge on vmnet2. For VM3 and VM4 I configured to use the new bridge.

[QUOTE=bradmkjr]
I hope you have the isp allowing you to get 4 public ips. 1 for the nat, 1 for eth1 and 1 for vm3 and 1 for vm4?
[/QUOTE]
I was also curious about this, but they did :-) I'm now getting 4 public ips from their dhcpd. Great stuff :-)


[QUOTE=bradmkjr]
what you mean to say is.. sshd, httpd should not be accessible on eth1 from the internet, you could say this: port 22 and 443 only allow from 192.168.*.*? that would disallow internet access to those two ports, which are your services of concern. I don't think it is possible to "not accept" traffic from the internet as you want the VMs to be able to receive traffic from the  internet. this should be doable either as a firewall rule or part of the configuration of the services depending on your preference.
[/QUOTE]
You are correct, what I really wanted to say is that eth1 should not have any services listening. I could set specifically for each service (sshd, httpd etc.) but that would be tedious. And, if I later add a service which default listens on all nics, they would be open on eth1. 

What I did was to install iptables and (using webmin) configured the "Linux Firewall", and selected a simple setup "Block all traffic on nic:" where I selected eth1. I am still able to access sshd and httpd on VM3 and VM4. I guess that means that VMWare is before iptables in the chain. And it works exactly as i hoped :-)

[quote=bradmkjr]
simple, give them shell accounts on the VM. they don't need any account on the vm host or the other machines, if they can ssh into the actual vm then that part is secure.
[/QUOTE]
Yeah, that is what I did. From VM3 and VM4 users are not able ping, ssh or anything else to eth1, eth0 or any of the machines on the 192.168.x.x network.

Thanks for the tips Brad. They were helpul. Now I can securely set up VMs on the same server as I use for other stuff without security issues.

-sveinh

---

### Post by Toky on 2008-07-05
Great diagram!

Now I will attempt to hijack this thread...


I have a question like sveinh's 

I have a MoBo that has 4 integrated NICs
I would like to assign eth2 to the VMware guest but I want it to get an IP from the dhcp that the host is running.

I want to be able to create a rule to forward traffic from a specific port to the VMware guest nic (eth2)

My reasons are security based too.

[IMG]http://tokynet.com/hosted/smalldiagram.png[/IMG]

---

### Post by Toky on 2008-07-07
bump

really need help with this please.

---

### Post by Chris33478 on 2008-07-08
Toky,

How are you connecting to the Internet? If you're using a router of some sort, the easiest solution may be to just connect eth2 to a connected switch and forward port 25 traffic to that IP.

-Chris

---

