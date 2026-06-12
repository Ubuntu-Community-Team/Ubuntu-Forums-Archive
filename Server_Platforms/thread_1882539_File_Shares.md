---
title: "File Shares"
date: 2011-11-17
forum: Server Platforms
---

### Post by Jay89 on 2011-11-17
Hi,
  I would like to create a bunch of directories for end users and I would like to know the best way to achieve this. All users are authenticated through a windows active directory. Does anyone have an Idea how to get this done? I probably could add seperate entries into the smb.conf file but is there an easier way? The permissions should be that the directory's owner (user) can have rwx access. Everyone else has nothing.

Thanks

The file server is version: Linux fileserver 2.6.24-16-generic

---

### Post by boast on 2011-11-17
> **Jay89 said:**
> Hi,
  I would like to create a bunch of directories for end users and I would like to know the best way to achieve this. All users are authenticated through a windows active directory. Does anyone have an Idea how to get this done? I probably could add seperate entries into the smb.conf file but is there an easier way? The permissions should be that the directory's owner (user) can have rwx access. Everyone else has nothing.

Thanks

The file server is version: Linux fileserver 2.6.24-16-generic

i can point you to wiki tutorials...

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

[https://wiki.archlinux.org/index.php/Arch_Server_and_Active_Directory](https://wiki.archlinux.org/index.php/Arch_Server_and_Active_Directory)

---

### Post by Jay89 on 2011-11-17
Thanks but I already have winbind up and running. I think this is a file permission issue. For example, I have a user1 folder that has a chmod of 700 so only the owner (user1) has rwx. Group and other have nothing.  But other people can still access it. Any suggestions? Oh and the version of linux is 8.04 Hardy Heron.

---

