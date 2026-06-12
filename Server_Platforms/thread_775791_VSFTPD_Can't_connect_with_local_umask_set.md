---
title: "VSFTPD: Can't connect with local_umask set"
date: 2008-04-30
forum: Server Platforms
---

### Post by noahclark on 2008-04-30
Good Morning,

I have VSFTP up and running and everything works fine except permissions.  Whenever I try to set local_umask, I can't connect to the server and I get the following in filezilla.

```


Status:	Connecting to 192.168.0.4:2324...
Error:	Could not connect to server
Status:	Waiting to retry...
Status:	Connecting to 192.168.0.4:2324...
Error:	Could not connect to server
Status:	Connecting to 192.168.0.4:2324...
Error:	Could not connect to server
Status:	Waiting to retry...
Error:	Connection attempt interrupted by user

```

Here is my config file:

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


local_umask =0022

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

rsa_cert_file=/etc/vsftpd/certs/vsftpd.pem
#file_open_mode=0111
```

Once I comment out local_umask, it starts to work again.  I have file_open_mode commented out, but I tried using that to fix it too.

Any advice would be much appreciated.

Thank you.

---

