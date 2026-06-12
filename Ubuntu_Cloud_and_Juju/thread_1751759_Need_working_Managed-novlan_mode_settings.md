---
title: "Need working Managed-novlan mode settings"
date: 2011-05-07
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-05-07
Hi,

I have setup the private cloud cloud using 2 machines (CLC/CL/Walrus/SC on one machine and NC on another machine.

I can access the vm instances through ssh the problem is instances cannot connect with the internet.

I need all the configuration files of eucalyptus of both CLC and NC because the Managed-novlan mode was assigned automatically while setting the cloud.

Instance has got two ip address 10.1.1.106 172.19.1.2

When i get into the instance it shows only 172.19.1.2 ip address and i cannot update the instance when i use the command **sudo apt-get update** to install packages from net. 


ubuntu@ip-172-19-1-2:~$ sudo apt-get update
sudo: unable to resolve host ip-172-19-1-2

---

### Post by kim0 on 2011-05-10
Hi, I think you need to set ip_forward to 1 on the CLC/CC machine, and use iptables to masquerade connections to allow for internet connections

---

