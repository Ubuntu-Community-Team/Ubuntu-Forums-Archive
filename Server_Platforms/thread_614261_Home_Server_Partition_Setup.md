---
title: "Home Server Partition Setup"
date: 2007-11-15
forum: Server Platforms
---

### Post by Shiva88 on 2007-11-15
Quick question about directory setup conventions for servers.  Right now I've got an old XP2800+ box running a simple file server under Windows XP with two hard drives- one 20GB hosting the OS, and one 250GB that holds all the files.  I want to migrate this machine over to ubuntu, but I'm unsure of how/where these drives should be partitioned/mounted.  

Is there any convention on where the shared data is located on a file server?  Does it just reside within a user's home directory?  Or do people usually create a new top-level directory, such as /Share?  

Also, who should have ownership of the files?  Do I just create user Shiva88 and give him ownership of everything, and use those credentials when I need to access the data?

The only caveat is that I may wish to also setup additional services from this box; most likely HTTP for wiki's and the like.  That data would also be located on the 250GB drive, so Apache needs to be able to access the drive as well.

Right now this will only be a single hard drive, but in the near future I would like to move to a RAID setup.  That's beyond the scope of my question here, but I wanted to mention it in case it effects where I should put the data now.

---

### Post by jflaker on 2007-11-15
> **Shiva88 said:**
> Quick question about directory setup conventions for servers.  Right now I've got an old XP2800+ box running a simple file server under Windows XP with two hard drives- one 20GB hosting the OS, and one 250GB that holds all the files.  I want to migrate this machine over to ubuntu, but I'm unsure of how/where these drives should be partitioned/mounted.  

Is there any convention on where the shared data is located on a file server?  Does it just reside within a user's home directory?  Or do people usually create a new top-level directory, such as /Share?  

Also, who should have ownership of the files?  Do I just create user Shiva88 and give him ownership of everything, and use those credentials when I need to access the data?

The only caveat is that I may wish to also setup additional services from this box; most likely HTTP for wiki's and the like.  That data would also be located on the 250GB drive, so Apache needs to be able to access the drive as well.

Right now this will only be a single hard drive, but in the near future I would like to move to a RAID setup.  That's beyond the scope of my question here, but I wanted to mention it in case it effects where I should put the data now.

In my last company and my current one, all user 'home' directories are located under a home volume and each share is created below that.  This is for organizational reasons.

The general 'Office' share is on a volume with other shares and sharing permissions are placed on the shares as warranted........Administrator and EVERYONE groups has access to the general share.

All permissions are group based
'Executive' share permitted to Administrators and Executive group
'IT' share permitted to Administrators and IT group
'Marketing' permitted to Administrators and Marketing group
etc

Notice, Administrator group always has access for management and backup purposes

---

