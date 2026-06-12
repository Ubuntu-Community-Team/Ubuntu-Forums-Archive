---
title: "KVM Networking Issue"
date: 2010-05-28
forum: Virtualisation
---

### Post by enkitech on 2010-05-28
Hi everyone,

I am trying to get the networking to function correctly on my KVM-based virtual machines. I am using the new Ubutu Server LTS, v. 10.04 as both host and guest. I have managed to get the machines to boot and access them through qemu. However something seems to be not quite right with the networking configurations that let traffic pass from the host to the guest.

In my case, both the host and the guest will need static IP addresses. The host is 10.0.1.108, and the two guest machines will be 10.0.1.112 and 113.

The current /etc/network/interfaces file on the host is:

## The loopback network interface
auto lo
iface lo inet loopback

## The primary network interface
auto eth0
iface eth0 inet manual


auto br0
iface br0 inet static
    address 10.0.1.208
    network 10.0.1.0
    netmask 255.255.255.0
    broadcast 10.0.1.255    
    gateway 10.0.1.1
    bridge_ports eth0
    bridge_fd 0
    bridge_hello 2
    bridge_maxage 12
    bridge_stop off


My first guest is currently configured:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.1.212
netmask 255.255.255.0
broadcast 10.0.1.255
gateway 10.0.1.1



I have tried the instructions here:
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

however they are not working, possibly because they were written for 8.04. Some of the files listed simply don't sync up to my installation.

I hope someone out there can help me. Thanks.

---

### Post by srivo on 2010-06-04
I have a similar problem, they only way I found from now is to issu the:
 sudo sysctl -p /etc/sysctl.conf each time I reboot the machine.

---

### Post by benderisgreat on 2010-06-06
in what way exactly does networking not function? how did you test this? where did it fail?

---

