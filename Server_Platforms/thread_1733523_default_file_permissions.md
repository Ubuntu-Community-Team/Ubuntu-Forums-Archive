---
title: "default file permissions"
date: 2011-04-19
forum: Server Platforms
---

### Post by herdthat on 2011-04-19
i have a web server running ubuntu 10.04, with nginx installed as the server. i installed vsftpd as my ftp server, when i upload files to the server their default permissions are not setup correctly so when you try to visit a .html or .php or .jpg page/item you get an access denied/403 Denied.

how/where can i change it so that files uploaded have the proper file permissions by default and i don't have to go though and manually. This article shows how an individual was able to manually set the permissions:

[http://www.ruby-forum.com/topic/172018](http://www.ruby-forum.com/topic/172018)

---

### Post by Herazio on 2011-04-19
I believe it's possible to use umask to set default permissions for files and directories. I'd suggest checking the man page to this. 

If you want everyone to have access to a certain directory such as public_html you could normally (if I'm not mistaken) use the command

umask 044 -Rf public_html (this would give full access to root and read/execute access to group and others).

Hope it may help

Herazio

---

### Post by herdthat on 2011-04-19
Thanks for the response.

I went in and checked the umask setting in my /etc/profile/ and ~/bashrc and made sure it was set to 022, which is read and execute. Also, I'm using vsftpd and I looked at it's conf file and made sure the settings in there were set for 022. 

I rebooted my server, tried to upload the file and still no dice. The permissions that were created with nginx, the default in /var/www/nginx-default/ is -rw-r--r-- but the permissions in my directory uploaded via FTP to /var/www/mydomain.com/public_html/ is -rw-------

I uploaded a test file to /var/www/nginx-default/ and it also has the permission -rw------- so it's definitely not a folder permission issue, but an FTP issue.

I'm just confused. Big time.

---

### Post by egpetrich on 2011-04-20
When you connect to the FTP server, you should be able to change the umask for uploaded files with the "umask" command (try "umask 0007" to allow read/write/execute for user and group).

The "vsftpd.conf" configuration file has an option "local_umask" that looks like it controls the default starting umask value. (Google "vsftpd man" to learn more.)

---

### Post by fenderr357 on 2011-04-20
Try playing around with the "file_open_mode" setting in vsftpd.conf (this is what permissions are assigned to uploaded files).

You might have to use something like 775 to allow the web server to access. Or, you could chown the document root to administrator:www-data (may be a different group than www-data, I know this works for Apache) - then a setting like 750 would work. 


Either way, you should be able to set it with file_open_mode.


..Also, if you have local_umask set (mentioned above), that value is  applied on top of file_open_mode; That means a file_open_mode=755 with  local_umask=022 means uploaded files have 777 permissions.

---

### Post by egpetrich on 2011-04-21
> **fenderr357 said:**
> ..Also, if you have local_umask set (mentioned above), that value is  applied on top of file_open_mode; That means a file_open_mode=755 with  local_umask=022 means uploaded files have 777 permissions.

I must disagree. The file-creation mask value (aka umask) can only subtract permissions. It isn't supposed to add permissions. An example in Bash:

```
umask 0
touch file_with_umask_000
umask 0027
touch file_with_umask_027
ls -l file_with_umask_*
```

The file "file_with_umask_000" should show "rw-rw-rw-", which is the default for files created under most circumstances. The file "file_with_umask_027" should show "rw-r-----". The octal "2" masks out the group write permission, and the octal "7" masks out all permissions for "other".

Bash doesn't allow you to specify the file creation mode, so I can't easily test the example you give. Based on what I have seen, however, setting local_umask to 022 should turn off write permission for "group" and "other".

---

