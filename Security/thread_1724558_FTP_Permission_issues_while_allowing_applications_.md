---
title: "FTP Permission issues while allowing applications read/write access."
date: 2011-04-08
forum: Security
---

### Post by iarp on 2011-04-08
I have my websites hosted through 1and1 Linux hosting and the way it works is like this. Anything I upload via FTP is and always will be writable by my user AND the user that handles web application writing such as www-data. I do not have ssh access to those servers, and they will not divulge any information to me about how it is setup.

I'm unable to replicate anything like this on any Linux platform. vsftpd is the ftp server I've found that'll run almost how i want it, login as my own user and have access to my home folder which has a folder inside called "www" which contains all my public files.

Anything uploaded via FTP is always iarp/iarp permissions, files set to 0644 and folders 0755. But that stops www-data from having write access to the contents. So i chgrp the folders to www-data and 775 which allows access, but i figure that's a security issue, anyone with www-data access would now do whatever they wished, correct?

Anything written via web application is always www-data/www-data and i'm unable to write to it.

I am at a loss. If i added users to the www-data group that basically opens anything owned by www-data to everyone but then also requires 0775 permissions. I'm unable to figure out how to make it so i am able to access and edit files while allowing web applications access to required files when needed, it's a constant permissions battle really.

---

