---
title: "vsftpd ignoring user_config_dir setting."
date: 2013-09-21
forum: Server Platforms
---

### Post by Benjamin_Solum on 2013-09-21
Hello All!

I'm brand new to Ubuntu server's and I'm getting my feet wet on Ubuntu 13.04 x 64bit.

I've been working on getting vsftpd installed and I've been able to successfully FTP in using a user I created: "MYUSERNAME".  When I FTP in, the default directory is /home/MYUSERNAME.  What I'd like it to be is: /var/www/MYUSERNAME.  That folder exists and my user has permissions to it.

My vsftpd.conf file is as below:
**=== /etc/vsftpd.conf ===**


listen=YES
local_enable=YES
write_enable=YES
local_umask=022
chroot_local_user=YES
user_config_dir=/etc/vsftpd/users
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
userlist_file=/etc/vsftpd.userlist
userlist_enable=YES
userlist_deny=NO
seccomp_sandbox=NO


And my user config file is:
**=== /etc/vsftpd/users/MYUSERNAME ===**


local_root=/var/www/MYUSERNAME
dirlist_enable=YES
download_enable=YES
write_enable=YES


vsftpd is completely ignoring my settings.  On top of all that, I can't seem to write when I FTP in as that user.  Any ideas?  I've scoured the net for several hours now and none of the "common" fixes (like tweaking user_config_dir and checking permissions) seem to work.

Thanks in advance!

---

### Post by peertje on 2013-09-25
Did you restart vsftpd after you changed your configuration file?

```
sudo service vsftpd restart
```

Also add 

```
tcp_wrappers=YES
```

to your vsftpd.conf

As an alternative you try making a simlink in your home directory? Maybe this works.

```
ln -s /home/MYUSERNAME/www /var/www/MYUSERNAME
```

What happens if you put local_root=/var/www/MYUSERNAME to the main vsftpd.conf?

---

### Post by Bucky Ball on 2013-09-25
*Thread moved to **Server Platforms**.*

Welcome. You might have more luck here. ;)

---

