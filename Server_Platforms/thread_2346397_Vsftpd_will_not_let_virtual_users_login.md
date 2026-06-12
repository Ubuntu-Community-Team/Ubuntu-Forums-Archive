---
title: "Vsftpd will not let virtual users login"
date: 2016-12-14
forum: Server Platforms
---

### Post by taylors11 on 2016-12-14
Here is my vsftpd.conf file



listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
userlist_enable=YES
user_sub_token=$USEER
local_root=/var/www/$USER
chroot_local_user=YES
#
#Virtual 
nopriv_user=vsftpd
virtual_use_local_privs=YES
guest_enable=YES
hide_ids=YES
guest_username=vsftp
pam_service_name=vsftp
#
#Certs
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH

Also here is my Pam.d file
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/user


account required /lib/security/pam_userdb.so db=/etc/vsftpd/user

I have no issues with logging in as a local user, but I want this to work basically for only virtual users. 

Any help would be great, thanks!!!

---

### Post by cariboo on 2016-12-15
Moved to Server platforms, you may get help quicker here.

---

### Post by Graham_Willis on 2016-12-15
Isn't it that you just have writable [COLOR=#000000]/var/www/$USER directories? If this is the case, google for allow_writable_chroot. I'm not saying that I recommend to turn this option on, but the relevant documents should point you in the right direction.[/COLOR]

---

### Post by taylors11 on 2016-12-21
I got this fixed thanks, i used db4-utils to create a data base, i had that wrong in my pam.d file. That was blocking my virtual users from logging in, once i got that part added to the pam.d file it worked fine.

---

