---
title: "ubunto filezilla ftp access"
date: 2016-04-02
forum: Server Platforms
---

### Post by banks11378 on 2016-04-02
HI, Just installedUbuntu Server 14.04,  i got the filezilla working i am able to see the directory

[ATTACH=CONFIG]268133[/ATTACH]

but when i go to edit anything or upload, download i get this error

[ATTACH=CONFIG]268134[/ATTACH]

i know this has to be a permission issue , so my question is how do i fix this

I am logged into filezilla using my ubuntu server root name and a key file

[ATTACH=CONFIG]268135[/ATTACH]

---

### Post by darkod on 2016-04-02
You accessed it by ftp or sftp? Because there is a difference. For ftp you need to set up ftp server on your server and sftp works over ssh by default without any ftp.

If you did use ftp, it seems the default folder is the whole / partition, which is not really recommended. Better to set ftp to open your user home folder, upload the files you want there, and then use ssh session and move them to another location if needed.

The same applies to sftp. By default it should open your home folder so you can upload files there.

As for the permissions issue, don't forget that the first user created during install has sudo rights to run system commands but is not the same as root user. This is probably it is not allowing you to upload where you want.

Better to upload to your home folder first and then use sudo and copy where you want.

---

### Post by banks11378 on 2016-04-02
yea its sftp, sorry

I manage to fix it using the command in putty
chown -R rootuser /var/www/html

---

### Post by ajgreeny on 2016-04-02
Please mark as SOLVED from the Thread Tools menu up top.

---

