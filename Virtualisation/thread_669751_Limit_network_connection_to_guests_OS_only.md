---
title: "Limit network connection to guests OS only"
date: 2008-01-16
forum: Virtualisation
---

### Post by jc104 on 2008-01-16
I am just getting started with ubuntu and need help in configuring my system.

My host machine is running winXP and I have two ubuntu guest OS running on vmware. Using bridge networking, I can connect to the internet from the host and both vm instances. I can ping the host from the vm and vice versa. 

Question:
Since my purpose in creating this environment was to have an isolated network where only the two guest os can communicate with each other, is there an option in ubuntu or vmware server that will allow me to limit the connection between these instances.

I only want VM1 to talk to VM2 with no need for VM->host or VM->internet.

Thanks,
JC

---

### Post by fjgaude on 2008-01-16
Do the VMs have to talk to the Internet?

---

### Post by jc104 on 2008-01-17
Yes, I can connect to the internet from the VMs but don't want that. I just want to be able to limit the connection between the two VMs so I can have a webserver on one and use it from the other VM.

---

### Post by fjgaude on 2008-01-17
Is it permitted to remove your router from the WAN, from the Internet connection?

If not it is going to require setting the guest to Bridged and then somehow downing the host. I've never done such.

Let us know if you get such working. Thanks.

---

### Post by gvartser on 2008-01-18
Change the IP adress subnet on the 2 UBUNTU guest os:es to its own subnet.

example:

Ubuntu guest 1:
* IP: 192.168.66.2
* SM: 255.255.255.0

Ubuntu guest 2:
* IP: 192.168.66.3
* SM: 255.255.255.0

Best regz,
/g

---

### Post by jc104 on 2008-01-18
Thanks for the reply, unfortunately I am not able to edit the subnet mask in the vmware settings. 
I will have to learn more about networking and experiment until I find out how to do this. Thanks for your help.

---

### Post by gvartser on 2008-01-19
> **jc104 said:**
> Thanks for the reply, unfortunately I am not able to edit the subnet mask in the vmware settings. 
I will have to learn more about networking and experiment until I find out how to do this. Thanks for your help.

I meant that you should change the subnet & Ip adress in both guest os:es, so that they use the same which should be different from the one where your host is on.

No need to change anything in vmware, you do it on your ubuntu machines.

Best regz,
/g

---

### Post by popch on 2008-01-19
When creating a virtual machine in VMWare Workstation you are given several options for networking:
[LIST=1]
[*]NAT
[*]Bridged
[*]Virtual Network for communication between virtual machines only
[*]none[/LIST]#3 is exactly what you want.
Since I do not use VMWare any more, I can not tell how to set it up. However, I presume it's possible using VMWare Server, too.

---

### Post by raven on 2008-02-01
I think the best solution is what popch suggested
but
Me on the other hand I want the opposite

I have Ubuntu Gutsy amd64 as host

and with all kind of virtual OS's (NIXs, XPs)

and all guests are configured with NAT
all guest need to access internet and they do
all guests share folder with host and they do

but,
no guest can ping host
host cannot ping any of guests
but guest can ping other guest

and this after disabling win firewall on XP's
disabling firestarter with (stop firewall option on host)
still,
no guest can ping host
host cannot ping any of guests
but guest can ping other guest

host IP =192.168.2.3/24 static
guests IP=192.168.2.1xx/24 DHCP

any ideas ?

---

### Post by popch on 2008-02-01
@raven: Again: I am not using VMWare any more, so I can not verify anything I am going to say here. Please take it as a number of suggestions of things to try.

You mention one IP address of the host. I think the host should have two addresses: the one by which the host is known to all other nodes in the real network, and one by which it is known to the guests. In fact, VMWare entertains a virtual network within the host, if memory serves me right.

Therefore, I think that guests should be able to ping the host's real network address. They might be able to ping the virtual address as well, provided that NIC has been setup to be pingable.

Now I am going to tread on thin ice:

The host OS may be unable to ping the guests because it is not aware of the virtual NIC through which the guest machines are visible. Perhaps adding a line to the routing table would change that?

---

