---
title: "Need help with Samba"
date: 2011-05-14
forum: Server Platforms
---

### Post by ftornell on 2011-05-14
Hi,
Have read a few guides but want to verify the configuration with you guys.

I would like to accomplish:
1. Users to have access to their own Share on the server, no one exept the user shall be able to browse, read/write. (sould the user directories be in /home/<username> folder or shall one use another structure?

2. There shall be a public are where all users can browse, read and write. no guests, only users who have accounts!

3. A GroupShare. Users who are members of group Staff many browse, read/write.

4. Add some directorys for private use (to see how it works)

So would this be correct:

Create the Directory Structure on the server:
```

# mkdir /usr/smbroot
# mkdir /usr/smbroot/users
# mkdir /usr/smbroot/public
# mkdir /usr/smbroot/groups/staff
# mkdir /usr/smbroot/private/fredrik_extended

```

or shall one use the default user shares /usr/<username>/?
Whats best practice?

```

[homes]
comment = Home Directories
browseable = no
writeable = yes

[public]
comment = Public
path = /usr/smbroot/public
public = yes
writeable = yes
directory mask = 0770
create mask = 0770

[groups]
comment = Public
path = /usr/smbroot/groups/staff
public = no
writeable = yes
write list = @staff
directory mask = 0770
create mask = 0770

[fredrikextended]
comment = Fredriks Private Directory
path = /usr/smbroot/private/fredrik_extended
valid users = fredrik
public = no
writable = yes
printable = no


```

---

### Post by Morbius1 on 2011-05-14
* The [homes] section is the classic way of implementing item (1) on your list. 

* You public share will work but just to make sure everyone will be able to access the contents I would add one more line to it:
> [public]
comment = Public
path = /usr/smbroot/public
public = yes
writeable = yes
**[COLOR=Blue] force user = nobody[/COLOR]**
directory mask = 0770
create mask = 0770And you will have to change permissions on the target to allow a guest to write to the share:
```
sudo chmod 777 /usr/smbroot/public
```* The groups share can get a little complicated depending on what right's you want to give to the members of groups.

First though you need to change the group of the target folder:
```
 sudo chown :staff /usr/smbroot/groups/staff
```And then change permissions:
```
sudo chmod 770 /usr/smbroot/groups/staff
```The way you have it now all members of @staff will be able to add to and delete files from the share but only the owner of the file will be able to edit it. If @staff = mary and bill and mary adds a file it will save as:
owner = mary
group = mary
permissions = 664

bill will be able to remove mary's file but he won't be able to edit it. That may be just what you want it to do - not sure. You can make it such that only mary can remove mary's files and you can make it so bill can edit mary's files so it depends on what you want these users to be able to do.

---

