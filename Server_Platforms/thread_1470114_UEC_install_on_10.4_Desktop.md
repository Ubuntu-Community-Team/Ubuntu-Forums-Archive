---
title: "UEC install on 10.4 Desktop"
date: 2010-05-02
forum: Server Platforms
---

### Post by wcorey on 2010-05-02
Hi, 
   I recently installed a Ubuntu Server 10.4 on a new machine. This I installed as a cloud node controller.

   I wanted to use an existing machine running U 9.10 Desktop (which was a cloud controller, cluster controller, storage controller, and Walrus controller) in that same capacity under the newer UEC. The advertising was compelling with respect to the new 10.4 cloud auto registration based upon E 1.6.2 etc etc. My cloud stopped working. 

To make a long story short... Would someone point me at a way to execute the preseed debconf scripts such that I can get the non-node controller configuration set up in the new environment or tell me how I can get a reinstall of the packages to asked the questions and do the config. 

I am stuck as of now.

Thanks,

Walt

---

### Post by wcorey on 2010-05-08
For anyone who happens to come across this thread in search of the same answer, here is the answer..

First, the problem:

EUC was successfully installed on Ubuntu 9.10.
I upgraded to 10.4, in the process the the cloud stopped working.
I tried removing the packages and reinstalling, I was never prompted for config info during install via debconf.
The cloud just plan old stopped working
I thought maybe if I removed all existing conf, from 1.5, that would allow for reasking the questions and rebuilding the confs.
The cloud not only still didn't work, it wouldn't even start.
I tried reinstalling packages again to no avail.

And the answer IS:

Completely remove (purge) the front end packages and then reinstall.
The debconf q&a did take place and the cloud appears to be on its way to working. It did ask for cluster name and it did ask for ip address range. While I do see the cluster name in the cluster config I do not see the address range in the ipaddr config but perhaps it will be there after a restart.

At any rate, the above is what got me past my problem

---

