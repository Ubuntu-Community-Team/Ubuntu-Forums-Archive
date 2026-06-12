---
title: "Samba Question"
date: 2010-12-02
forum: Server Platforms
---

### Post by MindController on 2010-12-02
Hi All
I made a samba sever for my work. Now I have a little bit problem regarding read write access. Here is detail. I have 24 clients and they have their own folders. Among them 4 of my clients have public files. So I made one public folder and i keep their files in the public folder. I want to give the fully permission to those 4 client for the public folder and other people are read and execute permission only. Please check the below code in the smb.conf. 

```

[global]

workgroup =myworkgroup
security = Yes
wins support = Yes

[Public]

path = /data/public
guest = ok
force users = admin client1 client2 client3
force group = users
read only = no

```

---

### Post by SeijiSensei on 2010-12-02
You need to use the "valid users" directive to list the usernames that can access the share.  The "force user" directive enables a single username to own all the files in the share.  "force group" does the same for groups.

You probably want something like 

```

path = /data/public
;guest = ok
valid users = admin client1 client2 client
force user =  admin
force group = admin
read only = no
create mode = 0664
directory mode = 0775

```

The admin user will own all the files, and group permissions will be granted to members of the admin group.  Admin and the three client users can access the share.  I don't think you want "guest = ok"; that will permit everyone to use the share;  I've commented that out above.  If you do want public access, you don't need the "valid users" directive.

---

