---
title: "VMware Server with Ubuntu Server access denied"
date: 2008-11-05
forum: Virtualisation
---

### Post by cane1832 on 2008-11-05
Ok,

So I setup a Ubuntu Server to run a VMware server. It runs great. The problem i am having is it is setup for 3 users to use it. If one installs a guest no other user has the right to take down or bring up the vm image. 
I have chmod the directory of the virtual hard drives to 777 and still no luck. Any input will be greatly appreciated.

Thanks

---

### Post by cane1832 on 2008-11-05
just found the solution. You have to do a chgrp to the dir

sudo chgrp -R groupname /media/vhds

hope this helps someone down the road.

---

### Post by cane1832 on 2008-11-05
ok i will add that you have to chmod the directory so that it has rwx. Everytime a user creates a vmware guest they have to do that to the dir created by vmware for the guest os. 

if anyone knows how to get it to set rwx for all users when creating a guest os please post reply.

---

### Post by cane1832 on 2008-11-05
So i tried changing the umask in /etc/profile for all users to 0000
when i mkdir i get full wrx across the board. but when vmware makes the directory it doesn't apply the umask i set. 

is there a location within vmware or anywhere else that umask value can be changed to take this affect in vmware server console when creating a guest os

---

