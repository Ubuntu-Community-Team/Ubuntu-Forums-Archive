---
title: "vsftpd (+apache2) permissions configuration"
date: 2010-10-13
forum: Server Platforms
---

### Post by windsxs on 2010-10-13
Hello. 
I'm hoping to get advice on how to configure vsftpd server, to enable users upluoad  files with right permisions. I create user like this:
```
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/<newUser>.domain.com
a2ensite <newUser>.domain.com
/etc/init.d/apache2 restart
useradd -d /var/www/<newUser>.domain.com -m <newUser>
passwd <newUser>
restart vsftpd
```And so, when <newUser> uploads file via ftp protocol (NetBeans (e.g. in filezilla you can manually set permissions)), the file is unreadable to server. File owner is <newUser>:<newUser>. 
Already I managed to find, that I need configure in /etc/vsftpd.conf theese lines:
```
file_open_mode=0777
anon_world_readable_only=NO
local_umask=0777
```I believe it's not enough and I etoted it wrong.
I did whoami command on my univercity server, and found that it showed me www-data. Is it group or what...

So, in summary, how to make ftp to create files with permisions e.g.  +rwxrwxr-x or smth more clever..

---

### Post by windsxs on 2010-10-13
i can't believe nobody knows... :/

---

### Post by Vegan on 2010-10-13
I have mind setup for user accounts, no account no access.

All users are uploading and downloading from their respective home folders. No problem.

Read the config file carefully, it has all the info you need.

---

### Post by windsxs on 2010-10-18
that was lame question :oops: I was surfing and surfing google, but nothing... Then once again i was changing stuff in /etc/vsftpd.conf, and uncommented ```
local_umask=022. 
```. This is what permissions is set to uploaded files.. 0 means it is in octal.

> Read the config file carefully, it has all the info you need. :KS

---

### Post by verysimple on 2010-10-27
022 is the umask not the permission. Both are related, but different. The system uses the umask to set permission on files.

e.g.

umask = 022

newfile will have permissions: 755 (i.e. 777 - 022)

---

