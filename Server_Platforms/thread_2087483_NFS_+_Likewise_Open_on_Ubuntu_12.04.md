---
title: "NFS + Likewise Open on Ubuntu 12.04"
date: 2012-11-23
forum: Server Platforms
---

### Post by ic3000 on 2012-11-23
Hi to all!

I work on a school that until recently was using windows on servers and desktops. We have already migrate all our web services to a ubuntu 12.04 server where we put our moodle and drupal that until now where running on a Windows Server 2003.

With likewise open for AD authentication we have already migrate some desktops, and with pam we are able to let users use windows and ubuntu desktops in a mixed enviroment.

Now we want to start migrating the desktops that don't really need to have any connection to a windows file server and want to implement NFS so users can use whatever computer they need and get the same home folder.

For now we need to keep our windows AD and as i said above with likewise open for authentication this works. But we have a problem with the introduction of a ubuntu 12.04 server with NFS.

The ubuntu 12.04 server is also using likewise to let him know that the AD exists and have access to users and groups so we can get the right permissions to folders.

This works ok but there is one annoying thing that we are unable to resolve... The problem is that Domain Users that are using "exported" home directories to the NFS server don't have sound...

The same user with a local home directory don't have this problem but if he moves to a machine that is configured to use the NFS server the sound just wont work and the system shows no access to audio harware...

This is the only problem we found with this setup and is for now the only detail that is keeping us to get a step closer to put windows out of our network...

Does anyone had this problem before? Is there anyone using NFS with likewise?

Thanks in advance!

---

### Post by JS207 on 2012-11-26
Whilst these instructions utilize another free AD integration utility (Centrify Express), you may find these postings of use
 
[http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Kerberos-ticket-delegation-with-nfs-user-home/td-p/7954](http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Kerberos-ticket-delegation-with-nfs-user-home/td-p/7954)
 
[http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Mounting-NFS-Home-drives-on-startup-causes-problems-to-Centrify/td-p/386](http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Mounting-NFS-Home-drives-on-startup-causes-problems-to-Centrify/td-p/386)

---

