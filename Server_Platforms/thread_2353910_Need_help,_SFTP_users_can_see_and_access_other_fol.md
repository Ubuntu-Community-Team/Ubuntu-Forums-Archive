---
title: "Need help, SFTP users can see and access other folder in Home"
date: 2017-02-26
forum: Server Platforms
---

### Post by rlischer on 2017-02-26
I set up a sftponly group.  I modified sshd_config and added to the bottom:

```

Subsystem sftp internal-sftp

Match Group sftponly
ChrootDirectory /srv/sftproot/home
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp

```

I have users now trapped in their home folder when they sftp in and their websites work fine under /srv/sftproot/home/username1website.com/public_html

```

drwxr-xr-x 4 root       root     4096 Feb 26 06:34 .
drwxr-xr-x 3 root       root     4096 Feb 26 06:24 ..
drwxr-xr-x 4 username1 sftponly 4096 Feb 25 07:42 username1website.com
drwxr-xr-x 3 username2 sftponly 4096 Feb 25 06:06 username2website.com
 
```

My problem is the users can go in and out of each others website folder and see files in Filezilla using sftp.  When I try different permissions, it breaks Apache's ability to view their site.

Any ideas how I can stop access to other users folders and not kill Apache?

Thanks!

---

### Post by TheFu on 2017-02-26
The other would be to remove any access for "other" from the top level directories [S]and probably make the group be www-data (for apache)[/S]. Standard Unix permissions matter.

Or

Use ACLs.

---

### Post by rlischer on 2017-02-26
Thanks Fu, I'll probably try to avoid ACLs and try fixing permissions.

---

### Post by rlischer on 2017-02-26
I removed access for "other" and added each user to www-data, but still no luck.  Apache says 403 Forbidden, don't I need "other"?  I though other was the the rest of the world?  The world would need read access to the public_html right?

---

### Post by TheFu on 2017-02-26
> **rlischer said:**
> I removed access for "other" and added each user to www-data, but still no luck.  Apache says 403 Forbidden, don't I need "other"?  I though other was the the rest of the world?  The world would need read access to the public_html right?

No.  "Other" means anyone not in the group or the owner of the file ON THE SYSTEM.  It has nothing to do with people coming in through apache.  All website users access as "www-data" in a default apache configurations. They don't have accounts on the machine and if they do, those aren't being used.  The access is for what apache has only.

"World" is a bad term for the 3rd set of permissions. It oversimplifies and leads to incorrect settings.  There is no "world" in Unix. It is "other".

To get this working, you'll need an intermediate level of knowledge over Unix permissions. That is beyond what most Unix permission tutorials cover, but not hard at all.  There is an elegance there.

For example, the group sftponly doesn't need to be set on any of the directories.  That group is only used by the sftp-server to determine if someone should or shouldn't be allowed to sftp in. In their HOME directories, it probably shouldn't be used.

Also, Be very careful allowing www-data write access to directories.  They only need read, not write.  Allowing that group to write would let anyone in the group (all the other webmasters) write access. Probably not what you intend.  Also, you probably don't want all the sftpusers to be members of the www-data group either from a security perspective.

Does this make sense?

I found that the best way to learn about file and directory permissions is to create 3 groups and 4 userids, then mix and match them into different groups and then create a test directory under /tmp/ somewhere.  Try every possible mix of permissions, groups, and access modes.  Figure out how to allow everyone except members of a specific group to access the files.  Probably takes about 45 min doing this for things to start *clicking*.  Plus there will be some surprises - like chmod 711 on a directory. That's an interesting set of permissions which can be very helpful to upload directories ... for example.

Anyway, there are lots of different ways to address this with permissions.  I would start by looking at the permissions on a trusted, shared, hosting, website.  How do they do it?  
[https://superuser.com/questions/380119/permissions-on-a-typical-shared-linux-web-host](https://superuser.com/questions/380119/permissions-on-a-typical-shared-linux-web-host) goes into a few different options.  I like the last one there - they run a different apache instance for each different customer. That instance runs as the customer's userid.
[https://www.webhostingtalk.com/showthread.php?t=1325786](https://www.webhostingtalk.com/showthread.php?t=1325786) says to use fcgi and run stuff as the customer userid too.

---

### Post by rlischer on 2017-02-26
Thanks!  I just started learning about users and groups as well as permissions yesterday, so this really helps me out.  I learn best by doing, so I am going to take your advice on creating users and groups and messing around.

Thanks again!

---

### Post by TheFu on 2017-02-26
If you really want to learn this stuff, LPI has free training materials for Linux administration.  I teach a class weekends using their books.  [https://wiki.lpi.org/wiki/Free_Training_Materials](https://wiki.lpi.org/wiki/Free_Training_Materials) has links.
There is also the *Linux Command Line* book [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - free, no-hassle, PDF download. That book uses "world" - which is incorrect - but if you know UGO (user, group, other), then it should be fine.  I prefer "Owner" to user, but the chmod command has to use 'u' to differentiate from 'other.' ;)

---

### Post by rlischer on 2017-02-26
Thanks!

---

### Post by TheFu on 2017-02-26
I asked a buddy of mine who works at a hosting provider today how they do it.  He said that their method sucked and had lots of flaws, but the company wasn't going to change it now.  In short:

They only allow sftp access.
Every customer's account drops into a separate chroot - their HOME directory.  
Website files go into ~/public_html/.
They are all in the same group, but because they are stuck inside a chroot, they cannot see each other's files.
.htaccess is the only controls they have.

Then he pointed out how to get around those protections (it was VERY trivial for anyone with web scripting knowledge) to see all the other files on the server.

Anyway, hope this is of some help.

---

### Post by rlischer on 2017-02-26
Thanks.  I did what you said and made several users and groups and played around and now things make sense. 
I was then able to fix it and lock down the folders and still have working websites. When they SFTP in the are stuck in their home folder only.

The key was having each user own his own folder and his same group own the folder.  Then remove the www-data group I had added to each. The www-data group was allowing each user to browse the others folder. 

The tree looks like this:
&#9492;&#9472;&#9472; sftproot
         &#9492;&#9472;&#9472; home
             &#9500;&#9472;&#9472; user1
             &#9474;   &#9492;&#9472;&#9472; public_html
             &#9474;        &#9492;&#9472;&#9472; index.html
             &#9492;&#9472;&#9472; user2
                    &#9492;&#9472;&#9472; public_html
                        &#9492;&#9472;&#9472; index.html

permissions that worked:
```

drwxr-xr-x 4 root       root       4096 Feb 26 08:22 .
drwxr-xr-x 3 root       root       4096 Feb 26 06:24 ..
drwxr-x--x 4 user1     user1    4096 Feb 25 07:42 user1
drwxr-x--x 3 user2     user2    4096 Feb 25 06:06 user2

```

Thanks again!  I started reading the book you sent.

---

