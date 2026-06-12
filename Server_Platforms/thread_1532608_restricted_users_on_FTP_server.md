---
title: "restricted users on FTP server"
date: 2010-07-16
forum: Server Platforms
---

### Post by Emascu on 2010-07-16
Hello.

I am working on setting up a web server on my Ubuntu 10.04. Everything goes nicely so far and now I'm trying to set up a FTP server so I can work from other computers and give other users access to certain projects. Now I've followed this guide to install ftp with user access. ****

[http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

Now the ftp server works and I can add users and when they connect they see the file I want them to see. The only problem is that users also see all higher maps and can browse through them. As example, I add a user so he can connect to a project at /var/www/project1. And when the user connects through a ftp client he sees project1, but the user can also browse through www, var and the root of my ubuntu. So the user can browse through all my files and I don't want that.

Does anyone know how to solve this? Any help would be greatly appreciated.

---

### Post by david.garceau on 2010-07-17
What i used for this was VSFTPD, follow the basic setups for it, and then what i did was to uncomment chroot_local_user=YES in the config file which makes it so they can only go in their root folder...Then once its all setup in order to add users do the following...

terminal->sudo su
->groupadd groupname
->useradd username
->passwd password
->chgrp -R groupname /thisiswhere/youput/thedirectory (make sure you create it first)
 ->usermod -G groupname username
->chmod -R g+rwx /thisiswhere/youput/thedirectory*
->usermod  -d /thisiswhere/youput/thedirectory username

---

