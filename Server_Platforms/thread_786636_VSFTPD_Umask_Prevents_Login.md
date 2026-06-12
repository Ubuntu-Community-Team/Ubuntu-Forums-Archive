---
title: "VSFTPD Umask Prevents Login"
date: 2008-05-08
forum: Server Platforms
---

### Post by noahclark on 2008-05-08
Whenever I uncomment the umask setting I can no longer login to my VSFTP server.  Any ideas on why this is?  All users logging in are local users.

```
listen=YES
listen_port=2324
local_enable=YES
write_enable=YES
anonymous_enable=NO
chroot_local_user=YES
pasv_min_port=1400
pasv_max_port=1450
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES


#local_umask =022

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

rsa_cert_file=/etc/vsftpd/certs/vsftpd.pem
file_open_mode=0777

```

Thanks!

---

### Post by nix4me on 2008-05-08
remove the space before the =

---

### Post by noahclark on 2008-05-09
Thanks so much! That fixed it!

---

