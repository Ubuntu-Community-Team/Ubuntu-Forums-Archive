---
title: "Upload directory permissions"
date: 2011-04-28
forum: Server Platforms
---

### Post by leegold on 2011-04-28
Hi,

I have a LAMP stack on my laptop for learning, "localhost". I'm using Lighttpd instead of Apache. It's on Lubuntu 10.10.

When I try to upload some files via PHP code it didn't work. The target folder is /var/www/uploaded_vids

It was 755 and uploads didn't work. I changed it to 777 and now the uploads work. It's ls -l is now:

drwxrwxrwx 2 root root   4096 2011-04-27 20:50 uploaded_vids

maybe 775 would be enough? Nope, tried  775 for the dir and does *not* work. Does it make sense that 775 was not enough permissions? 

777 works. Is this normal? My browser or whatever component is uploading is not root? But the server itself is running as root(?). 

Could someone help me with uploads regarding permissions so I can better understand? What are the permissions normally for an upload directory on a server?

Thanks,

Lee G.

---

### Post by falko on 2011-04-28
Lighttpd is running and the user and group www-data. So the directory must be owned by that user and group.

Try this:
```
chown www-data:www-data /var/www/uploaded_vids
chmod 755 /var/www/uploaded_vids
```

---

