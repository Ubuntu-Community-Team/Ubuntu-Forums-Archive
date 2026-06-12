---
title: "Error while trying to restart network. &quot;Couldnt read interface file etc/network/inte&quot;"
date: 2014-05-29
forum: Server Platforms
---

### Post by Micheal_Overman on 2014-05-29
[SIZE=3][FONT=arial]I have installed lamp onto my computer and I am currently running and apache sever. I am running ubuntu through a virtual machine. Since I am hosting the server on a VM i want the IP to stay the same every time i restart the VM. I need it to stay the same because I am port forwarding that IP. I looked at a guide online on how to make my ip static. This is the guide I followed: [http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu](http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu). 

This is my interface file:

auto lo eth0
iface lo inet loopback
iface eth0 inet dynamic
address 192.168.x.xx
broadcast 192.168.x.xxx
netmask 255.255.255.0
gateway 192.168.x.x

I edited the file to that but when I run the command: [COLOR=#000000]*sudo /etc/init.d/networking restart*[/COLOR]

[COLOR=#000000]But I get the error couldn't read interface file /etc/network/inerface

How can I fix this or are there any other ways to get a static ip?[/COLOR][/FONT][/SIZE]

---

### Post by steeldriver on 2014-05-29
Hello and welcome to the forums

I don't think **dynamic** is a legal method for the inet (IPv4) address family - you probably need that to be **static**

If this is on a VM, you will also need to set the VM's virtual network interface to bridged mode (instead of NAT) if you want to use an IP in the address space of the host LAN (which I am guessing you do, based on the 192.168.x.x addressing).

---

### Post by Micheal_Overman on 2014-05-29
I already have my virtual machine of bridged mode, ill try changing the dynamic to static and see how that works.

---

### Post by Micheal_Overman on 2014-05-29
[SIZE=2][FONT=arial]I have got around the error and now it restarts my networking interfaces. But when it does restart and I run ifconfig I do not get the IP that I set.
This is my /etc/network/interfaces file:
[/FONT][/SIZE][FONT=arial][/FONT][SIZE=2][FONT=arial]# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
    address 192.168.0.yy
    netmask 255.255.255.x
    broadcast 192.168.0.xxx
    network 192.168.0.x
    gateway 192.168.0.x
dns-nameservers 194.168.4.xxx

But when I run ifconfig it comes up with the ip address being: 192.168.0.xx not 192.168.0.yy




[/FONT][/SIZE]

---

### Post by steeldriver on 2014-05-29
Is this really a (CLI) server or do you have a GUI desktop installed on it? If so what desktop - and is NetworkManager or another networking service running?

BTW there is nothing sensitive about LAN-side IP addresses - you can post the actual numbers (not xx, yy)

---

