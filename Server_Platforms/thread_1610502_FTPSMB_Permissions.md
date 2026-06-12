---
title: "FTP/SMB Permissions"
date: 2010-10-31
forum: Server Platforms
---

### Post by docwisdom on 2010-10-31
I have read a few threads and they have solved a couple of my problems, but I am still running into some issues. Basically I am trying to set up permissions for my user account to have read/write permissions to /var/www for web development purposes.

1. I created a group called webdev
2. I added my user docwisdom account to webdev
3. I did chmod g+w -R /var/www

All folders/files are properly owned by root and have the group of webdev.

Uploading and downloading of files works just fine from ftp.

Now the problems:
1. When I create a new folder, I has d-------w- 2 docwisdom webdev but I have my ftp mask set to 0775. Shouldnt it be drwxrwxr-x 2 docwisdom webdev?
2. With smb, I am able to log in with my username IF the only directory I have set up in smb.conf is userhome. If I add /var/www to smb.conf as a directory it locks me out and I cant log in from my other computers (Im on macs for web development)

---

