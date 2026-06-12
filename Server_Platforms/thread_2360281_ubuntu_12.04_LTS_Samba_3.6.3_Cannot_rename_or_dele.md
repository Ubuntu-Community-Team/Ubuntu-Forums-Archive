---
title: "ubuntu 12.04 LTS Samba 3.6.3 Cannot rename or delete owned files/folders"
date: 2017-05-03
forum: Server Platforms
---

### Post by Walter_ZAMBOTTI on 2017-05-03
I have inherited an Ubuntu server 12.04 LTS with Samba 3.6.3 that has a simple share setup used by windows users.

The smb.conf (relevant sections) looks like this

security = user 

( I have also tried the above line commented out. )

```
[staff]
  comment = Staff Directories
  path = /mnt/USERDATA/Staff
  read only = no
  guest ok = yes
  inherit permissions = Yes
  guest account = the_staff

/etc/passwd
the_staff:x:1000:1000:the_staff,,,:/home/the_staff:/bin/bash

/etc/group
the_staff:x:1000:

ls -l /mnt/USERDATA
drwxr-xr-x 31 the_staff the_staff 4096 May 3 10:15 Staff


Windows users can create files but cannot rename them (permission error) or delete them.
If they attempt to use windows to create a new folder it creates 4 new folders instead and
of course none of them can be renamed or deleted.

They can however they can get around this by creating a new folder on the windows system
and dragging it over to the samba share, then it gets the expected name.

When new files/folders are created they appear to have the correct permissions:

ls -l /mnt/USERDATA/Staff
drwxr-xr-x 2 the_staff the_staff 4096 May 3 10:31 New Folder
drwxr-xr-x 19 the_staff the_staff 4096 May 3 10:31 New Folder (2)
drwxr-xr-x 5 the_staff the_staff 4096 May 3 10:31 New Folder (3)
drwxr-xr-x 20 the_staff the_staff 4096 May 3 10:31 New Folder (4)
-rwxr-xr-x 1 the_staff the_staff 4096 May 3 10:32 New Text Document .txt

```
What am i missing here?

---

### Post by wildmanne39 on 2017-05-03
*Thread moved to **Server Platforms**.*

12.04 is no longer supported there will be no updates not even security so I recommend upgrading to 16.04 then figure out your issue.

---

### Post by Walter_ZAMBOTTI on 2017-05-05
I have a test 16.04 server and it exhibits the same behaviour so in the spirit of providing a solution and not excuses...

The solution was to add the following entries to the service
  force user = tcs_staff
  force group = tcs_staff

---

