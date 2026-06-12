---
title: "KVM &amp; Lucid; need guest2guest networking"
date: 2011-10-05
forum: Virtualisation
---

### Post by EdLesMann on 2011-10-05
Hello,

I am running KVM on 64 bit Ubuntu 10.04 Lucid with an AMD processor that has the svn flag.

I have read a few different guides on KVM and networking in Lucid including this one : [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

However, they all seem to focus on bridged networking. I need guest to guest networking.

I open the KVM virt-manager->Edit->Host Details->Virtual Networks->Add button.

First page is a banner page->Forward.
Network Name: LocalLan->Forward.
Network: 192.168.100.0/24->Forward.
Enable DHCP: checked; Start: 192.168.100.10; End: 192.168.100.20->Forward.
Isolated virtual network: selected->Forward.
Summary page->Finish.

"Error creating virtual network: cannot create bridge 'virbr0': Operation not permitted"

Fine. I will launch it with sudo. Except the sudo virt-manager launches a completely different session. I can't see my virtual machines in it and the network I created there isn't seen by my user mode virt-manager.

Does anyone know what change I need to make to allow the user mode virt-manager to create the virbr0?

Thanks!

---

### Post by lcman on 2011-10-05
> **EdLesMann said:**
> Hello,

I am running KVM on 64 bit Ubuntu 10.04 Lucid with an AMD processor that has the svn flag.

I have read a few different guides on KVM and networking in Lucid including this one : [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

However, they all seem to focus on bridged networking. I need guest to guest networking.

I open the KVM virt-manager->Edit->Host Details->Virtual Networks->Add button.

First page is a banner page->Forward.
Network Name: LocalLan->Forward.
Network: 192.168.100.0/24->Forward.
Enable DHCP: checked; Start: 192.168.100.10; End: 192.168.100.20->Forward.
Isolated virtual network: selected->Forward.
Summary page->Finish.

"Error creating virtual network: cannot create bridge 'virbr0': Operation not permitted"

Fine. I will launch it with sudo. Except the sudo virt-manager launches a completely different session. I can't see my virtual machines in it and the network I created there isn't seen by my user mode virt-manager.

Does anyone know what change I need to make to allow the user mode virt-manager to create the virbr0?

Thanks!

You need to create a bridged interface for your guests in your /etc/network/interfaces like this:
```
auto br0 
iface br0 inet static         
address 192.168.0.10         
network 192.168.0.0         
netmask 255.255.255.0         
broadcast 192.168.0.255         
gateway 192.168.0.1         
bridge_ports eth0         
bridge_stp off         
bridge_fd 0         
bridge_maxwait 0
```Of course, it needs to be in an entirely different network that your host's if you want only internal guest networking.

---

### Post by EdLesMann on 2011-10-05
Thanks for the reply.

I tried that already. It was posted in the Ubuntu KVM guide (in my first post). It doesn't show up as a possible network even though it shows up in ifconfig.

I did discover something interesting. When I created a network by running `sudo virt-manager` it not only created a new network with the proper settings but it survives reboot AND shows up when I run ifconfig!

I just can't seem to access it when I run virt-manager as a user...

[Edit to post]

OK. So I found a blog posting that said there was a difference between "QEMU Usermode" and "QEMU" which are the two options I have for localhost (they were there the first time I launched virt-manager). I don't know what those differences are, but ok, sure, whatever. I deleted my VM's out of "QEMU Usermode" and recreated them in "QEMU" mode. I was then able to access the network I created when I did "sudo virt-manager". However, it wouldn't assign a DHCP address to me. I kept getting an error about permissions.

So I just dumped all of the VM's and ran "sudo virt-manager" and recreated all the VM's inside of it. Everything works now so I just updated all the menu entries and added the gksudo in front of all the "virt-manager"'s. I am sure there is a reason why I shouldn't run it as sudo but it works now so I don't care :-P

---

