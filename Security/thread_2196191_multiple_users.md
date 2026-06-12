---
title: "multiple users"
date: 2013-12-28
forum: Security
---

### Post by pjmlmas on 2013-12-28
initial install of ubuntu created user tom:tom. User = tom, group = tom
say I have multiple users, on multiple partitions.
I have an ext4 share partition, sharepart.
If tom makes a directory on sharepart,  it is under tom:tom. So I should use groups,but...builtins or custom group. I see a group called users id = 100. Just make all users on all partitions part of this group? 

Also, the shared partition, the top level is root:root, should this be changed to say users:users or something.

---

### Post by oldfred on 2013-12-28
I do not have my system set up with multiple users, but I have saved some links in case I might later. If one of these users comes along they really understand groups and setting ownership.

 Share folder among two users of same PC.- posts by morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions - posts by BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[URL="http://ubuntuforums.org/showthread.php?t=1727396"]http://ubuntuforums.org/showthread.php?t=1727396

[/URL] Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)
Info on permissions for groups
[http://www.zzee.com/solutions/unix-permissions.shtml#setuid](http://www.zzee.com/solutions/unix-permissions.shtml#setuid)

[URL="http://ubuntuforums.org/showthread.php?t=1727396"]
[/URL]

---

### Post by bab1 on 2013-12-28
> **pjmlmas said:**
> initial install of ubuntu created user tom:tom. User = tom, group = tom
say I have multiple users, on multiple partitions.
I have an ext4 share partition, sharepart.
If tom makes a directory on sharepart,  it is under tom:tom. So I should use groups,but...builtins or custom group. I see a group called users id = 100. Just make all users on all partitions part of this group? 

Also, the shared partition, the top level is root:root, should this be changed to say users:users or something.

Users permissions are at the directory and file level.  If you have multiple mortal users (humans) and you want to share data then, yes, you should use a common group such as the group *users (gid=100)*.  But you could also make your own group. You are not limited to the default groups.  To see all the users (both mortal and system) try this from the CLI```
getent passwd
```...to see all the groups try this```
getent group
```

I have many shared branches of the file system that have ownership at root:users.  The fact that the top level is root:root does not tell the whole story.  By default the root:root directory has these permissions u=rwx,g=rwx,o=r-x (0775).  This means the directory is world (everyone) readable and can be descended into.  If the user can traverse the directory (decend) and the subdirectory has the user group ownership and the proper permissions all will work.

Here is a look at an implementation I have on this workstation```

 ls -ld /srv
drwxr-xr-x 3 root root 4096 Aug 31 16:51 /srv

ls -ld /srv/public
drwxrw**[COLOR="#FF0000"]s[/COLOR]**r-x 9 root users 4096 Dec  4 10:04 /srv/public

```...As you see I set the **sgid bit ** (see red above) to create group inheritance of the data.

All of this assumes you are using one instance of Ubuntu.  If you have multiple OS's and want to share a file system, you will need to make sure that at the very least the users group always has the same gid.  Ubuntu uses the gid rather than the group name as ID.

---

### Post by pjmlmas on 2013-12-28
> If you have multiple OS's and want to share a file system, you will need to make sure that at the very least the users group always has the same gid That is why I thought using builtin group "users" was probably best. That sgid bit is a nice new trick.  

I'll check out those other links as well.

---

### Post by bab1 on 2013-12-28
> **pjmlmas said:**
> That is why I thought using builtin group "users" was probably best. That sgid bit is a nice new trick.  

I'll check out those other links as well.

If you need help with the specific setup post back here.  Don't forget to check the ultimate umask settings.  The earlier Ubuntu versions had a default umask of 0022.  The later versions have a umask of 0002 which is what you want for group sharing.  In Ubuntu 13.10 there is a bug in Upstart for Gnome gvfs which sets the umask back to 0022.  But it is easily cured see [**here**]("http://ubuntuforums.org/showthread.php?t=2195326").

FYI -- using the sgid bit  has always been available in Linux.

[COLOR="#0000FF"]Edit:  Using the user group *users * will not guarantee that the gid will be consistent across multiple OS installs.  You need to check this on all installs first.  I have had the gid differences.  Ubuntu always picks the next available number at group creation time.  Yes the chances are slim that you will have a mismatch, but the re is a chance.  Check it whant you set everything up and then you can forget about it being a problem later.  [/COLOR]

---

### Post by pjmlmas on 2014-01-03
To all. I added me to users group as secondary. I chown to me:userson directory shared and set the  sgid. Works quite well...

---

