---
title: "New File Permissions on 10.04.1 Server"
date: 2012-04-10
forum: Server Platforms
---

### Post by bmcgree1 on 2012-04-10
I'm driving myself crazy trying to figure this out. I hope someone can shed some light on my problem. 

I need to know the simplest way to set default file permissions on a folder I created:  /var/www/uploads

So when someone accesses the site they insert some information and then upload a file to the server, inside that uploads folder. Everything works, including the upload except permissions. 

The newly uploaded file has default permissions (-fw------) and cannot be read inside a web browser. Please! Someone, what is the easiest way to do this and how? I've just about broken my neck trying to figure out acl. Thanks.

---

### Post by FreeD01 on 2012-04-11
Have you tried to change permission on folder with -r option? Something like

**[FONT=Book Antiqua][SIZE=2][FONT=&quot]sudo chown -R www-data:www-data[/FONT] /var/www/uploads[/SIZE][/FONT]**

if you want web users to own folder and everything in it. Also chmod should do the thing.

---

### Post by bmcgree1 on 2012-04-11
I have tried that, but it doesn't set the permissions for new files. They still don't have permissions :(

---

