---
title: "New to Ubuntu and Ubunto cloud - having basic problems accessing new VMs"
date: 2014-08-25
forum: Ubuntu Cloud and Juju
---

### Post by serge8 on 2014-08-25
Hi guys, 
I posted the message below on the beginner forum, as advised by the forum rules on my first post, and was told to post it here for better details and a better chance of solving my issue:

I am brand new to Ubuntu and everything that comes with it, my apologies if this question sounds a bit simple. 

After installing Ubuntu Desktop 14.04, I followed the guidelines of the post below to install a single machine openstack cloud:
[http://astokes.org/ubuntu-openstack-installer/](http://astokes.org/ubuntu-openstack-installer/)

with the stuff mentioned there, I was able to run cloud-install without any trouble. 

I see that it has created several virtual machines functioning as different OpenStack nodes (controller, compute, Neutron, etc).

My problem is as follows - when trying to create a new VM through the Horizon browser interface, I get an error saying the following:

Error: Failed to launch instance "i1": Please try again later [Error: No valid host was found. ].

I googled around and learned that this error is commonly associated with lack of resources, but that is simply not the case here.


I wanted to see the feedback from the openstack services themselves but I am not able to ssh into the VMs that cloud-install created that are running these services. 


How do I get to these VMs?
I tried SSH ing with no response, I tried ssh-copy-id to get my public key there, but got a permission denied error. 

I can ping the VMs fine, they are responding. 

So, how do I get into these VMs running the openstack services?
The forum rules said that since this is my first post, I should post here.


Thanks in advance

---

### Post by chris240 on 2014-09-03
Hi,

Try adding in nova.conf "scheduler_default_filters=AllHostsFilter" in the nova cloud-controller server or in juju-gui in config flags string try add it there.

---

### Post by adam-stokes on 2014-09-05
> **serge8 said:**
> 

My problem is as follows - when trying to create a new VM through the Horizon browser interface, I get an error saying the following:

Error: Failed to launch instance "i1": Please try again later [Error: No valid host was found. ].


In horizon dashboard you should have several floating ip's available. You'll want to associate a floating ip before you can ssh into your newly created instances.

HTH and feel free to reach out to us on irc.freenode.net / #ubuntu-solutions

Adam

---

