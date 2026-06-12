---
title: "Samba and filesystem permissions"
date: 2014-04-13
forum: Server Platforms
---

### Post by geohei on 2014-04-13
Hi.

Was spending quite some time on Google ... without any results.

Samba 3 server installation.

daddy, jack and jim are 3 users. All 3 accounts have been created on the Ubuntu 12.04 LTS server. They have also been created within Samba database (smbpassword -a).

This is the config. of jack:
```
[Data Jack]
comment = Jack's data storage place
path = /media/raid-main/Data_Jack
create mode = 0644
directory mode = 0755
valid users = daddy,jack,jim
write list = daddy,jack
```
This allows all 3 users to read the share, but only daddy and jack are allowed to write the share.

The initial data was copied by root, so all files and directories have root:root as user:group, 755 (directory) and 644 (file) as permissions.

Now, when jack creates a file, I'd like daddy to be able to delete this file, and vice versa. When jack creates a file, it shows "jack:jack 644". This will allow daddy to read, but not write (delete) the file.

How should I modify the setup so that daddy is able to delete jack's file?

I thought of 775/664 permissions and to manually add daddy to group jack?

Is there any better and/or more elegant way to achieve this task?

Thanks,

---

### Post by volkswagner on 2014-04-13
I think you can create a new group 'dadjack'.  Add dad and jack to that group.  You can set the writelist to the new group.  Then add the force group option.  This along with your directory mode and create mode should work well.

```
[Data Jack]
comment = Jack's data storage place
path = /media/raid-main/Data_Jack
create mode = 0664
directory mode = 0755
force group = dadjack
valid users = @dadjack,jim
write list = @dadjack
```

I believe even if jim creates a file, it will be writable via dadjack group.  Depending how you want directories
deleted, you can likely use 0775 for directory mode.

---

