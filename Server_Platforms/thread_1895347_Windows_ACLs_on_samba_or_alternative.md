---
title: "Windows ACLs on samba or alternative?"
date: 2011-12-14
forum: Server Platforms
---

### Post by floobit on 2011-12-14
I need to be able to set up samba homedir shares with read and delete only permissions.  I do not want users making new files or modifying existing files.  Is there a way to do this with samba?  the NFSv4 ACLs support this, but they look a wee bit experimental, and samba does not have support for them.  

I already have samba set up and working and was compiled with acl support.  

Context: a database drops reports into user homedirs.  I do not want them modifying the reports, but want them to be able to delete them at their convenience.  I also don't want them to use the homedirs for extraneous junk.  So: read only + delete.  

This would not necessarily need to be file or folder specific.  I'd be reasonably happy enabling read only + delete as a policy for every share from the machine.  

How would you suggest enabling delete-only permissions on a share?  

Thanks

---

### Post by floobit on 2011-12-15
Ok, so it's now clear I did not finish reading the smb.conf doc.  There are options for doing precisely this.  Specifically, it looks like I want:
readonly = yes
delete readonly = yes

The readonly aspect works great.  Unfortunately, adding these options does not allow me to delete files from the samba share when it's mounted in Win7.  It says I need permissions from the owning user (which is how I authenticated for mounting the drive).  

Thoughts?

---

