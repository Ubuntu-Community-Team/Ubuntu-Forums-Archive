---
title: "make 2 lxc communicate through multiple virtual bridges"
date: 2012-08-23
forum: Virtualisation
---

### Post by gvenkatsm on 2012-08-23
Hi All.

I need to create 2 lxc s connected to 2 different virtual briodges ( using "brctl") make them communicate through the virtual network. I am done with creation of bridges and connections ( using  "ip link add" ) and have connected them. I was able develop custom application and run instance of that attached to each of the bridges(using sysfs), and have traffic running through the links.

Issue/Problem-1:
But when it comes to communication between 2 lxc s ( lxc-1 ---- br1 ------ br2 --- lxc2 ) I see communication not happening through the link(s) I created, and not even through the interface created after lxc-start. I see traffic going through "any" and loop back(lo) as seen through wireshark.

"route" displayes the right interfaces ( in both the container)
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         [www.routerlogin]("http://www.routerlogin") 0.0.0.0         UG    0      0        0 wlan0
10.0.3.0        *               255.255.255.0   U     0      0        0 lxcbr0
10.4.0.0        *               255.255.255.0   U     0      0        0 vethn3AMsG <<<<< lxc-2--br2
10.4.0.0        *               255.255.255.0   U     0      0        0 vethuNvryF <<<<<<lxc-1--br1
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0

==
br1
 <edited>

br1-br2-l0 (1)
 port id        8001            state             forwarding
 designated root    8000.560f511095d7    path cost           2
 designated bridge    8000.560f511095d7    message age timer       0.00
 designated port    8001            forward delay timer       0.00
 designated cost       0            hold timer           0.55
 flags            

vethuNvryF (2)
 port id        8002            state             forwarding
 designated root    8000.560f511095d7    path cost           2
 designated bridge    8000.560f511095d7    message age timer       0.00
 designated port    8002            forward delay timer       0.00
 designated cost       0            hold timer           0.54
 flags            

gvenkatsm@gvenkatsm-300E4Z-300E5Z-300E7Z:~$ brctl showstp br2
br2
 bridge id        8000.062575c67fe8
 <edited>

br1-br2-l1 (1)
 port id        8001            state             forwarding
 designated root    8000.062575c67fe8    path cost           2
 designated bridge    8000.062575c67fe8    message age timer       0.00
 designated port    8001            forward delay timer       0.00
 designated cost       0            hold timer           0.00
 flags            

vethn3AMsG (2)
 port id        8002            state             forwarding
 designated root    8000.062575c67fe8    path cost           2
 designated bridge    8000.062575c67fe8    message age timer       0.00
 designated port    8002            forward delay timer       0.00
 designated cost       0            hold timer           0.00
 flags            

==

Basically I would need something similar  but not exactly to have a setup as in:
[http://lxc.sourceforge.net/index.php/about/kernel-namespaces/network/configuration/](http://lxc.sourceforge.net/index.php/about/kernel-namespaces/network/configuration/) 


Issue/Problem-2
The above link uses name-spaces. But I could get the command ns_exec for my ubuntu. Closest I see is lxc-unshare, unfortunately I could not get any documentation on that except saying as testing tool. or is it nsexec? I am not sure if use namespaces would help above problem.

Thanks a lot and regards,
gvenkatsm

---

