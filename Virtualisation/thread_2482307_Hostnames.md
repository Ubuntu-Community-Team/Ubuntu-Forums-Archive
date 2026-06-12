---
title: "Hostnames"
date: 2022-12-27
forum: Virtualisation
---

### Post by bytebro on 2022-12-27
I'm probably missing something obvs here, but I just put a brand new install of VirtualBox (7.0.4) on this Ubuntu 22.10, created a brand new VM and tried to name the VM 'Mint'. It said something about 'There is already a host with that name on this network'.  I know for a fact that the only machine on my network is this laptop which is named otherwise. I *may* once upon a time have created a VM named 'Mint', but why should that be a problem here? And where, please where, are these names stored so that I may purge them?!

---

### Post by MAFoElffen on 2022-12-27
VirtualBox keeps a list of all VM Guest names and their names need to be unique. To see the names of configured VM Guests do either
```

vboxmanage list vms
## OR ##
VBoxManage list vms

```
...depending whether is is from the Ubuntu Repo's or Oracle's.

---

### Post by bytebro on 2022-12-28
OK, to clarify (I was not strictly accurate in the OP, sorry!).
I installed Vbox from their own RPM, and created a VM named 'Mint', but when I tried to name the guest host as 'Mint' it said that this name already existed on my network, which I know it does not.

I guess I need to understand more about how this all works...

---

### Post by MAFoElffen on 2022-12-30
A quick basic explanation of virtual networks and virtual switches... It doesn't mater if your virtual host is KVM, Hyper-V, VirtualBox, VMware Virtual Player. There are 3 basic types: NAT, Private, Bridged
```

Default NAT:
            
 Host ------|---Other--- 10.0.0.0
            |
  Guest-----+ 192.168.122.0
    Guest---+
      Guest-+
     
Private" 
 Host-----------Other--- 10.0.0.0
 
   Guest-----+ 172.16.2.0
     Guest---+
       Guest-+
       
Bridged/Public
 Host---------+--Other 10.0.0.0
              |
   Guest------+  10.0.0.0
     Guest----+
       Guest--+

```
NAT- (default) The VM's can communicate with each other (for example with ssh), have a connection to the internet, and can talk with the Host, even though the host has a difference IP Net address. That is because the Host is managing the NAT addresses. Cannot talk with anything else on the host's network.

Private: The VM's can talk with each other, but not with anything else. You can add a virtual router to route between networks, for example to the host network or internet. I do that with pfsense or DD-WRT, or use a server as a router/firewall/dhcp/DNS appliance with one of it's ports bridged.

Public/ Bridged. The VM's are on the host network. This usually takes up a dedicated NIC on the host to do this...

There are other virtual switches and appliances, but the 3 above are the most common... You can do most virtual networking with the 3 above. 

So yes, your VM's and the VM host, even though different net addresses are connected together on the default NAT network.

---

