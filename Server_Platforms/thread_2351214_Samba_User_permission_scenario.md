---
title: "Samba User permission scenario"
date: 2017-02-01
forum: Server Platforms
---

### Post by cz.steve on 2017-02-01
Hi,

I m trying to setup custom User permissions for a certain user on my samba server. What i try to achieve is to login with mentioned user, lets say its name is user1, and only access two folders folder1, and folder2(with rwx permissions). The share contains plenty of other folders,which he should NOT see them. 
All my samba users are part of a group, lets say its called staff.

My global config is this :

```
[global][noparse]
log file = /var/log/samba/log.%m
load printers = no
socket options = TCP_NODELAY
full_audit[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/tongue.gif[/IMG]refix = %u|%T|%m|%S
full_audit:facility = local5
interfaces = 192.168.0.20/255.255.255.0
passdb backend = tdbsam
allow hosts = 127. 192.168.0. 192.168.3. 
unix extensions = no
cups options = raw
vfs objects = full_audit
full_audit:success = connect disconnect mkdir rmdir write sendfile rename unlink chmod fchmod chown fchown
full_audit[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/tongue.gif[/IMG]riority = notice
workgroup = MYSERVER
full_audit:failure = connect
use sendfile = yes
security = user
max log size = 50 [/noparse]
```

The shared directory config :

```
[share]
writeable = yes
path = /home/share
vfs object = full_audit
comment = Linux
valid users = user1,user2,user3
create mode = 0660
directory mode = 0770
```

With this configuration user1 can login and see all the files and folders. (which is not my purpose) 

If i erase user1 from the staff group, and set the mentioned folder1, folder2 with the permissions of 777, the user wont have permission to access the server. I just tested it.

So my question is how can i provide for the user accessibility to the share, but restriction to those folders only?

the mentioned shares permissions are:

```
drwxrwxr-- 28 root staff 4.0K Jan 30 16:22 share
```

Even with the read only for other permission, user1 should be able to login, and read the content of share, but he can t.

---

### Post by cz.steve on 2017-02-01
Looks like for a directory is not enough the only Read permission, i need to add the execute permission to list the content of a directory

---

### Post by TheFu on 2017-02-01
I have always split up CIFS shares by the group access (valid groups) needed. Different groups get different CIFS share access by 
* none
* read-only
* read-write

I use groups, not individual users to specify which users gain access. This doesn't mean what you are trying isn't possible, just that I've not done it that way.  I find that local Unix permissions mean nothing with common samba setups.  There is lots of documentation on the samba website about this stuff. [https://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](https://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html) might be helpful. See the different share-names for the same storage?

Also, if I have storage needed for just the single user, then I use the [Homes] setting. Each userid has access to a specific rw area just for themselves.

---

