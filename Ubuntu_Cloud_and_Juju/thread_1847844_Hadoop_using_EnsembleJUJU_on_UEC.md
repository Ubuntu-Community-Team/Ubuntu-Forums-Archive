---
title: "Hadoop using Ensemble/JUJU on UEC"
date: 2011-09-21
forum: Ubuntu Cloud and Juju
---

### Post by rohitkondekar on 2011-09-21
Is it possible to deploy hadoop on UEC using ensemble? or any other tool? 
Can somebody please also guide me regarding what slave node addresses we have to give while simple deploying on cloud (means by using custom images).

---

### Post by castrojo on 2011-09-21
Unfortunately no. But we've got it working on EC2. 

Mark Mims has the charms/formulas to get it running on Openstack that you can browse here if you're looking at playing with it: [https://code.launchpad.net/~mark-mims](https://code.launchpad.net/~mark-mims)

However none of it is ready for production to run on an internal cloud just yet, however Mark and Clint have it running already on openstack. 

This will be ready for 11.10 though, and once we have something you can play with we'll post it on cloud.ubuntu.com.

---

### Post by rohitkondekar on 2011-09-23
> **castrojo said:**
> Unfortunately no. But we've got it working on EC2. 

Mark Mims has the charms/formulas to get it running on Openstack that you can browse here if you're looking at playing with it: [https://code.launchpad.net/~mark-mims](https://code.launchpad.net/~mark-mims)

However none of it is ready for production to run on an internal cloud just yet, however Mark and Clint have it running already on openstack. 

This will be ready for 11.10 though, and once we have something you can play with we'll post it on cloud.ubuntu.com.

Thank you for clearing my doubt. :razz:

---

