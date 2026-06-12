---
title: "Default permissions for newly created files"
date: 2011-11-04
forum: Server Platforms
---

### Post by mjc7373 on 2011-11-04
HELLO ALL

I am trying to set default file permissions for newly created files using acl. I have used the setfacl command as such:

setfacl -d -m g::rwx /path
setfacl -d -m u::rwx /path
setfacl -d -m o::--- /path

The expected result was when I create a file or directory in /path the default permissions would be full access for owner and group, no access for others, or -rwxrwx---. 

Instead, what I get is -rw-rw----. When I run the getfacl, I get:

# file: /path
# owner: me
# group: group
user::rwx
group::rwx
other::rwx
default:user::rwx
default:group::rwx
default:other::---

I'm baffled! Any help would be greatly appreciated. Thanks!

---

### Post by vasile002 on 2011-11-05
Is your partition mounted with the acl option?
Check this link:
[http://www.linuxquestions.org/questions/linux-desktop-74/applying-default-permissions-for-newly-created-files-within-a-specific-folder-605129/](http://www.linuxquestions.org/questions/linux-desktop-74/applying-default-permissions-for-newly-created-files-within-a-specific-folder-605129/)

---

### Post by mjc7373 on 2011-11-05
Yes I edited fstab to inlcude acl and remounted. Directories created in the share do get the proper permissions, but files do not.

---

