---
title: "apt-cacher import fails ; cannot write to foo/apt-cacher/packages"
date: 2011-05-23
forum: Server Platforms
---

### Post by fermulator on 2011-05-23
Context:
 * Was previously running apt-cacher on Ubuntu Server 8.04
 * Upgraded to Ubuntu Server 10.04 LTS (note that I didn't upgrade per say, but rather formatted, and installed a fresh installation of the server OS)
 * Restored apt-cacher files to /media/arrays/md250/apt-cacher
 * Installed apt-cacher as per [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

The installation seems to have gone as expected, (I can access apt-cacher report through apache).

Problem:
 * When I try to "import" the previous package store, it complains:
```
fermulator@fermmy-server:/media/arrays/md250/apt-cacher$ sudo /usr/share/apt-cacher/apt-cacher-import.pl
No import directory specified as the first argument, using /media/arrays/md250/apt-cacher/import
Cannot write to /media/arrays/md250/apt-cacher/packages - permission denied?

```

All of the permissions are correct, and I can touch/delete/mkdir/rmdir the "packages" directory without issue.

```
www-data@fermmy-server:/media/arrays/md250/apt-cacher$ ls -al
total 1668
drwxrwxr-x+ 6 www-data www-data   4096 2011-05-23 00:07 .
drwxr-xr-x+ 9 root     root       4096 2011-05-22 23:53 ..
drwxrwxr-x+ 2 www-data www-data 532480 2011-04-18 01:37 headers
drwxrwxr-x+ 2 www-data www-data 503808 2011-05-23 00:03 import
drwxrwxr-x+ 2 www-data www-data 610304 2011-04-18 01:41 private
drwxrwxr-x+ 2 www-data www-data  28672 2011-04-18 01:41 temp
www-data@fermmy-server:/media/arrays/md250/apt-cacher$ getfacl .
# file: .
# owner: www-data
# group: www-data
user::rwx
group::rwx
group:www-data:rwx
group:admin:rwx
mask::rwx
other::rwx
default:user::rwx
default:group::rwx
default:group:www-data:rwx
default:group:admin:rwx
default:mask::rwx
default:other::rwx

www-data@fermmy-server:/media/arrays/md250/apt-cacher$ mkdir packages
www-data@fermmy-server:/media/arrays/md250/apt-cacher$ touch packages/test
www-data@fermmy-server:/media/arrays/md250/apt-cacher$ rm packages/test
www-data@fermmy-server:/media/arrays/md250/apt-cacher$ rmdir packages/

```

---

