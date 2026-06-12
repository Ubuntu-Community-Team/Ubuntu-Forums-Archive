---
title: "External Access"
date: 2007-01-27
forum: Server Platforms
---

### Post by opticalfiber on 2007-01-27
hi guys, i'm not very expert and i want to ask if it's possible to make a condivision or a server (web,ftp,http....etc) in order to access my pc from outside to download or upload files on my pc? i think there are some tools, but i don't know which and how to configure them! please help :D ! thx a lot

---

### Post by encompass on 2007-01-27
There are many ways... I recommend if your the only one of the system... use ssh

very secure connection and you can even run your computer from anywhere on the net.
here is the command...
```
sudo apt-get install openssh-server
```
Then you use the IP of your computer to login with this...
ssh username@ipaddress
That should do it...
to do copying is another matter...
windows... use winscp
linux... "connect to server" in gnome, gftp, or text based scp or rsync
All depends what you want to do.
I recently set up mine so I can mount ssh connections as actual directories to use on my local computer as if they where right in front of me.  not need to copy!
PM me if you need more help.

---

