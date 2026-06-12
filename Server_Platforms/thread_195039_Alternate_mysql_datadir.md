---
title: "Alternate mysql datadir"
date: 2006-06-12
forum: Server Platforms
---

### Post by bohboh on 2006-06-12
I have a fat32 partition which stores all my work files, i mount it with read and write permissions for the current user, me and not root. This works ok and i can read and write my files.

The problem is that my mysql data directory is also there and when it mounts it, it needs it to be mounted as mysql:mysql and not the current user.

So my question is, can i mount directories within drives. I have tried creating a symbolic link to the directory 

e.g. mysql -> /windows/share/mysql

but it gets created as root , not mysql and i cant change it, doing a

sudo chown mysql:mysql ./mysql returns a not allowed error.

How do i change the mysql datadir to point to the windows share? Its all to do with permissions which i cant seem to change.

---

### Post by bohboh on 2006-06-12
I have managed to sort this, in a fashion.

I created symbolic links to the actual data directories for each database within mysql's data directory.

So the data directory is

/var/lib/mysql

and i have created links to my data directories on my fat32 drive.

e.g.

/var/lib/mysql/mydatabase -> /windows/share/mysql/mydatabase

Which for me seems to work.

Hope that helps others.

---

