---
title: "Setup complete cloud [CLC+CC+NC] on a single machine"
date: 2011-02-07
forum: Ubuntu Cloud and Juju
---

### Post by snehalmasne on 2011-02-07
Hello there !

As a part of practical, I need a cloud. I have only one machine as of now. Could you please help me in getting a complete cloud setup on single machine ? Also I would be using that PC in college LAN, So if possible give the network configuration settings for following parameters :


Static IP of the form : 172.16.88.x

DNS : x.x.x.x  x.x.x.x 

Netmask : 255.255.248.0

Gateway : 172.16.88.1


While doing setup it asks about range of public IPs. After setup, I need to play with /etc/network/interfaces and /etc/eucalyptus.conf (some br0 and VLAN things). 

Got one article here : [https://help.ubuntu.com/community/UEC/Topologies](https://help.ubuntu.com/community/UEC/Topologies)

I am not sure what exactly these are and what values to specify for my college network. 

Please help me out.  Thanks in advance.



Regards,
[Snehal Masne]("http://www.techproceed.com")
[www.TechProceed.com](www.TechProceed.com)

---

### Post by kim0 on 2011-02-08
Hi,
The min supported setup is two machines. For testing setups, your best bet is probably the following article for running UEC on EC2

[http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html](http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html)

---

### Post by 1clue on 2011-02-14
Can one of the machines be a workstation or do they both need to be server?

And could the two machines be VMs?

---

### Post by kim0 on 2011-02-16
The NC needs to run on a physical machine, one that has VT support in its CPU

The other machine (CLC, CC, SC) can be a workstation, and I guess can even be a VM (give it 2G ram and plenty of disk space)

---

