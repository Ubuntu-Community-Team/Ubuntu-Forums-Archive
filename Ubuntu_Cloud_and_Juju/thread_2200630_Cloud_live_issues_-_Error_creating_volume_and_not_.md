---
title: "Cloud live issues - Error creating volume and not able to ping instances"
date: 2014-01-20
forum: Ubuntu Cloud and Juju
---

### Post by smakam on 2014-01-20
Hi
I installed Ubuntu cloudlive image in Virtualbox. 
Based on reading gettingstarted.txt, I did the following:
nova-setup.sh
start-openstack.sh
added the cirros image to glance.

I did not setup eth0 since I had dhcp already configured in Virtualbox. gettingstarted.txt mentioned the same.

I opened horizon and I created a cirros mini instance. I am facing the following issues:
1. I see error message "Unable to fetch volumes" as soon as I login into horizon.
2. When I try to create volume, I get error message "error creating volume" and volume does not get created.
3. I created instance and associated with security group to enable icmp and tcp traffic. I see that ip address 172.20.1.2 is allocated to the instance but I am not able to ping that ip address from my host ubuntu machine. I am also not able to ssh. 

In the host log, I see the error message as specified in the attachment.

Can someone help me with this.

Thanks
Sreenivas

---

