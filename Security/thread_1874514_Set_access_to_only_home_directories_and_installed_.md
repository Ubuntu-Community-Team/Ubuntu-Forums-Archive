---
title: "Set access to only home directories and installed applications"
date: 2011-11-03
forum: Security
---

### Post by frozen.fire on 2011-11-03
I'm trying to set up a new environment on ubuntu 10.04 for a few users and i need to restrict their access to only their own home folder and the installed applications. 

I thought, changing permissions to 700 or 750 on their home directories would help but it started giving a failed login so i didnt even touch the permissions of other folders on the filesystem. I have reverted the permissions to default but it is not helping. Im still at the same place where i started.

I also have a group for these said users, if it helps.. Please ask me any details if you need to know, im so confused that i don't even know what all should i post to begin with... :(

I already messed up my ubuntu once and had to reinstall..Please help...

---

### Post by cariboo on 2011-11-03
Setting the permission of the home directory to 700 is all you need to block access by other users except for root. Don't set the permissions of everything in the home directory to 700.

If you are experimenting, I'd suggest using virtualbox to create a vm if your system has the resources. That way, all you have to do is create a snapshot of the default install, then make all the changes you want, if you make a mistake, you can revert to the original snapshot, and start over.

---

### Post by frozen.fire on 2011-11-04
Thanks for the tip cariboo907.. I'm already on a VM this time and have a snapshot too. I understand that setting the permissions to 700 on home directory (not recursive) should be enough. I tried that but didn't succeed in it as the user was not even able to login (using xrdp) from his windows machine. it showed an error "password failed". however, when i reverted the changes, he could successfully login again.

Has that something to do with the remote login session(i really fail to understand how..!!), i tried to login the user locally which also failed.

I know i can use rbash to restrict the access but that's not secure and i messed up my ubuntu (fstab) last time when i tried to use acl. I'm currently staying away from these options. I'm actually a fairly new user as far as acl are concerned.

Any suggestions..??

---

