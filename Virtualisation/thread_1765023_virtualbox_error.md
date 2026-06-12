---
title: "virtualbox error"
date: 2011-05-22
forum: Virtualisation
---

### Post by qwertyjjj on 2011-05-22
I am trying to forward a port to vb but now it won't start.
Any ideas how I can correct this?

Failed to open a session for the virtual machine xp_clean.
NAT#0: configuration query for "GuestPort" int failed (VERR_CFGM_VALUE_NOT_FOUND).
Unknown error creating VM (VERR_CFGM_VALUE_NOT_FOUND).

```

j@j-Inspiron-9300:~$ VBoxManage modifyvm "xp_clean" --natpf1 "guestssh,tcp,,1604,,1604"
VBoxManage: error: The machine 'xp_clean' is already locked for a session (or being unlocked)
VBoxManage: error: Details: code VBOX_E_INVALID_OBJECT_STATE (0x80bb0007), component Machine, interface IMachine, callee nsISupports
Context: "LockMachine(a->session, LockType_Write)" at line 339 of file VBoxManageModifyVM.cpp
j@j-Inspiron-9300:~$ VBoxManage modifyvm "xp_clean" --natpf1 "guestssh,tcp,,1604,,1604"
j@j-Inspiron-9300:~$ VBoxManage modifyvm "VM name" --natpf1 delete "guestssh"
VBoxManage: error: Could not find a registered machine named 'VM name'
VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBox, interface IVirtualBox, callee nsISupports
Context: "FindMachine(Bstr(a->argv[0]).raw(), machine.asOutParam())" at line 336 of file VBoxManageModifyVM.cpp
j@j-Inspiron-9300:~$ VBoxManage modifyvm "xp_clean" --natpf1 delete "guestssh"
j@j-Inspiron-9300:~$ 


```

I get the error

---

### Post by CharlesA on 2011-05-22
What exactly are you trying to do?

---

### Post by qwertyjjj on 2011-05-22
> **CharlesA said:**
> What exactly are you trying to do?

FORWARD a port to xp in the virtual box

---

### Post by CharlesA on 2011-05-22
You just need to set the networking as bridged and then connect with the IP address of the guest.

Does the VM start?

---

### Post by qwertyjjj on 2011-05-22
> **CharlesA said:**
> You just need to set the networking as bridged and then connect with the IP address of the guest.

Does the VM start?

No VM will not start now.
Failed to open a session for the virtual machine xp_clean.
NAT#0: configuration query for "GuestPort" int failed (VERR_CFGM_VALUE_NOT_FOUND).
Unknown error creating VM (VERR_CFGM_VALUE_NOT_FOUND).

I tried to find the xml file with the settings but cannot.

---

### Post by qwertyjjj on 2011-05-22
> **CharlesA said:**
> You just need to set the networking as bridged and then connect with the IP address of the guest.

Does the VM start?

now it starts since setting it to bridged.
How can I forward a the port to the VB?

Will this do it?

VBoxManage setextradata namehere "VBoxInternal/Devices/pcnet/0/LUN#0/Config/SSH/HostPort" 1604
VBoxManage setextradata namehere "VBoxInternal/Devices/pcnet/0/LUN#0/Config/SSH/GuestPort" 1604
VBoxManage setextradata namehere "VBoxInternal/Devices/pcnet/0/LUN#0/Config/SSH/Protocol" TCP

---

### Post by CharlesA on 2011-05-22
What are you wanting to forward?

---

### Post by qwertyjjj on 2011-05-22
> **CharlesA said:**
> What are you wanting to forward?

port 1604 and maybe port 1935:

VBoxManage setextradata namehere "VBoxInternal/Devices/pcnet/0/LUN#0/Config/SSH/HostPort" 1604
VBoxManage setextradata namehere "VBoxInternal/Devices/pcnet/0/LUN#0/Config/SSH/GuestPort" 1604
VBoxManage setextradata namehere "VBoxInternal/Devices/pcnet/0/LUN#0/Config/SSH/Protocol" TCP

---

### Post by CharlesA on 2011-05-22
You don't really need to "forward" any ports to access them on the guest as long as you are using bridged networking.

---

### Post by qwertyjjj on 2011-05-22
> **CharlesA said:**
> You don't really need to "forward" any ports to access them on the guest as long as you are using bridged networking.

There is a client program on the VB that listens on port 8080 and connects remotely to a server but if the server connection comes in from the router doesn't it have to be forwarded?
Do I need to forward the port on the router to the linux box and then forward the linux port to the host?

---

### Post by CharlesA on 2011-05-22
> **qwertyjjj said:**
> There is a client program on the VB that listens on port 8080 and connects remotely to a server but if the server connection comes in from the router doesn't it have to be forwarded?
Do I need to forward the port on the router to the linux box and then forward the linux port to the host?

All you would have to do is give the guest an ip address and forward that port on the router to that ip address. Just like forwarding a port to a physical machine.

---

### Post by qwertyjjj on 2011-05-22
> **CharlesA said:**
> All you would have to do is give the guest an ip address and forward that port on the router to that ip address. Just like forwarding a port to a physical machine.

The ip addresses in VB are in the 10.0.xx range whereas most routers expect to forward to 192.xx xx ranges don't they?

---

### Post by CharlesA on 2011-05-22
> **qwertyjjj said:**
> The ip addresses in VB are in the 10.0.xx range whereas most routers expect to forward to 192.xx xx ranges don't they?
Most of the ones I have used can do any ip.

Are you sure you have the guest set to use bridged and not NAT? IIRC, NAT uses 10.2.x.x.

---

### Post by qwertyjjj on 2011-05-24
> **CharlesA said:**
> Most of the ones I have used can do any ip.

Are you sure you have the guest set to use bridged and not NAT? IIRC, NAT uses 10.2.x.x.

I have it set to bridged eth1 and the IP is 192.168.1.39
No matter what I so though I cannot seem to get connections on the forwarded ports. I set up NAT in my router to forward TCP/UDP of 1604 and 21 to that IP address.
Is there anyway I can check the forwarding / routing?

---

### Post by CharlesA on 2011-05-24
Can you access them from another box on the same network?

If you can, then the ports are open and I would double check the port forwarding.

---

### Post by qwertyjjj on 2011-05-24
> **CharlesA said:**
> Can you access them from another box on the same network?

If you can, then the ports are open and I would double check the port forwarding.

access what?
When I got to canyouseeme.org from the machine it says the port is open.
Am I supposed to ping the port from another machine on the network?
I don;t think the router will pick that up as it is expecting WAN connections to port 1604 before forwarding them.

---

### Post by qwertyjjj on 2011-05-24
Just found this on a post:
> 
Ok, I've literally JUST solved the same problem for myself lol. Forward your ports to your Host OS(Your physical, non virtual system), just like normal. Then, setup a bridged connection.

Now, on Linux, there are some Terminal commands to add "HostPort", "GuestPort", and Protocol. I will get into that later, once I fully test how to do it with a Windows host. I did it in Linux.

But just forwarding to your actual physical system and then setting the connection to "bridged" should suffice.


Does, that make sense? I thought on a bridged system I should be port forwarding to the ip address of the virtual box not the actual physical host?

---

### Post by CharlesA on 2011-05-24
> **qwertyjjj said:**
> access what?
When I got to canyouseeme.org from the machine it says the port is open.
Am I supposed to ping the port from another machine on the network?
I don;t think the router will pick that up as it is expecting WAN connections to port 1604 before forwarding them.

If canyouseeme shows that the port is open, then you have it set up correctly.

> **qwertyjjj said:**
> 
Does, that make sense? I thought on a bridged system I should be port forwarding to the ip address of the virtual box not the actual physical host?

I've never had to do that, the only thing I've had to do is allow that port thru on the host's firewall.

---

### Post by qwertyjjj on 2011-05-24
> **CharlesA said:**
> If canyouseeme shows that the port is open, then you have it set up correctly.



I've never had to do that, the only thing I've had to do is allow that port thru on the host's firewall.

So, if canyouseeme shows open then it is working and going through the host firewall as well?
If the host is 192.168.1.5 and the VB is 192.168.1.6 then I port forward to 192.168.1.6?
Doesn't it have to go through the host IP first?

---

### Post by CharlesA on 2011-05-24
> **qwertyjjj said:**
> So, if canyouseeme shows open then it is working and going through the host firewall as well?

That's correct.
> 
If the host is 192.168.1.5 and the VB is 192.168.1.6 then I port forward to 192.168.1.6?
Doesn't it have to go through the host IP first?

It would have to be forwarded to 192.168.1.6 and doesn't have to go thru the host's IP first, since you are using bridged networking, the machine is seen as being on the same network as the host.

---

