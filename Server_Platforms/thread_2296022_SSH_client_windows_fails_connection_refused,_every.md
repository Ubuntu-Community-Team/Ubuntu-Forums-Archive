---
title: "SSH client windows fails connection refused, everything ok"
date: 2015-09-22
forum: Server Platforms
---

### Post by Dum Lu Ngoc on 2015-09-22
Hi
I install openstack on VM Virtual Box 3 node ubuntu: controller, network, compute1. 3 node installed openssh-server, firewall service inactive
But ssh client connect status:
host (windows - putty) --> controller: OK 
host (windows - putty) --> network: connection refused 
host (windows - putty) --> compute1: connection refused 
controller, network, compute1 connect together (openssh-client): OK

Thanks.

---

### Post by TheFu on 2015-09-23
Check the network types for each VM in virtualbox - are they the same and "bridged"?
Also - ssh troubleshooting guide: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

