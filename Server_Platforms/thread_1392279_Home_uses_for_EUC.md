---
title: "Home uses for EUC?"
date: 2010-01-27
forum: Server Platforms
---

### Post by cdcoley on 2010-01-27
As someone relatively new to Ubuntu I am very curious to know for what purposes a person might build a private cloud using EUC?   Could an LTSP server be placed on it allowing 10 or 15 people to access it?   Are there any home business possibilities for building something like this?

Any response would be welcome..

Thanks

---

### Post by yogesh.girikumar on 2010-02-02
Hi,


       To define cloud in its simplest form, cloud computing consists of shared computing resources that are virtualized and accessed as a service, through an API. Cloud computing is the term for the computations performed on the cloud, that lies somewhere out there.


       UEC is short for "Ubuntu Enterprise Cloud". Ubuntu Enterprise cloud is an implementation of Eucalyptus using KVM, which is an infrastructure that helps in implementing a cloud computing model on a computing cluster. Eucalyptus offers an API compatible with the APIs provided by Amazon Web Service(AWS). UEC has a bunch of tools that are useful in spawning, managing and controlling virtual machines, clusters and nodes.


       A cloud can provide computational power on demand. It also provides for dynamic allocation of physical resources to the virtual instances ( which is called 'On Demand Scalability' ). This is required in case of applications that utilize heavy resources and those that are constantly in need of varying amount of resources.


       Most of the time, one would not need to build a cloud at home, unless it's for learning or experimentation. You can have a look at the following links, which might give you an insight about this subject:


       1. [http://www.appistry.com/cloud-info-center](http://www.appistry.com/cloud-info-center)
2. [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private)
3. [http://en.wikipedia.org/wiki/Cloud_computing](http://en.wikipedia.org/wiki/Cloud_computing)

---

