---
title: "Using CC as NC, no network in instances available"
date: 2011-10-01
forum: Ubuntu Cloud and Juju
---

### Post by Majinor on 2011-10-01
Hello,

we are running 3 servers. We have tested a Cloud/CC/SC + NC + NC setup in the same network so far and this setup worked fine. Now we are trying to optimize our setup as follows:

[list]
[*]Adding a fast private Network to all servers (Cloud/CC/SC dual interface)
[*]Using the Cloud/CC/SC additionally as NC
[/list]

To do this, we have completely reinstalled UEC 11.04. Uploading Images and instancing VMs are working fine. euca-describe-instances looks good. But the instances have no network now. We have checked this by connecting to the Instance via VNC, too. (using the VNC hack as described [here](http://cssoss.wordpress.com/2010/05/04/ueceucalyptus-debugging-instances/))
We are using Images from the Store and self-made images. (which worked with the previous setup)
The instances are not able to get an IP address. And of course the meta-data service is not available, too.

Does anyone have an idea what's going wrong? 

Our entire setup:
[list]
[*]Eucalyptus:[list][*]MANAGED-NOVLAN[*]Public IP address range: 192.168.3.120-192.168.3.150[/list]
[*]Server1:[list][*]eth0: Public Interface 192.168.3.101[*]eth1: Private Interface 192.168.4.101[*]Cloud/CC/SC/NC[*][*]Clustername: cluster1[*][eucalyptus.conf](http://paste.ubuntu.com/700427/)[*][eucalyptus.local.conf](http://paste.ubuntu.com/700429/)[*][/etc/network/interfaces](http://paste.ubuntu.com/700435/)[/list]
[*]Server2:[list][*]eth0: Public Interface 192.168.3.102 (physically attached, but this card is currently **NOT** configured)[*]eth1: Private Interface 192.168.4.102[*]NC[/list]
[*]Server3:[list][*]eth0: Public Interface 192.168.3.101(physically attached, but this card is currently **NOT** configured)[*]eth1: Private Interface 192.168.4.103[*]NC[/list]
[/list]

Commands on Coud/CC/SC/NC-Server
[list]
[*][euca-describe-instances](http://paste.ubuntu.com/700436/)
[*][brctl show](http://paste.ubuntu.com/700438/)
[*][ifconfig](http://paste.ubuntu.com/700439/)
[*][ip addr](http://paste.ubuntu.com/700440/)
[/list]

Thanks

---

