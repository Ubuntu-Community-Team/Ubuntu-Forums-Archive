---
title: "Finetuning of ACL using Samba"
date: 2010-10-01
forum: Server Platforms
---

### Post by the student on 2010-10-01
Hi there, 

I was so sure it must be easy to set up the file permissions like I want, but obviously it isn't :confused:. Here is what I want to have:

I have a samba fileserver (only Windows clients connecting) with a common share. Everybody is supposed to be able to put files on the share, but no one should be able to delete files which do not belong to oneself. 

I want several users to put files in a common directory, so they need write access to the directory, right? but all the same they should not be able to delete files from others. So they are not allowed to have write access to the directory, right?

It all works fine with modifying etc. but still I can delete files I am not supposed to do. I learned already that permission to delete is bound to the permissions of the containing folder and that sticky bits might help. But either they don't or I didn't get it right until now.

I'm a bit confused right now and not sure if it is actually possible to do what I wanted. Can somebody help?

Thanks in Advance...

---

### Post by SlugSlug on 2010-10-01
install acl & add ,acl   to /etc/fstab  after the bit it says defaults..

/home/shared    ext4    defaults,acl 

now you want to control via users and groups

user = rwx  group= rw

use group shared for eg..
sudo addgroup shared
sudo adduser [username] shared

we want chmod 750 /directory
chgrp shared /directory -R

ls -l will look like

drwxr-x---+  30 username shared  4096 2010-09-23 13:41 common


then inside that common directory the files are owed by he user and readable to the group..

now with the acl bit

we can add additional groups access for instance

setfacl -R -m g:accounts:rwx /common

will give all in the group accounts rwx access to the shared folder (providing you have added a group called accounts and added the users to that account,,}

---

