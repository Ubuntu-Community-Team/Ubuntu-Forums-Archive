---
title: "Samba question"
date: 2010-04-24
forum: Server Platforms
---

### Post by Lokro on 2010-04-24
I'm using ubuntu server 9.10 for a home build NAS. Everything is working great just have one more thing to figure out. I have Samba set up to access my files and I set up a recycle feature so anything deleted will get moved to a Recycled folder.  (I learned this the hard way after hitting delete key by accident while browsing the shares in windows. Lost 100 GB of data)

Now it is for the most part working but the permissions on folders isn't getting set right. If I delete a file in a share I can go to Recycle bin folder and delete the file for good. But if I delete a folder I can not access that folder to delete or restore from the Recycle bin folder. I have to chmod the folder before I can do anything with it. Anything I can change to get folders deleted via windows to have the right permissions when it is moved to the Recycle bin folder?

```

[global]
    workgroup = WORKGROUP
    os level = 20
    writeable = yes
    guest only = yes
    public = yes
    preferred master = no
    interfaces = lo eth0
    bind interfaces only = true
    security = share
    guest account = matt

[Media]
    comment = Media
    create mode = 777
    path = /nas/Media
    directory mode = 777
          vfs object = recycle
              recycle:repository = /nas/Recycle Bin
              recycle:keeptree = Yes
              recycle:touch = Yes
              recycle:versions = Yes
              recycle:maxsixe = 0
              recycle:exclude = *.tmp
              recycle:exclude_dir = /tmp
              recycle:noversions = *.doc
[Backup]
    comment = Backup
    create mode = 777
    path = /nas/Backup
    directory mode = 777
          vfs object = recycle
              recycle:repository = /nas/Recycle Bin
              recycle:keeptree = Yes
              recycle:touch = Yes
              recycle:versions = Yes
              recycle:maxsixe = 0
              recycle:exclude = *.tmp
              recycle:exclude_dir = /tmp
              recycle:noversions = *.doc
[Music]
    comment = Music
    create mode = 777
    path = /nas/Music
    directory mode = 777
          vfs object = recycle
              recycle:repository = /nas/Recycle Bin
              recycle:keeptree = Yes
              recycle:touch = Yes
              recycle:versions = Yes
              recycle:maxsixe = 0
              recycle:exclude = *.tmp
              recycle:exclude_dir = /tmp
              recycle:noversions = *.doc
[Pictures]
    comment = Pictures
    create mode = 777
    path = /nas/Pictures
    directory mode = 777
          vfs object = recycle
              recycle:repository = /nas/Recycle Bin
              recycle:keeptree = Yes
              recycle:touch = Yes
              recycle:versions = Yes
              recycle:maxsixe = 0
              recycle:exclude = *.tmp
              recycle:exclude_dir = /tmp
              recycle:noversions = *.doc
[nzb]
    comment = nzb
    create mode = 777
    path = /nas/nzb
    directory mode = 777
          vfs object = recycle
              recycle:repository = /nas/Recycle Bin
              recycle:keeptree = Yes
              recycle:touch = Yes
              recycle:versions = Yes
              recycle:maxsixe = 0
              recycle:exclude = *.tmp
              recycle:exclude_dir = /tmp
              recycle:noversions = *.doc
[Recycle Bin]
    comment = Recycle Bin
    create mode = 777
    path = /nas/Recycle Bin
    directory mode = 777
```

---

### Post by windependence on 2010-04-24
Try using a write list for users or groups you want to be able to access folders in the recycle share. 
Groups are defined like this:

```
write list = @users
```

While you can also define individual users this way:

```
write list  = admin, root
```

Here is the section from the SAMBA docs:

> **write list (S) **


     This is a list of users that are given read-write access to a  service. If the      connecting user is in this list then they will be given write  access, no matter      what the [read only]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#READONLY") option is set to. The list can      include group names using the @group syntax.     
     Note that if a user is in both the read list and the write list then  they will be      given write access.     
     By design, this parameter will not work with the      [security = share]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY") in Samba 3.0.     
Default: *[I]write  list* = [/I]



Remember to restart the services (nmb and smb) after you make the changes.

Good luck!

-Tim

---

