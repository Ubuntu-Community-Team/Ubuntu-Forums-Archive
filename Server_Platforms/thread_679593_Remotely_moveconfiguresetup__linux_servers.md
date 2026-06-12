---
title: "Remotely move/configure/setup  linux servers"
date: 2008-01-27
forum: Server Platforms
---

### Post by terminal on 2008-01-27
This question basically refers to all linux distributions and not only ubuntu . Many times before i have moved full OS install of linux , basically i just cp -ax / /backup where /backup is another mounted device . After that i just get second hard disk connected , format with ext3 , copy whole /backup to it , configure grub ,etc. and whole OS copy is sucessfuly . This can also be done remotely on any linux OS . Suppose remote server has CentOS on it , i can make a new partition and upload/copy whole root over there and make grub to boot other partition and the new OS will boot fine anyway . Since it is done remotely i want the new OS to configure itself to IP address i want during boot . After reboot ubuntu doesnt name first recognized network card to eth0 or eth1 if these were already configured in previous hardware . It will name it something like eth4 or 5 ( and preserve eth0 for older NIC which will now never be connected ) . 
My question is that is it posisble to copy whole OS above way and make it NIC it will detect to set certain IP address without knowing device name it will be assigned . Themethods i have in mind are that i can set ifconfig to set all eth1-eth6 to set to required ip address and then add default gatway below it ( can be done with rc.local file ) but it will create havoc if remote system has 2 nic's . Is there any other simple way to do this ? All i want is that copied OS to boot and get on network with IP address i want so it will remain connected . Is it possible to make ubuntu name first detected NIC to eth0 instead of reserving it for previous NIC ( I am sure older distro's used to do this) .

This is useful in many scenarios like if data center doesnt provide ubuntu installation . Considering dhcp is disabled and the system hardware works with linux ( including nic ) .

---

### Post by terminal on 2008-01-28
bump!

Where does ubuntu store eth interface information ? It makes sense why ubuntu always reserves eth0 for first detected card even if its removed , eth0 wont be given to other card instead it will be named eth1 . Where is that info stored ? Is it binding interface name with mac address or something :-/

---

### Post by terminal on 2008-01-28
Found it atlast . Gutsy stores in 
/etc/udev/rules.d/70-persistent-net.rules

Feisty store in /etc/iftab ( not sure ) .

---

