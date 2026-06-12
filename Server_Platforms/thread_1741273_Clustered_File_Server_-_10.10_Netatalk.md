---
title: "Clustered File Server - 10.10 Netatalk"
date: 2011-04-27
forum: Server Platforms
---

### Post by kyleh0000 on 2011-04-27
Hi All,

I have been searching the net and these forums for quite a while now and I have not yet been able to come up with an answer so i though I would create a thread for it :)

What im trying to achieve is an clustered server setup to run Netatalk file services. Im planning to start off with a simple 2 node load balanced cluster just for dev/testing but the production system will have up to 8 nodes.

I have been following this guide to set it up however I have hit a problem...

[https://wiki.edubuntu.org/ClusterStack/Natty](https://wiki.edubuntu.org/ClusterStack/Natty)

when run "sudo drbdadm dump export" to verify my /etc/drbd.d/export.res file i get the following error 
 
drbd.d/export.res:1 Prase error: '[' expected,
but got ';' (TK 59)

So to me this is a syntax error I have tried a few things such as replacing the ';' with '[' but that causes all sorts of other problems.

Im relatively new to cluster administration, but i am very familiar with linux, we are using SLES but only because we have a support contract with Novell but that is now gone and I would like to move to Ubuntu.

As i said the end result needs to be a load balanced Netatalk cluster for serving out MAC users, if anyone knows of a better guide or HOWTO on doing this your help would be greatly appreciated.

Thanks!

---

