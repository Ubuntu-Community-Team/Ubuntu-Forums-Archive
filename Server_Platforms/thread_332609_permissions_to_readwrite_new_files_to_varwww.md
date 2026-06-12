---
title: "permissions to read/write new files to /var/www/"
date: 2007-01-06
forum: Server Platforms
---

### Post by mikeintj on 2007-01-06
Hi,

I want my website to allow users to upload files and then view those files. But I'm a newbie to Linux and I'm having file permission problems. I can see how to change permissions for existing files, but whenever a new file is uploaded, my permissions for this new file are different.

I have messed around with my default settings because I thought that the only two groups that existed were root and mike, not realising that www-data owned the /var/www/ directory. So currently the directory is owned by user mike of group root. When I upload a new file the owner of the new file is www-data. I added mike to group www-data but that doesn't seem to affect anything.

I'm sure this is a basic problem (and maybe should be moved to the absolute beginners forum).

Thanks,

Mike

---

### Post by matthew on 2007-01-06
To allow anyone in the world access to that directory for reading and writing (and program execution if any exist) you need to do this from a command line (terminal).
```
sudo chmod 777 /var/www
```

Take a few minutes to read these pages...they will help you considerably. I recommend reading before you do the above.

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)
[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by mikeintj on 2007-01-06
thanks for that Matthew, but I think the specific problem relates to the default settings for the creation of new files that are uploaded. When I click on the ownership profile for a newly uploaded file it is -rw-------, when I want them to be -rw-rw-rw-.

Searching around I believe it is the umask setting that  needs adjusting, which I think is in /etc/profile. But setting it to 000 didn't work. I'll experiment again.

---

### Post by Koybe on 2007-01-07
It depends how files are uploaded. The /etc/profile umask will only work with logged in users.

---

