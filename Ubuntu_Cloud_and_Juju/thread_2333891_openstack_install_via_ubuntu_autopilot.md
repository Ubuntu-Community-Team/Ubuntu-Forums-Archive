---
title: "openstack install via ubuntu autopilot"
date: 2016-08-14
forum: Ubuntu Cloud and Juju
---

### Post by sinamaleki2 on 2016-08-14
Hi all , 

I have 8 HP DL380 G9 servers with a cisco 2960X switch for deploying ubuntu openstack . 

I had install the MAAS via this command " 
```
sudo apt install maas
```

and allthings goes fine . then I add images from images section and I change the private network in cluster to manage DHCP and DNS . the gateway of the private network is the MAAS IP . 
then I add sshkey to maas and i power on 7 servers . MAAS detected the hardware and networks . So i do a commision . after that in every node I add bond . 

the bond modes are balance-alb which there isnt any requirements at switch . 

each server have 1 bond that the interfaces are eth0 eth1 eth2 and these 3 physical nodes are the same VLAN in switch . and eth3 is the public network . 

after that I use openstack-install command and allthing goes fine and landscape installed successfuly . after logging in to landscape I do an openstack install . 

But some servers stucks at Bootstrap juju environment on . I do openstack install from landscape severals and all times servers hangs on bootsrap juju environment . so there isnt server problem and hardware issues cause installing cloud will be stucks on servers randomly . 

So I do a login to console of servers that hangs and all of them hangs at "DHCPRELEASe" that I put the screenshot here . 

I will attach the logs here too . so if anyone can help me to solve this issue its will be perfect . 

here is the logs that landscape generated : [http://87.247.175.1/landscape-openstack-autopilot-logs-2016-08-13T05_11_08Z.tar.gz](http://87.247.175.1/landscape-openstack-autopilot-logs-2016-08-13T05_11_08Z.tar.gz)

Thanks

---

