---
title: "Home Server Advice"
date: 2012-11-19
forum: Server Platforms
---

### Post by brianafischer on 2012-11-19
I am looking for some advice on my proposed home server setup.  
[LIST]
[*]Public - User, everyone that has network access (no password required)
   -Guest access
   -Downloaded/Archived TV and Music and Movies (read-only)
[*]Family - Family documents, photos, and videos
-Mom
-Dad
-Son
-Daughter
[*]Parents - Write access to family Group files plus additional separate “parental files location”
-Mom
-Dad
[*]Kids - Parents also have full permissions
-Son
-Daughter
[/LIST]


The Public Group will be for guests over our house on the network.  They should have read-only access to a public folder for information such as movies, tv shows, and documents for neighbors phone numbers, emergency contacts, …

The Family Group will be for direct family only: parents and kids.  Only the     should have write access to the family folder so the kids don’t accidentally delete the family photos.  Eventually when they get older, they should be able to create files and folders.  However, they should never be able to delete a file or folder made by a Parent.

The Parents Group will be for parents only.  Only parents should have access to the parents folder.  The kids should not be able to list or access this directories.  By default, Mom or dad should have full access (read/write/execute) to new files and folders created in this folder.

The Kids Group will be for our son and daughter.  They should not have access to each others files but the parents should have full access to their files.  Files to be shared with the Family should be placed in the Family folder.

All of these folders should be exposed over the network via Samba shares.  It would be nice to have the current windows username and password the same on the Linux server.



Strategy

[LIST]
[*]Users
-Mom
-Dad
-Son
-Daughter
[*]    Groups
-Public
-Family
-Parents
-Kids

[*]    Folders
-/user/mom
-/user/dad
-/user/son
-/user/daughter
-/user/family?
-/user/parents?
-/user/public?
[/LIST]


Questions
I understand the basics of user and group creation, but had a few questions:

[LIST=1]
[*]Where should “group” folders be placed?  Since there is no “family/parents/public” user, where should this shared folder be created?
[*]    How do I setup default access control/permissions for each “group folder” as described above?  Each folder has different requirements for the default permissions when files are placed in the folder.  In addition I would like these permissions to be applied to the samba shares AND local machine.
[*]    Is there a way to implement the Windows 7 “libraries” feature where the group folders and user folders are presented as merged into a single directory structure?  Is UnionFS the suggested way for Ubuntu 12.04?  What package should I install for this?
[/LIST]


Thanks for any advice, I am looking forward to my new server setup.

---

### Post by SeijiSensei on 2012-11-20
> **brianafischer said:**
> Where should &#8220;group&#8221; folders be placed?  Since there is no &#8220;family/parents/public&#8221; user, where should this shared folder be created?

I'd create a "family" user, put everyone in the "family" group and set the permissions on /home/family to 770.

> How do I setup default access control/permissions for each &#8220;group folder&#8221; as described above?  Each folder has different requirements for the default permissions when files are placed in the folder.  In addition I would like these permissions to be applied to the samba shares AND local machine.

You just need to set the right permissions at the operating system level.  Suppose you also create /home/parents.  Then mom and dad would need to be members of the "parents" group, and the permissions on /home/parents should be 770.

You might find the "force group" and "create mask" directives to be helpful in the Samba configuration for this share:

```

[parents]
     path = /home/parents
     valid users = mom, dad
     force group = parents
     create mask = 0770
     [other stuff]

```

Files mom puts there will be owned by mom with group parents and will have full permissions for both her and other members of the parents group. You should probably disable the default [homes] share in smb.conf and set up the exports yourself.

> Is there a way to implement the Windows 7 &#8220;libraries&#8221; feature where the group folders and user folders are presented as merged into a single directory structure?

Can't help with that one, I'm afraid.

---

### Post by rubylaser on 2012-11-20
> **brianafischer said:**
> 
Is there a way to implement the Windows 7 &#8220;libraries&#8221; feature where the group folders and user folders are presented as merged into a single directory structure?  Is UnionFS the suggested way for Ubuntu 12.04?  What package should I install for this?


You could pool the storage with either [mhddfs]("http://romanrm.ru/en/mhddfs") or [AUFS]("http://aufs.sourceforge.net/").

mhddfs is very neat, but runs as a FUSE module, so it's not very fast.  AUFS runs in kernel space, so it's very fast and is lighter on resources, but is not as feature rich as mhddfs.  A Typical AUFS mountpoint would look like this (/etc/fstab).

```
none /storage aufs br:/media/disk1=rw:/media/disk2=rw:/media/disk3=rw:/media/disk4=rw,sum,create=pmfs 0 0
```

You need to have filesystems on each disk you want to pool, and have each of those disks already mounted.

---

