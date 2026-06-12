---
title: "Help with file permissions server 10.10"
date: 2011-03-16
forum: Server Platforms
---

### Post by FromTheUnderground on 2011-03-16
I am fairly new to Linux and trying to setup a file server for a small group of users and I am in need of help with file permissions with Ubuntu Server 10.10.

I have a single share mapping (ex /media/hdd1/share1). There are several folders that everyone will need read/write/edit permissions and there will be a few folders that all users will need read permissions and a couple of users will need read/write/edit permissions.  

I have tried several things and as long as I create the folders/files through ssh using sudo, the permissions are fine, but when the users create file and folders through their computers (mixture of Windows and Mac) that user becomes the owner and no one else can write or edit those files.

I am using SAMBA and though it was a config issue with that but I logged each user  directly into the server with the same issue.

I tried sudo chmod 777 /media/hdd1/share1 but all newly created files have the above issue.

Any and all help would be greatly appreciated.

---

### Post by SeijiSensei on 2011-03-16
I've found the easiest solution in these cases is to use the "force user" and "force group" directives in the share definition.  At the command line, type "man smb.conf" then search for these terms by typing "/force user" (without quotes, of course).

Basically "force user" makes all files created in the share be owned at the operating system level by a single Linux user.

---

