---
title: "ubuntu cloud setup in vmware/virtualbox"
date: 2011-07-01
forum: Ubuntu Cloud and Juju
---

### Post by tanveer on 2011-07-01
Hi everyone,
I was recently looking into the cloud setup of ubuntu and now would like to setup in my laptop. but in the docs it's mentioned that minimal setup requires at least 2 physical machines. 
So that means I can't setup the front-end controller and one node in vmware/virtualbox? But as I have only 1 laptop so is there any way around? I just need the controller and one node to test something.

Thanks in advance

---

### Post by kim0 on 2011-07-02
This will not be easy. You may be able to run the cloud controller inside a VM, but the node controller needs a physical machine (since nested virtualization is not too mature). The other option is to run UEC on Ec2 like
[http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html](http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html)

Or consider running the openstack cloud. It's the default for 11.10 and runs on a single vbox machine 
[http://wiki.openstack.org/NovaVirtually](http://wiki.openstack.org/NovaVirtually)

---

### Post by tanveer on 2011-07-05
Hi thanks for your reply.
first let me clear my understanding as I just started in this cloud field.
Lets say, a company want to host their website and database in cloud and to visualize that I am building a cloud with one controller and one node only. Now first thing why the node is needed? Is it where the database and web contents wil be stored and it will run apache server? Then controller is only for controlling this node; here control means what actually?

Thank you in advance.

---

### Post by kim0 on 2011-07-07
Controller is really needed to keep the cloud itself alive, doing the management "paper" work for the cloud itself to function. However, the "node controller" is the machine(s) that runs VMs and those VMs host your application (mysql, apache ...etc)

If you're just testing, it might be easier to spin up amazon ec2 servers and play with those instead though

---

### Post by tanveer on 2011-07-13
Thanks for the reply. 
I have installed Ubuntu 11.04 cloud in my VMWARE just for testing. Now after installing in the /var/log/eucalyptus/registration.log it keeps saying .. [PHP]4277 -> Cluster cluster1 doesn't exists, retrying in 10 secords[/PHP]
It has 512MB RAM and 8GB disk space . Is it because of the small disk space it can't create the cluster and giving this error ?

thanks.

---

