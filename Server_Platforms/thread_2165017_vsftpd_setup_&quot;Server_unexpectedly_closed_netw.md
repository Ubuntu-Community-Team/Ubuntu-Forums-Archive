---
title: "vsftpd setup &quot;Server unexpectedly closed network connection&quot;"
date: 2013-08-02
forum: Server Platforms
---

### Post by PaulWhipp on 2013-08-02
My goal is to run a small secure ftp service for virtual users on an Ubuntu 12.04 EC2 server. 

I've followed the [guide]("https://help.ubuntu.com/community/vsftpd") and exposed the necessary ports.

When I started the service I didn't get an error message and nothing appeared in the error log or in the syslog but the service failed to start:
```

~/vsfptd $ sudo service vsftpd start
vsftpd start/running, process 16103
~/vsfptd $ sudo netstat -lpn | grep -E ":21|:990|:20"
~/vsfptd $ 

```

I knew something was probably up with the configuration but what?

Here is what I did:
Invoking vsftpd directly on the configuration file allowed ne to see the error:
In my case:
```

~/vsfptd $ sudo vsftpd /etc/vsftpd.conf
500 OOPS: SSL: cannot load RSA private key

```

Even though this key is in use for https on the server it seems vsftpd does not like it (I checked the permissions so that the ftp user could access the file). I've temporarily reset vsftpd.conf to use the snakeoil certificates so vsftpd starts.

However, now when I use Filezilla to attempt access it just reports "Server unexpectedly closed network connection" Nothing turns up in /var/log/vsftpd.log but there is an entry in the syslog:
```
Aug  3 00:37:17 ip-10-39-71-182 kernel: [12182291.524325] type=1326 audit(1375490237.363:17): auid=4294967295 uid=65534 gid=65534 ses=4294967295 pid=16529 comm="vsftpd" sig=31 syscall=96 compat=0 ip=0x7ffff45d3c9e code=0x0
```

I don't know what that means and I'm not sure how I can continue to move forwards.

Can anyone help?

My vsftpd.conf contents are:
```

~/vsfptd $ cat vsftpd.conf | grep -v "^#\|^[[:space:]]*$" | sort
allow_anon_ssl=NO
anonymous_enable=NO
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
chroot_local_user=YES
connect_from_port_20=YES
debug_ssl=YES
dirmessage_enable=YES
force_local_data_ssl=YES
force_local_logins_ssl=YES
ftpd_banner=Welcome to the Evanidus secure FTP service
guest_enable=YES
hide_ids=YES
listen_port=990
listen=YES
local_enable=YES
local_root=/home/ftp/$USER
max_clients=10
pam_service_name=vsftpd.virtual
pasv_max_port=12100
pasv_min_port=12000
rsa_cert_file=/etc/apache2/ssl/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/apache2/ssl/ssl-cert-snakeoil.key
secure_chroot_dir=/var/run/vsftpd/empty
ssl_enable=YES
ssl_sslv2=YES
ssl_sslv3=YES
ssl_tlsv1=YES
use_localtime=YES
user_sub_token=$USER
virtual_use_local_privs=YES
write_enable=YES
xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log

```

---

