---
title: "ZFS pool imported, but I am not the owner?"
date: 2020-12-28
forum: Ubuntu/Debian BASED
---

### Post by robbrown99 on 2020-12-28
I imported a zpool into an 18.04 distro (Zorin OS 15.3). 

The zpool imported fine with no errors. However in nautilus there was a padlock sign over the root folder of the zpool, and I cannot create or delete any of its contents. When I clicked on permissions it states:

```
Owner: root
(Access: greyed out)
Group root
(Access: greyed out)
Others
(Access: greyed out)
You are not the owner, so you cannot change these permissions
```


How can I change the permissions of an imported zpool?

---

### Post by yancek on 2020-12-29
If you want to change permissions of a folder owned by root, you need to use the chmod or chown commands prefixed with sudo to get admin privileges.

---

### Post by robbrown99 on 2020-12-29
OK, I figured it out. 

1. I made a new user group called zfsusers, and added my username to that group
sudo groupadd zfsusers

sudo adduser rbrown zfsusers


2. I then recursively changed ownership of the folder (zpool root) to the zfsusers group
sudo chown -R zfsusers BigDiskZFS

Looks like all permissions issues are now resolved.

---

### Post by robbrown99 on 2020-12-29
Thanks yancek for the response to lead me there

---

### Post by robbrown99 on 2020-12-29
Well that didn't work either. I tried some applications like digikam and it didn't recognize any folder. So I changed the permissions to myself and that worked

 sudo chown -R rbrown BigDiskZFS

Perhaps there should be some modification to ZFS on Linux to allow the user permissions to be assigned to the current user when importing the zpool, or at least providing an option to change permissions when importing. Perhaps there is and I missed it, but it took me several hours to figure out how to get this done (barrier to entry).

---

