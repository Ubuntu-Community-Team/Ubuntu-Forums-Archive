---
title: "attempt to get boot images does nothing (14.04)"
date: 2014-05-01
forum: Ubuntu Cloud and Juju
---

### Post by Graham_Irvine on 2014-05-01
Hi

Long term Linux admin (SUSE) so might be missing a higher level trick here than a simple maas set up issue. 
Looking at Ubuntu cloud stack and getting stuck here with getting boot images so admit the server admin stuff is also having to be picked up along the way.

Background . This is a 14.04LTS server install on a VMWARE esxi 5.5 host.

I have got MAAS up and running on what is currently a region and cluster controller as a starting off point.
Had a few issues with networking config which dont belong here but at this point I have all networking fixed . Routing and DNS etc.

So the WebUI MAAS/clusters is showing me  Name=Cluster master   Managed Interfaces=0  Boot images=0 (with an warning triangle saying this cluster has no boot images)  Nodes 0
Clicking on "Import boot images" no reaction and no errors but no Boot Images either.

From checking server itself nothing is being downloaded .

From the command line with a profile correctly paired up etc the following happens.

graham@vm-ubuntu-01:~$ maas my-maas node-groups import-boot-images
Import of boot images started on all cluster controllers

so far so good.

Nothing seems to be logging into /var/log/maas logs that I would say is significant here . (No errors).

What does appear to be happening so far only is a *.part file has appeared in /var/lib/maas/boot-resources  
but its stopped being added too , the file is  around 3.3M

Out of ideas for now with searching , no reports in the wild of this type of issue . 
Not many reports of anything on 14.04 in fact , Seems mostly people might still be using v12 . 
Have I jumped in too bleeding edge here ?

Thanks for any pointers.

---

### Post by Graham_Irvine on 2014-05-03
Update :  

Without really doing anything apart from leaving it alone It appears that yesterday around 16:11 UTC a load of root images and other files appeared in /var/lib/maas/boot-resources/cache. 
Front end still however reporting no boot images. 

I am seeing very little replies to technical questions in this forum (what replies have been made seem to be only non tech replies) and a very high percentage of unanswered questions.  
Is there a better forum somewhere for that level of community discussion/support?

---

### Post by heroddaji on 2014-05-15
i also having some problems with it, if u use this command, you can see some feedback:
 sudo maas-import-pxe-files

---

