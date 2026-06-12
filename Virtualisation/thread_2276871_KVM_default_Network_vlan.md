---
title: "KVM default Network vlan"
date: 2015-05-05
forum: Virtualisation
---

### Post by Sreejith_P on 2015-05-05
Hello all,

I am trying to learn virtual networking with KVM. I am trying to create a vlan for the virbr0 (the default Nat KVM network). I added the Network configuration on to /etc/network/interfaces

auto virbr0.10
iface virbr0.10 inet static
        address 10.240.0.1
        netmask 255.255.252.0

when i restart the computer, i am not getting the network. I am doing this setup on my laptop.
Please let me know whether i am doing it correct.

---

### Post by TheFu on 2015-05-05
I've found the automatically created bridges to be less-than-stable over the years.  If I manually make the bridge, it behaves perfectly, as expected.  There are posts here about how to make a bridge for KVM/libvirt uses. Search.  You are missing all sorts of things, it appears, if I'm reading the question/issue correctly.

Which machine are those settings? Which bridge is it connected with? What are the settings for the bridge?

There is an ubuntu server guide which goes into details for this stuff. A web search will find it or a link is in my profile here under "visitor messages".

---

### Post by Sreejith_P on 2015-05-05
I am trying to achieve the following

eth0/wlan0 ---> Natted virtual bridge (virbr0) ----> vlan 

i dont want to attach the brigde to eth0 because my internet connection may be on eth0 or wlan0. So creating a vlan on virbr0 is the choice.

Please let me know if there is any alternative method for the achieving the same

---

### Post by TheFu on 2015-05-05
Either you will need to make your hostOS into a router (eeew) or manually convert the bridge connection for VMs between eth0/wlan0 in the interfaces file.

I don't have any VM hosts running on portable devices, so don't know the details to do what you seek. Sorry.

---

