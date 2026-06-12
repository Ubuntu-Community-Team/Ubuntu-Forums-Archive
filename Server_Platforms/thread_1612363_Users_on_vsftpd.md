---
title: "Users on vsftpd"
date: 2010-11-03
forum: Server Platforms
---

### Post by Strega on 2010-11-03
Hello,

I recently installed vsftpd on my server. I noticed that users on the machine can login into vsftpd with their username and password on the machine and go to their root dir "/home/username".
Now, I want to give some people a vsftpd username and password so they can upload and download files and folders to their folder, but this folder has to be in the "/var/www/(username)" folder. I don't want them to be able to go to any other folder than their own folder like "/var", "/etc" or "/home" etc. Also I don't want them to be able to login on the machine as a user, through putty for example. They should only be allowed to acces their folder with vsftpd, nothing else.
How can this be done?

Regards,
Strega

---

### Post by HermanAB on 2010-11-03
[http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)

---

