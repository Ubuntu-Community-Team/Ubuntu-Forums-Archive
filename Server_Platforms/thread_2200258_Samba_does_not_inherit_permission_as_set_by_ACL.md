---
title: "Samba does not inherit permission as set by ACL"
date: 2014-01-18
forum: Server Platforms
---

### Post by Tjalleman on 2014-01-18
Hi all,

I have spent two day trying to find a solution for my situation, but unfortunately found none. I read several threats on numerous sites about people with the same problem and tried all possible solutions, but no results so far.
 
[B]The situation:
[/B]-          Ubuntu file server with samba share
-          ACL for setting the permissions (I’m usin ACL because the permissions of new files and folders depend on the folder in which they are placed, so the more general umask isn’t sufficient)
-          Two windows clients
-          Two users in one group, let’s say User1,User2 and Group1 (which is for both users the primary group)
-          Now and then a guest user will access the server
-           
Let’s presume I got a folder Documents_User1. In Documents_user1 User1 has rwx access. User2 has r-x access and others don’t have access at all [---]. New files and folders in Documents_user1 obviously need to get the same permissions. So the ACL getfacl looks like this: 
 
[FONT=lucida console]root@Server:~# getfacl /data/documents_user1
getfacl: Removing leading '/' from absolute path names
# file: /data/documents_user1
# owner: user1
# group: group1
# flags: -s-
user::rwx
group::r-x
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:mask::rwx
default:other::---[/FONT]
 
Music is a more open folder: both user and group have rwx acces. Others (guests) have r-x access. New files and folders in Music need this same permissions. NB: because these permissions are different from the permissions of Documents_user1, I choose to use ACL.
 
[B]The problem:
[/B]When I make a new file or folder from a windows client using the windows-explorer, this file or folder does not get the permissions as set by ACL. Let’s say I created testfolder1 in windows via samba. When I run getfacl, I get this:
 
[FONT=lucida console]root@Server:~# getfacl /data/documents_user1/testfolder1
getfacl: Removing leading '/' from absolute path names
# file: data/documents_user1/testfolder1
# owner: user1
# group: group1
# flags: -s-
user::rwx
group::rwx
mask::rwx
other::--x
default:user::rwx
default:group::r-x
default:mask::rwx
default:other::---[/FONT]
 
Obviously the permissions are more permissive and now user2 can modify or delete this new folder. 
In Music new files and folder got the permissions presented below. In this case the permissions are less permissive then as set by ACL. So now the users cannot copy new music to the folder.
 
[FONT=lucida console]root@Server:~# getfacl /data/music/testfolder2
getfacl: Removing leading '/' from absolute path names
# file: data/music/testfolder2
# owner: root
# group: home
user::rwx
group::r-x
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:mask::rwx
default:other::r-x[/FONT]
 
[B]The question:
How can I fix this problem? I need new files and folder to inherit the permissions of the folder in which they are created/moved thus as set by ACL.
[/B] 
[B]Extra info:

[/B][U]1: My umask
[/U][FONT=lucida console]root@Server:~# umask
0022[/FONT]
 
[U]2: Relevant settings in samb.conf:
[/U]
[FONT=lucida console][Documents user1]
        comment = docs user1
        path = /data/documents_user1
        browsable = yes
        guest ok = no
        read only = no
        create mask = 777   # *
        inherit acls = yes
        inherit permissions = yes
 
[Music]
        comment = music
        path = /data/music
        browsable = yes
        guest ok = no
        read only = no
        inherit acls = yes
        inherit permissions = yes[/FONT]
 
* I tried several options here and even tried letting ‘create mask’ out  completely: no effect.
 
[U]3: When I login via ssh and create a folder, the permissions are as set by ACL.
[/U]
[FONT=lucida console]rutger@Server:~$ mkdir /data/documents_rutger/testfolder2
rutger@Server:~$ getfacl /data/documents_rutger/testfolder2
getfacl: Removing leading '/' from absolute path names
# file: data/documents_rutger/testfolder2
# owner: rutger
# group: documents
# flags: -s-
user::rwx
group::r-x
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:mask::rwx
default:other::---[/FONT]
 
Help is very much appreciated. Thanks in advance!

---

### Post by TheFu on 2014-01-18
If you want guests to access the [Music] share, then you cannot set "Guest Ok = no"

I would setup shares with read-only users to be separate from the read-write users. Manage the permissions at the share level.  If there are sensitive files under a directory that must be viewed by guests, then the directory structure is messed up and needs to be changed. If not really, then virtually.

And I've never needed to use ACLs for anything, except on web servers to protect static files from cracker attacks. These days, I use read-only NFS mounts from different servers for read-only files on a website. More secure and a hacker with root on the web server still can't change that, not that this helps you in any way.

---

### Post by Tjalleman on 2014-01-20
Thanks for your answer TheFu. The work-around you provided didn't fit my needs. But thanks anyway.

I spend many more hours on this problem and I have found the solution: mounting the drive with xattr and reffer to xattr in the smb.conf. This is how it works:

0: At this point I had installed Sambashare, and ACL and mounted the drive with ACL (as I explained in my post above)

1: Mounted my drive with xattr by inclusing 'user_xattr' in [COLOR=#333333][FONT=monospace]/etc/fstab[/FONT][/COLOR]
 e.g.: UUID=ea7d59a1-bc75-4403-874c-75e677a18f85 /data ext4 defaults,acl,user_xattr

2: Edited my smb.conf and ended up with this:

[Documents_user1]
        comment = docs user1
        path = /data/documents_user1
        browsable = yes
        guest ok = no
        read only = no
        vfs objects = acl_xattr
        nt acl support = yes
        inherit acls = yes
        inherit owner = yes
        inherit permissions = yes
        map acl inherit = yes

Now all the new files and folder inherit the permissions as set by ACL.

---

