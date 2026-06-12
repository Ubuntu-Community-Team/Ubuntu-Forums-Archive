---
title: "problem with Ubuntu 9.04 image"
date: 2010-07-21
forum: Virtualisation
---

### Post by mikrix on 2010-07-21
Hello, 

I'm using Karmic , and 
I have created Jaunty Ubuntu image by vmbuilder, 

Those who are familiar with OpenNebula, might know that there is a storage of images in front-end node; the image is transferred to cluster nodes, and then boots 

Booting goes fine, so I can see the VM indicated as "running"

But that's not enough: after VM boots, I need to ssh into it

I have two images: compact one for TTYlinux (I have found it in web), and Jaunty Ubuntu (I created myself by vmbuilder); 

There is a bridge configured on cluster node


When I use TTYlinux image, I can ping its IP both from IP of cluster node on which the VM is located, and IP of front-end node. Vice versa, I can ping mentioned nodes from VM. Hence no problem with connectivity and, since the image comes wih SSH server already installed, I can SSH into it without any problem !

Now, Jaunty Ubuntu. When it boots on cluster node, I try to ping front-end node's IP from VM, but something strange happens: ping replies 10-15 (sometimes even 1) times, and then freezes : ( 
When I restart /etc/init.d/networking on VM , and ping front-end node again, everything repeats 
Same thing when I try to ping VM from front-end node : after restarting /etc/init.d/networking on VM, ping replies several times, then freezes

By the way, when I try to ping cluster node's IP from VM, ping gives almost no replies, (one at maximum) and vice versa

I don't know why Jaunty image behaves like that , here is the command that I used for vmbuilder to create it : 

**sudo vmbuilder kvm ubuntu --suite jaunty --flavour virtual --arch i386 -o**
**--libvirt qemu:///system --ip <value> --mask <value> --net <value> --bcast <value> --gw <value> --dns <value> --firstboot boot.sh --firstlogin login.sh **

I used static addressing for VM
All IP credentials are valid, IP value is registered in the subnet by administrator 

boot.sh file contains commands for installing openSSH server on first boot

Also I have modified vmbuilder's [FONT=Courier New]libvirtxml.tmpl [/FONT]template for bridge usage 

Maybe someone could help ? : (

---

### Post by mikrix on 2010-07-22
It appears that TTYlinux image behaves absolutely identically, I just have to wait more, for about a minute or two, I don't know why this is so

In case of Jaunty image, this strange fact occurs immediately after the boot of VM,

Now I realize, that this is NOT because of vmbuilder command, both images are supposed to work correctly

One more fact : when I restart, and ifconfig executed, I have br0, eth0, lo, and virbr0 interfaces in the list; MAC addresses of br0 and eth0 are the same; 
When VM image from OpenNebula boots on cluster node, one more interface called vnet0 is added to the list, and every time it is assigned some arbitrary MAC

when I run brctl before VM boots, it shows two entries
------------------------------------
name________interfaces
br0__________eth0

virbr0
------------------------------------
when I run brctl after VM boots, it shows same two entries, 
------------------------------------
name_______interfaces
br0_________eth0
                     _____________vnet0  
virbr0
------------------------------------

MAC address of VM is defined according to the IP address that VM borrows from the pool of IP addresses defined in template file; the following rule is used:

MAC = MAC_PREFIX (in my case 00:03) + hex values of borrowed IP

I don't know, maybe vnet0 and VM should have same MAC address, or maybe there is some other reason...

---

