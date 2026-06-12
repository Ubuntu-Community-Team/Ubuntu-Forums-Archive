---
title: "Ubuntu Secure File Permissions With File Permission Lists"
date: 2010-05-21
forum: Security
---

### Post by deere on 2010-05-21
Hello All!

I would advice to use permission list files in Ubuntu like SUSE dose.
Suse has these permission files where all the files are listed with their default permissions.
You can choose between permission policies and can place permission files for programs like postfix in /etc/permissions.d.
You can place explicit permissions for files in /etc/permissions.local.
I think this is a very good solution for the permission problem and it makes a system more secure.
It is also a good solution for the accidentally executing "chmod -R 777 /".

SUSE Permission files / dirs:
/etc/permissions.paranoid
/etc/permissions.d
/etc/permissions.secure
/etc/permissions.easy
/etc/permissions.local
/etc/permissions


You can run a command if you want to reset the permissions or you can run it from cron every day to make sure your files have the right permission.
How could this functionality be added to Ubuntu?

---

### Post by CharlesA on 2010-05-21
[http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists](http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists)

---

### Post by deere on 2010-05-21
> **CharlesA said:**
> [http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists](http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists)

I think first it would be important to have a list for normal unix file permissions.
Often you don't really need acl.
Later this could be extended to lists which also contain acl entries.

---

