---
title: "UEC CD install: login on node? default user/password?"
date: 2010-11-06
forum: Ubuntu Cloud and Juju
---

### Post by captaincomic on 2010-11-06
Hello!

I am trying to set up a simple cloud with two machines with the Ubuntu 10.04 Server Edition CD. The first machine will be the front end with  cloud controller, cluster controller, storage controller and walrus. The second will be a node with only the node controller installed.
I'm strictly following this guide [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

When installing the front end I get prompted for a user name and password.
But when installing the node controller, there is no prompt at all. I had some difficulties setting up the cloud and wanted to take a look in the config files and log files on the node. But without a password I cannot login the node machine. I can connect with ssh to an instance running on the node, but not to the node itself (again I would need a user/password).

Is this the intended behaviour? Why is the admin not given login information for the node machine?
Or are is there a default user name and password? (I searched the web, but all I found was the default user/password for the web interface of the front end - admin/admin)

Thank you for any help!

---

### Post by kim0 on 2010-11-06
hey there, not quite sure what the password is, perhaps you can reset it to a password you know. Check out these instructions
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Let me know how it goes

---

### Post by captaincomic on 2010-11-27
Thanks for this tip, I haven't tried it yet, as the cloud was working, and I didn't want to mess it up again :).
But I guess it would work this way.

Btw. I noticed that if you install the node controller, and the cluster controller is *not* found during the installation, you *do* get prompted for a username and password - which makes sense, as in this case you would need to configure the node by hand.

Still, I don't get why you are not given a chance to create a user, when the cluster controller is found. Should I file a bug report about it?

---

### Post by kim0 on 2010-11-29
Well, it's always safe to file a bug report when in doubt ;)

---

