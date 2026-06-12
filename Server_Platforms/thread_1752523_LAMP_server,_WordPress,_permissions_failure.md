---
title: "LAMP server, WordPress, permissions failure"
date: 2011-05-07
forum: Server Platforms
---

### Post by Nocturna1 on 2011-05-07
Main purpose of this LAMP server is testing development.  I would like to get this server setup up almost exactly to a T how my real web hosting server is setup.
 
I am running 11.04 and have installed LAMP.
 
I also installed vsftpd.
 
I went ahead and made a symlink from /home/user/public_html to /var/www/.
 
I login from a Windows 7 computer via CuteFTP to my Ubuntu server.
 
I can enter the public_html directory and can create folders but the default permissions for any folder created is 700.
 
I have tried running chmod -R 755 /home/user/public_html but this does not work.  Every file or folder created now currently will take a 700 permission.
 
How do I make it so anything that is uploaded into this folder will be at either 755 or 775?
 
Also what is the best practice for utilizing the /var/www directory?  Should I be using a symlink to link it to my user's home folder?
 
I have read through so many posts with regards to adding users to a group and giving this group permission and this or that I'm so confused.  Thanks in advance.

---

### Post by CharlesA on 2011-05-08
You'd have to chmod the /var/www directory to 755 for it to be world readable.

You could look into setting the umask, but I believe that the default is already 755.

---

### Post by Nocturna1 on 2011-05-08
Ok it was actually an issue with vsftpd.  After going into the config file I had to uncomment a section which was something along the lines of local_umask=022.

---

