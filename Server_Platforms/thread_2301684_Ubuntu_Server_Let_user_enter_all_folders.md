---
title: "Ubuntu Server: Let user enter all folders"
date: 2015-11-04
forum: Server Platforms
---

### Post by Koen_Oosterhuis on 2015-11-04
Hello everyone!

I own a VPS running Ubuntu Server 14.01, and I run a game server for a friend on it, with him having FTP access to the server resources.
Because I have to program for his server, I need to access his files, so I have a sudo user, but how can I make that user bypass all permissions?
I want to be able to enter his folders with my user, but since he owns the folder and because the permissions for his files are something like 640, I cannot see his files, unles I sudo chmod them to 777. How can I fix this?

---

### Post by Lars Noodén on 2015-11-04
Welcome.  

One of the first things to do is to [turn off FTP and replace it with SFTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  Then change all the passwords.  FTP is unsafe.  

About the directory permissions, you can do that with a group.  If that directory is /var/www you could do it like this:

```

# do initial setup just once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add koen  webmasters

```

In that example, any user in the group 'webmasters' could write in the /var/www hierarchy.

---

