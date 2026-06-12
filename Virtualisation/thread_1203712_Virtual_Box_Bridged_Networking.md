---
title: "Virtual Box Bridged Networking"
date: 2009-07-03
forum: Virtualisation
---

### Post by moonoo on 2009-07-03
Hi All, 

Hope some one can help as I have tried loads of tutorials to which nothing comes close to what I am looking to do!

In a nutshell, I am running Intrepid with VirtualBox 3, I have a virtual Machine Ubuntu 9.04 server.

What I would like to do is bridge the two so I can connect from my host machine to the virtual machine's LAMP.

I have tried bridging the network using this script:
[PHP]
#!/bin/sh

sudo apt-get install uml-utilities bridge-utils

sudo cp /etc/network/interfaces /etc/network/interfaces.`date +%F~%T`

sudo echo "
auto br0
iface br0 inet dhcp
bridge_ports eth0 vboxnet0
" >> /etc/network/interfaces

sudo /etc/init.d/networking restart
sudo echo "vboxnet0 moonoo br0">/etc/vbox/interfaces
sudo /etc/init.d/vboxdrv stop
sudo /etc/init.d/vboxdrv start
sudo chown root:vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun

echo "
Change 
KERNEL==”tun”,     NAME=”net/%k”
to
KERNEL==”tun”,    NAME=”net/%k”,  GROUP=”vboxusers”,     MODE=”0660&#8243;
"
sudo nano /etc/udev/rules.d/20-names.rules
[/PHP]

Started the virtual machine and ping every address on the host that appears in the virtual machine ifconfig.

Tried from virtual machine to host. No go either way.

So tried this tutorial:
[http://www.virtualbox.org/wiki/PPP_Tunnel](http://www.virtualbox.org/wiki/PPP_Tunnel)

Seemed to connect but again no go with connecting either wey.

Read on VirtualBox website that in VB3 you just flip a switch on the gui network section top Bridged Network and hey presto its suppose to work.

So a reinstall of VB and a new VM, ticked the box but no go..

ifconfig on the VM only give 127.0.0.1..

Confused.... I am!

So I wonder if anyone here has got something similar to what I ma looking for and if they could give me some pointers where I am going wrong.

Thanks for reading and your help!

---

### Post by sdowney717 on 2009-07-03
did not seem so complicated when I did that, no script needed.
under network settings for the VM, set it to 

adapter type PCcnet-fast III
network type bridged 
attached to eth0

and it worked.

I am running Virtualbox version 3.0 beta

I noticed from main menu edit prefernces and it is set up as a host only network with an IP address and a DHCP setting
it is called Vbox0network

---

### Post by moonoo on 2009-07-04
Cheers for that, maybe its me over complicating things!
Ill try it a simpler way and report back here!

---

### Post by moonoo on 2009-07-04
Hi, 

Thanks again, but how did you connect to the host in the VM or the VM in the host?

---

