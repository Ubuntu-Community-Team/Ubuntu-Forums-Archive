---
title: "vsftp cluster on Ubuntu LTS"
date: 2013-11-19
forum: Ubuntu Cloud and Juju
---

### Post by flickerfly on 2013-11-19
I'm pretty fresh to clustering and elsewhere I'm being encouraged to move to RedHat for the purpose of clustering, but ... :(

I want to setup a two member ftp cluster where the /srv and vsftpd config are replicated between the two members. I've been talked out of using a cluster file system and sticking with an active/passive scenario with EXT4 fs. 

The two cluster members will be setup as VMs on a VMWare ESX host. The VMs do not have access to the ESX host for security reasons so my first problem is figuring out how to handle fencing. 

The next problem is that all the documenation I've found is either old (and so not quite right) or incomplete. I'm struggling to put together all the parts with confidence. Even outside Ubuntu, the various parts have changed roles and it seems without understanding the history of how the softwares have developed and grown it is nearly impossible to bring the documentation pieces together into a complete solution.

Can anyone point me in the right direction for current documentation and fencing in VMs without direct host access?

---

