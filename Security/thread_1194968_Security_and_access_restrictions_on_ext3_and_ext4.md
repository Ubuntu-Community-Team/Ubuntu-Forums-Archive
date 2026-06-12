---
title: "Security and access restrictions on ext3 and ext4"
date: 2009-06-23
forum: Security
---

### Post by pagis on 2009-06-23
Hi,

I wanted to know if ext3 or ext4 has security options, similar to the NTFS ones. I want to have access control to specific users to specific files and directories and / or to encrypt files and directories in a similar manner to NTFS, so it is be transparent to the user with the suitable permissions, again, in a similar way to the way NTFS works on windows

Thanks :)

---

### Post by sisco311 on 2009-06-23
Linux/Unix file permissions:
[uhelp]community/FilePermissions[/uhelp]

acl provides a more flexible permission mechanism for file systems:
[http://www.vanemery.com/Linux/ACL/linux-acl.html#using]("http://www.vanemery.com/Linux/ACL/linux-acl.html#using")

encryption:
[uhelp]community/FolderEncryption[/uhelp]
[http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html]("http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html")

---

