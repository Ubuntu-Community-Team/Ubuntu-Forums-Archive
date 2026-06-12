---
title: "YP Server fails to bind"
date: 2009-02-12
forum: Server Platforms
---

### Post by bean72 on 2009-02-12
Hi guys,

I am trying to get an NIS server up and running in Ubuntu 8.10. I have used the following guide to do this:[http://https://help.ubuntu.com/community/SettingUpNISHowTo]("http://https://help.ubuntu.com/community/SettingUpNISHowTo")

The problem is that when i finally get it all configured and I try to start NIS services for the first time, it fails when it attempts to bind with yp server. I have tried this before, right after the official launch of intrepid and I ran into the same problem, but with everyone else's trouble after the release, my post got lost in the forums. :)

These were both fresh installs, I have not tried to install anything else before NIS.

By the way, I don't know if this is any error to be concerned about, but building the DB for the first time got me this:
```
jeff@jeff-nfs:~# /usr/lib/yp/ypinit -m

At this point, we have to construct a list of the hosts which will run NIS
servers.  jeff-nfs is in the list of NIS server hosts.  Please continue to add
the names for the other hosts, one per line.  When you are done with the
list, type a <control D>.
	next host to add:  jeff-nfs
	next host to add:  
The current list of NIS servers looks like this:

jeff-nfs

Is this correct?  [y/n: y]  y
We need a few minutes to build the databases...
Building /var/yp/jeff-nfs/ypservers...
Running /var/yp/Makefile...
make[1]: Entering directory `/var/yp/jeff-nfs'
Updating passwd.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating passwd.byuid...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating group.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating group.bygid...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating hosts.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating hosts.byaddr...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating rpc.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating rpc.bynumber...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating services.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating services.byservicename...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating netid.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating protocols.bynumber...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating protocols.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating netgroup...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating netgroup.byhost...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating netgroup.byuser...
failed to send 'clear' to local ypserv: RPC: Program not registeredUpdating shadow.byname...
failed to send 'clear' to local ypserv: RPC: Program not registeredmake[1]: Leaving directory `/var/yp/jeff-nfs'

jeff-nfs has been set up as a NIS master server.
```

Any help with this would be greatly appreciated.

Thanks,
Jeff

---

### Post by bean72 on 2009-02-13
Hi again,

Would it be better for me to use an LDAP server rather than NIS, either one will work for me as I just want my server to handle all users and groups, and I also want to run an NFS server.

I can see more documentation for LDAP, but which would be the best path to take?

Thanks

---

### Post by iamkmac on 2009-03-18
anyone have any incite on this issue? i have run into the same problem on a fresh install.

added my ip and nis clients to /etc/hosts.allow under portmap ypserv and ypbind then ran sudo apt-get install portmap nis

on installation if nis i get:

```
* Starting NIS services
* binding to YP server...
* ....
* ....
* ....
* ....
* ....
* ....
* ....
* ....
* ....
* ....                                     [fail]
                                           [ OK ]
```

---

### Post by iamkmac on 2009-03-18
i was able to find a fix.

after the YP binding fails you need to edit /etc/default/nis and set NISSERVER.

once you have done this, run /usr/lib/yp/ypinit -m

once this is complete you can run /etc/init.d/nis start with no errors.

---

