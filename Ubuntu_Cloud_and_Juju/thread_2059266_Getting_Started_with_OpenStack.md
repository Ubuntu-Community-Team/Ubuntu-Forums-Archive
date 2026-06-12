---
title: "Getting Started with OpenStack"
date: 2012-09-17
forum: Ubuntu Cloud and Juju
---

### Post by jonesyp on 2012-09-17
Hi,

I'm following the Ubuntu OpenStack Beginners Guide at:

[http://docs.openstack.org/essex/openstack-compute/starter/content/Base_OS-d1e542.html](http://docs.openstack.org/essex/openstack-compute/starter/content/Base_OS-d1e542.html)

I have used Ubuntu for some years, but always just accepted the standard partition set-up.  I'm now following the instructions which say use Ubuntu Server, and now I am not sure how to set-up the partitions in the format asked for:

We will also be running nova-volume on this server and it is ideal to have a dedicated partition for the use of nova-volume. So, ensure that you choose manual partitioning scheme while installing Ubuntu Server and create a dedicated partition with adequate amount of space for this purpose. We have referred to this partition in the rest of the chapter as **/dev/sda6**. You can substitute the correct device name of this dedicated partition based on your local setup while following the instructions. Also ensure that the partition type is set as Linux LVM (8e) using fdisk either during install or immediately after installation is over. If you also plan to use a dedicated partition as Swift backend, create another partition for this purpose and follow the instructions in "Swift Installation" section below.

Would anyone be able to advice?

Also, I am assuming I am OK to use VirtualBox Images.

Finally, on the network configuration instructions:

[http://docs.openstack.org/essex/openstack-compute/starter/content/Network_Configuration-d1e591.html]("http://docs.openstack.org/essex/openstack-compute/starter/content/Network_Configuration-d1e591.html")

Do I actually use the settings below, I do I have to adjust for my settings?

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
		address 10.10.10.2
		netmask 255.255.255.0
		broadcast 10.10.10.255
		gateway 10.10.10.1
		dns-nameservers 10.10.8.3

auto eth1
iface eth1 inet static
		address 192.168.3.1
		netmask 255.255.255.0
		network 192.168.3.0
		broadcast 192.168.3.255

Many thanks

Peter Jones
Crawley
West Sussex

---

