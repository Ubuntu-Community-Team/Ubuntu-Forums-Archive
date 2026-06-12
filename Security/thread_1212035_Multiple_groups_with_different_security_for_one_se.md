---
title: "Multiple groups with different security for one set of directories?"
date: 2009-07-13
forum: Security
---

### Post by jrollf on 2009-07-13
I'm trying to solve a directory access issue at my work, our IT support doesn't seem to be able to come up with a solution.  In a nutshell this is what we need:

starting at a lower level directory and subs, eg

/root/level1/level2/level3/... subs ...

We need to setup two separate groups to have access with different permissions, essentially:

GroupA needs full access (eg read/write/delete/execute)

GroubB needs to have READ ONLY access

The World needs to be restricted from the directory and subs completely. 

The directory needs permission equivalent to chmod 750, but somehow we need the entire GroupA to have read write access not just the "owner".  Is there a way to make GroupA the owner of the directories instead of the individual user that created it?  Any other bright ideas?

Our IT tried to tell us to have one group with read/write access and just set it so the world can read (chmod 775), but that would be a contract violation (gives access to non cleared personnel).

Thanks!
John

---

### Post by movieman on 2009-07-13
You probably need to look into either ACLs or SELinux.

---

