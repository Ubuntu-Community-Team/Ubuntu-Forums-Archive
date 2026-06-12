---
title: "Permissions on files in specific directory and subdirectories"
date: 2008-10-05
forum: Security
---

### Post by mrlizard123 on 2008-10-05
Hi,

I've looked but haven't been able to find an answer to my problem, if I've missed it and anyone knows where it's been posted already would appreciate a nudge in the right direction.

I have a server on my home LAN which has a folder to which multiple users have access. I want files that are created in this directory (and subdirectories) to have group write permissions by default when any user creates them. Using chmod g+s any files created in the directory inherit the group.

I realise that umask can do this but that would not be specific to this directory.

Can someone give me a pointer in the right direction? Do I need to use something like acl? If so can someone help me with the appropriate syntax assuming for arguments sake the folder is */some-folder* and the group is *users*?

Thanks in advance!

---

### Post by cdenley on 2008-10-06
First edit /etc/fstab. Add ",acl" to the mount options for /. Reboot.

Assuming you want to give the admin group inherited write permissions to a directory named test:
```

sudo chgrp admin test
sudo chmod g+s test
sudo setfacl -d -m u::rwx,g::rx,o::rx,mask::rwx test
sudo setfacl -d -m g:admin:rwx test

```

---

### Post by mrlizard123 on 2008-10-06
Thanks for the quick reply, I'll test this out when I am back at my home, unfortunately won't be able to test it for a couple of days.

Regarding changing the fstab options, does this apply still for jfs partitions? Or is it only for ext3?

---

### Post by cdenley on 2008-10-06
> **mrlizard123 said:**
> Thanks for the quick reply, I'll test this out when I am back at my home, unfortunately won't be able to test it for a couple of days.

Regarding changing the fstab options, does this apply still for jfs partitions? Or is it only for ext3?

The "acl" option is for ext3. I don't see a similar option for jfs, so I'm not sure how you would enable ACL support.

---

### Post by bigbear2350 on 2008-10-06
I believe JFS has ACLS enabled by defualt and in fact i dont think they can be turned off.

---

