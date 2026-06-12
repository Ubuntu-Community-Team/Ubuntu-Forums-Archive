---
title: "permissions and ownership"
date: 2010-02-04
forum: Server Platforms
---

### Post by shiggydiggy on 2010-02-04
I'm trying to do some php/mysql dev in ubuntu and i can't seem to get this permissions and ownership deal right. apache runs as www, but if i copy files to /var/www with nautilus then their owner is <user>. I got around the problem by running midnight commander as root and then setting everything to 777. but that's really stupid. is there any way to change ownership of files and directories easily or to just do stuff as www? i tried su www in the root terminal but it said "Unknown id: www"

---

### Post by shiggydiggy on 2010-02-04
or is there a way to run apache as my user?

---

### Post by BobVila on 2010-02-05
> **shiggydiggy said:**
> I'm trying to do some php/mysql dev in ubuntu and i can't seem to get this permissions and ownership deal right. apache runs as www, but if i copy files to /var/www with nautilus then their owner is <user>. I got around the problem by running midnight commander as root and then setting everything to 777. but that's really stupid. is there any way to change ownership of files and directories easily or to just do stuff as www? i tried su www in the root terminal but it said "Unknown id: www"

I think the username is www-data, isn't it?

You could just sudo chown www-data:www-data [filenamehere] if you're not moving a ton of files. 

what's the ownership of /var/www look like? Did you edit it inadvertently?

---

### Post by Meelad on 2010-02-05
If I'm getting exactly what you wanna do, then try to change the ownership of the www directory and all of its subdirectories through:

```
sudo chown -R username /var/www
```and that should make username the owner of www, and should give him all rights for folder management.

---

