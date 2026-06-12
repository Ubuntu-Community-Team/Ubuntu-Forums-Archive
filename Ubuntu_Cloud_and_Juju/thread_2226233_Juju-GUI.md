---
title: "Juju-GUI"
date: 2014-05-26
forum: Ubuntu Cloud and Juju
---

### Post by Veeresh_Hiremath on 2014-05-26
Hi All,

I bootstrapped my maas environment and then used juju quickstart to deploy juju-gui. I am able to succesfully install and open the web gui page.

While I am deploying a openstack charms (say - Keystone), I see it creates a new machine and then the service(keystone) is deployed on top of it .

Both my machine and services are in pending state. 

However If i manually deploy the services using "juju --to 1 deploy keystone" . I then see it in GUI.

Question:
1) Why juju-gui creates a new machine when a service is deployed . Why it does not use the existing machines I configured already 
2) Is there no way to view the machine details on juju-gui

---

### Post by sam-c on 2014-06-03
We had Mark Shuttleworth at openstack Israel do june 2 2014 
Very interesting , Hope your question gets a Reply soon.:D

---

