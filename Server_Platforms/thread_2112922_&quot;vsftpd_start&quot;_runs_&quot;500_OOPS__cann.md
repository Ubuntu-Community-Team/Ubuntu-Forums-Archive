---
title: "&quot;vsftpd start&quot; runs &quot;500 OOPS : cannot read config file: start&quot;"
date: 2013-02-06
forum: Server Platforms
---

### Post by tarikaltuncu on 2013-02-06
Hi!

Although I am not an advanced user in Ubuntu, i keep googleing to create an ftp server on my server pc that runs Ubuntu 10.4 32 Bit for Servers as OS.

I kept following this post : [http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/) 

and completed its steps. But at the end of the process, i could not log into any account that i have created by htpasswd command.

and when i run vsftpd start command i get 500 OOPS : cannot read config file: start error whilst when i try to go on the server's ip on any browser it asks user name and password.However it does not accept.

Here how my vsftpd.conf file is ;

> listen=YES
anonymous_enable=NO
local_enable=YES
virtual_use_local_privs=YES
write_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
guest_enable=YES
user_sub_token=$USER
local_root=/var/www/sites/$USER
chroot_local_user=YES
hide_ids=YES

---

