---
title: "Userdir no write acces by website"
date: 2009-12-17
forum: Server Platforms
---

### Post by sjaakmans on 2009-12-17
Hello,

I have setup a user_dir in apache2, on ubuntu server 9.10

My problem is that i can't write to this dir while i'm running a website in my browser. Although I can access my website. I can also write to this dir by FTP. 

Is there any solution for this problem?

Greetings,
Sjaakmans

---

### Post by lykwydchykyn on 2009-12-17
If you're accessing the website through a browser, the directory is being accessed by the web server, not by your browser directly.  That means it's being accessed by the user running the webserver (www-data, by default) and will have the privileges of that user.

Normally you want that read-only, but if for some reason it's necessary to enable write-access, you just need to make sure the www-data user has access to write to the files.

Simplest way is to make the files world-writable, but if you need more granular control there are other methods available.

---

### Post by sjaakmans on 2009-12-17
If i do: chown -R www-data:www-data ./public_html , does the user still has any write rights?

Or should i add the user to de the group www-data?

---

### Post by lykwydchykyn on 2009-12-17
> **sjaakmans said:**
> If i do: chown -R www-data:www-data ./public_html , does the user still has any write rights?

No, that would make the owner of the files www-data.  You want to keep the user as the owner of the files, just add permissions for www-data

> 
Or should i add the user to de the group www-data?

That won't accomplish anything, unless you also make sure the group has write permissions on the files and that the file group is set to www-data.  Actually, if you did those last two, you still wouldn't need to add the user to that group.

---

### Post by sjaakmans on 2009-12-17
Ok thanks, i will use the chmod option.

---

### Post by oneloveamaru on 2009-12-17
Just do a "chmod 775 directory" and then a "chgrp www-data directory" and your browser should have full access to the directory. Throw in a "-R" if all sub directories need the same permissions.

---

