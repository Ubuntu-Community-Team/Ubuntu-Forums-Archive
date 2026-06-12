---
title: "I know what i want, but i know not what its called..."
date: 2011-01-07
forum: Server Platforms
---

### Post by triunenature on 2011-01-07
I have ubuntu 10.10 server, and 3 computers running ubuntu 10.10 desktop ed.

All i am looking to do is to have one set of usernames/passwords for all the computers.  With the directories being mirrored.

So a user can login to computer one, download a file, walk over to computer 2, login and then edit the file, then walk over to computer 3 and do (insert random thing) with the file.

The main key is, when i want to add a user, i merely go onto the server and add the user, and not have to do the same with all 3 computers.

Is this possable?  I'm 99% sure i've seen it done.  I just don't know how.

If you even just give the name of the concept, i don't mind researching it, and doing the work myself.

---

### Post by Girya on 2011-01-07
> **triunenature said:**
> I have ubuntu 10.10 server, and 3 computers running ubuntu 10.10 desktop ed.

All i am looking to do is to have one set of usernames/passwords for all the computers.  With the directories being mirrored.

So a user can login to computer one, download a file, walk over to computer 2, login and then edit the file, then walk over to computer 3 and do (insert random thing) with the file.

The main key is, when i want to add a user, i merely go onto the server and add the user, and not have to do the same with all 3 computers.

Is this possable?  I'm 99% sure i've seen it done.  I just don't know how.

If you even just give the name of the concept, i don't mind researching it, and doing the work myself.

don't quite understand what you're after but centralized logins from one server: LDAP

---

### Post by vortmax on 2011-01-08
I just got this running on my network and it's easy. 

If all of these computers are on your local LAN, then the easiest way to set it up is with NIS.  Here is a good write up:
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

Basically you setup a NIS server with the users and groups you want for the cluster.  The other servers authenticate back to this server over the network.  To the end user, it appears no different from a traditional unix login.  The issue is that it is very insecure, so make sure to lock down the traffic and only run it if your LAN is trusted.  For what it's worth, you can do it in LDAP too, but it's MUCH more complicated.  It took me a full day to get openLDAP up and running on the server, but only 2 hours to get 4 machines synced with NIS (once I gave up on ldap).

For the shared directories, use NFS.  This is a good write up on setting up NFS:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

having spent the past week working out the bugs, I can offer some advice.  When you export your home dir, use these options (this is my full export line):

```

/mnt/homes 192.168.30.0/24(rw,sync,no_subtree_check,no_root_squash)

```

and when you mount your home dirs on the remote machines, make sure you use the vers=3 option.  I had serious issues with it exporting the wrong UID's without it.  The nolock fixes a lockfile issue with firefox.

```

xxx.xxxx.xxxx:/mnt/homes /home nfs defaults,vers=3,nolock 0 0

```


Some other words of wisdom:
Make sure that your UID and GID's are the same across all systems.  Also, when you setup NIS, the server will still attempt local auth first, then query the NIS server, so if you already have all of your users setup on all of the machines, it won't do much for you.  My suggestion is to get your users and groups on your head node setup, then purge your "client" servers of all non-system users and groups EXCEPT FOR ONE SUPERUSER (so you can locally login if your NIS server goes down).  Configure the clients one by one and check to make sure file permissions are still okay (NFS home directories make this easier).  

You'll also want to make an alias for all users (just throw it in /etc/skel/.bashrc) to change passwd to yppasswd. (alias passwd='yppasswd').  Since you are authenticating over NIS now, passwd will only update the local machine's passwd database (for which there probably isn't an active user).  yppasswd is the nis aware version of the command.

It's really not that difficult, but there are a few gotcha's along the way.  Let me know if you have any difficulties.

---

### Post by triunenature on 2011-01-27
Sorry it took so long, Thank you for the help!

---

