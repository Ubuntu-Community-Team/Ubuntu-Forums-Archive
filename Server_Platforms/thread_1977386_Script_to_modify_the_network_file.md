---
title: "Script to modify the network file"
date: 2012-05-10
forum: Server Platforms
---

### Post by Raj Singh on 2012-05-10
Hello Folks, I'm new to Ubuntu and need some help. Basically I need help with the /etc/network/interfaces file. we have 2 many users are they are constantly making mistakes entering the network information into the file. I would like some help with a script that will do the following:

I would like to have the user only be able to input the ip,netmask, gateway for both devices bond0 and bond1. 

Here is my interfacces file:

# This file describes the network interfaces available on your system.

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# Private bond0
auto bond0
iface bond0 inet static
address 
netmask 
up /sbin/ifenslave bond0 eth2 eth4
down /sbin/ifenslave bond0 eth2 eth4

# Public bond1
auto bond1
iface bond1 inet static
address 
gateway 
netmask 
up /sbin/ifenslave bond1 eth3 eth5
down /sbin/ifenslave bond1 eth3 eth5

---

### Post by rubylaser on 2012-05-10
There's are no checks built into this script to test for valid ips, subnets, etc and there are no loops to allow users to make changes if they screw up entering info (other than to ctrl+c or re-run the script), but here's a quick script to get you started.

```
#! /bin/bash
# Script to configure /etc/network/interfaces
echo "Configuring bond0..."
echo "Please enter an ip address for bond0 and press [ENTER]:"
read bond0_ip_address
echo "Please enter a gateway for bond0 and press [ENTER]:"
read bond0_gateway
echo "Please enter a subnet mask for bond0 and press [ENTER]:"
read bond0_subnet_mask
echo "These are the values you entered for bond0 and press [ENTER]:"
echo "ip address: $bond0_ip_address, gateway: $bond0_gateway, subnet: $bond0_subnet_mask"
echo ""
echo "Configuring bond1..."
echo "Please enter an ip address for bond0 and press [ENTER]:"
read bond1_ip_address
echo "Please enter a gateway for bond0 and press [ENTER]:"
read bond1_gateway
echo "Please enter a subnet mask for bond0 and press [ENTER]:"
read bond1_subnet_mask
echo "These are the values you entered for bond0 and press [ENTER]:"
echo "ip address: $bond1_ip_address, gateway: $bond1_gateway, subnet: $bond1_subnet_mask"
echo ""
# cleanup existing file
> /etc/network/interfaces
echo "# This file describes the network interfaces available on your system." >> /etc/network/interfaces

echo "# The loopback network interface" >> /etc/network/interfaces
echo "auto lo" >> /etc/network/interfaces
echo "iface lo inet loopback" >> /etc/network/interfaces
echo ""
echo "# Private bond0" >> /etc/network/interfaces
echo "auto bond0" >> /etc/network/interfaces
echo "iface bond0 inet static" >> /etc/network/interfaces
echo "address $bond0_ip_address" >> /etc/network/interfaces
echo "gateway $bond0_gateway" >> /etc/network/interfaces
echo "netmask $bond0_subnet_mask" >> /etc/network/interfaces
echo "up /sbin/ifenslave bond0 eth2 eth4" >> /etc/network/interfaces
echo "down /sbin/ifenslave bond0 eth2 eth4" >> /etc/network/interfaces
echo ""
echo "# Public bond1" >> /etc/network/interfaces
echo "auto bond1" >> /etc/network/interfaces
echo "iface bond1 inet static" >> /etc/network/interfaces
echo "address $bond1_ip_address" >> /etc/network/interfaces
echo "gateway $bond1_gateway" >> /etc/network/interfaces
echo "netmask $bond1_subnet_mask" >> /etc/network/interfaces
echo "up /sbin/ifenslave bond1 eth3 eth5" >> /etc/network/interfaces
echo "down /sbin/ifenslave bond1 eth3 eth5" >> /etc/network/interfaces

# Restart networking...
/etc/init.d/networking restart

# All Done...
echo "Bonded Interfaces are setup as follows..."
ifconfig -a 
```

---

### Post by Raj Singh on 2012-05-10
Thank you so much Rubylaser. This is exactly what I was looking for. I'm so glad I joined this forum, I'm lookin forward to learning from some of the best here. 

Thanks again for yur time.

---

### Post by Raj Singh on 2012-05-10
Can I ask for one last thing please. 

Can I get a script to give me the following informtion

in /etc/hosts

1. prompt user to enter the ip address. I would like the output to be able to match below...

127.0.0.1    localhost.localdomain  localhost
2.2.2.2      [www.google.com](www.google.com) google.lon google.auk

---

### Post by SeijiSensei on 2012-05-10
Might I just ask why you are having users modify /etc/network/interfaces rather than using DHCP?

---

### Post by Raj Singh on 2012-05-10
We dont us dhcp, only static.

---

### Post by SeijiSensei on 2012-05-10
Obviously.  I was asking why you chose to make life difficult for yourselves.  Is it because you want to have specific machines be assigned specific IP addresses each time?  You can accomplish that with host reservations.  Other than that, I find it puzzling why anyone would manage a network with more than a couple of users and not use DHCP for network configuration.

---

### Post by Raj Singh on 2012-05-10
I am very new to all this, but all I know if this is how its being done here.

---

