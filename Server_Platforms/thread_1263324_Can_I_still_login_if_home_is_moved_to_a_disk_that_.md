---
title: "Can I still login if /home is moved to a disk that crashes"
date: 2009-09-10
forum: Server Platforms
---

### Post by dougalmcshlong on 2009-09-10
Am building a Ubuntu family domain server using Samba for Windows/Linux clients - trying to get the setup right.
 
Have decided that I will have a seperate disk (which will be backed up) for all user files so that if the system disk crashes I can just replace and reinstall (I actually made a ghost).
 
The question is this...
 
Let's say I login to account called sysadmin and move the /home partition (I know there are plenty of howto's) to the new user disk, and the user disk crashes at some point, will I still be able to login to sysadmin to replace and restore the userdisk from backups? Surely the /home for sysadmin will be absent. Won't that create problems?
 
Part 2 of the question then is, what is so magical about /home? Surely if I leave /home alone so sysadmin will always work. Then create /userhomes on the new disk, and when I do adduser, use the -b hook to state that the homes will hang off the base dir /userhomes.
 
Wouldn't that be better? Am I missing something about /home?
 
Sorry if I've misunderstood something - I'm still fairly new to all this.

---

### Post by lloyd_b on 2009-09-11
> **dougalmcshlong said:**
> Am building a Ubuntu family domain server using Samba for Windows/Linux clients - trying to get the setup right.
 
Have decided that I will have a seperate disk (which will be backed up) for all user files so that if the system disk crashes I can just replace and reinstall (I actually made a ghost).
 
The question is this...
 
Let's say I login to account called sysadmin and move the /home partition (I know there are plenty of howto's) to the new user disk, and the user disk crashes at some point, will I still be able to login to sysadmin to replace and restore the userdisk from backups? Surely the /home for sysadmin will be absent. Won't that create problems?
 
Part 2 of the question then is, what is so magical about /home? Surely if I leave /home alone so sysadmin will always work. Then create /userhomes on the new disk, and when I do adduser, use the -b hook to state that the homes will hang off the base dir /userhomes.
 
Wouldn't that be better? Am I missing something about /home?
 
Sorry if I've misunderstood something - I'm still fairly new to all this.

The only "magical" thing about /home is that some poorly written programs may assume that your home directory is "/home/username" (instead of checking the $HOME environment variable the way they should).

If /home isn't mounted (as in the case of a disk crash), and your sysadmin home directory is "/home/sysadmin", then you will probably get an error on login because the home directory doesn't exist.

What I would suggest is that you create your sysadmin user, specifying a home directory other than in /home (something like /sysadmin) tree.  That way you can tweak /home however you like without problems as long as you're using that user.  By default, the "root" user has a home of "/root" for just this reason.  Since Ubuntu disables the root account for security reasons, doing something similar with "sysadmin" makes sense.

There's no real advantage to setting up your "/userhome" tree - just mount the filesystem on the second disk at "/home", and you get the same effect...

Lloyd B.

---

### Post by dougalmcshlong on 2009-09-16
Awesome. That answers my question perfectly and makes total sense. :)

---

