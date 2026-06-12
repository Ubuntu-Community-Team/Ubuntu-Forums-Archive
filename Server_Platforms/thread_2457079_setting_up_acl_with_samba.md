---
title: "setting up acl with samba"
date: 2021-01-25
forum: Server Platforms
---

### Post by espressobeanmachine on 2021-01-25
I am new to ACL and I am trying to accomplish the following. My setup is an LXD container, it runs NGiNX on it using the user nginx and group nginx. I have the following two users

```
Jillsmb
Bobsmb
```

These two will need to have access to directory /var/www/data that would be shared across the networking via samba but so does nginx as it will too 

I was told that ACL would be a good option since I don't have to worry about making sure all users needing access. Currently nginx has chown over /var/www in total. I have ran the following commands:

```
setfacl -m u:Jillsmb:rwx /var/www/data
```

```
setfacl -m u:Bobsmb:rwx /var/www/data
```

My samba config:

```
[officeshare]
comment = Office Share
path = /var/www/data
valid users = Jillsmb, Bobsmb
read only = no
create mask = 0777
writeable = yes
browsable = yes

```



But I am still getting permission denied when accessing from Windows 10. Where am I messing up?

---

### Post by LHammonds on 2021-01-28
What are the permissions on /var and /var/www look like?

If /var/www does not have at least read permissions for said user (as in "other" group access), then it may be impossible for said user to reach the /var/www/data folder.

LHammonds

---

### Post by darkod on 2021-01-29
You also have other options.

Since years ago samba was the natural option when windows computers needed to access a linux server. But with Win10 if I am not mistaken, there is NFS-Client feature that you can activate/install.

This will allow you to export paths from the linux server in a more native way, without having samba in between, and connect to them from windows computers. You still need to consider permissions but this setup would be more native and easier to manage.

---

