---
title: "Not able to set a bridged connection in Virtual Box"
date: 2008-09-19
forum: Virtualisation
---

### Post by akshata on 2008-09-19
Hi,
   I have installed Ubuntu in both virtual machines in Sun virtual box. Each machine has network setting s connected to a NAT. I want to put two virtual machines in the same network and ping them. Are there no options for bridged connections in virtual box? I tried using the option not attached for each network adapter. But, i could not ping the two virtual machines after statically assigning the ip address. How should i set up bridged connections in virtual box? Should i disable NAT? Please provide some guidance.

---

### Post by dark_phantom on 2008-09-20
Bridged is not directly enabled, but it is supported nonetheless.  The documentation has steps as to how to enable it.  Two different options, permanent or dynamically.  See section 6.8 of the latest manual.

```

Install needed software
sudo apt-get install bridge-utils
modify /etc/network/interfaces to create the bridge interface
auto br0
iface br0 inet dhcp
bridge_ports eth0  #assuming eth0 is your interface
restart networking
sudo /etc/init.d/networking restart
Add interface name and user of that interface
sudo VBoxIFAdd vbox0 <user_id> br0
Then add or modify the interface to your VM to use vbox0, make sure to select host interface.

```

That's the permanent method, you will notice that eth0 will not have an IP after this and that should be normal.  The new interface br0 will now be given the IP that you used to get on eth0.

I hope this helps, read the manual it's good information.

---

### Post by akshata on 2008-09-21
Thanks!!

I tried the procedure given in the manual. 
I was able to edit /etc/network/interfaces
All the steps were fine till i had to do

sudo VBoxAddIF vbox0 <user> br0

It said 
VBoxAddIF : command not found

i tried to locate it using find / -name VBoxAddIF
but in vain
/sbin is included in my $PATH variable

Could you please help regarding this issue.

---

### Post by pwaugh on 2008-09-21
> **akshata said:**
> Thanks!!

I tried the procedure given in the manual. 
I was able to edit /etc/network/interfaces
All the steps were fine till i had to do

sudo VBoxAddIF vbox0 <user> br0

It said 
VBoxAddIF : command not found

i tried to locate it using find / -name VBoxAddIF
but in vain
/sbin is included in my $PATH variable

Could you please help regarding this issue.

He gave the command wrong in his example above... strangely, you have it right:

sudo VBoxAddIF vobx0 {user} br0

of course, you must use your username, in place of {user}.

good luck

---

