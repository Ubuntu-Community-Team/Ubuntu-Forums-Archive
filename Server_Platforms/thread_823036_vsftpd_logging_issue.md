---
title: "vsftpd logging issue"
date: 2008-06-08
forum: Server Platforms
---

### Post by jombeewoof on 2008-06-08
using Hardy server, no gui

vsftp is setup to lock all users to /var/ftp

when I set xferlog_enagle=yes

now the ftp service runs, but does not even let you try to login.


Do I have to "touch" the log file, or is it automatically created?
If I have to create it, where?

---

### Post by windependence on 2008-06-09
> **jombeewoof said:**
> 

when I set xferlog_**enagle**=yes



I'm sure it's a typo but if you just copied and pasted there is one problem. Should be "enable"


What error are you getting when trying to log on? How are you logging in to the server?

-Tim

---

### Post by jombeewoof on 2008-06-09
yeah, that's just a typo. I double checked the file just in case and it's right


No error, when connecting with gftp in linux and coreftp in windows it just doesn't connect.
This is all I get from gftp

```

Looking up 192.168.2.103
Trying 192.168.2.103:21
Cannot connect to 192.168.2.103: Connection refused
```

This is my entire vsftpd.conf
```
dirmessage_enable=YES
anonymous_enable=NO
anon_world_readable_only=YES
syslog_enable=YES
connect_from_port_20=YES
pam_service_name=vsftpd
listen=YES
ssl_enable=NO
anon_mkdir_write_enable=NO
anon_upload_enable=NO
chroot_local_user=YES
ftpd_banner=Welcome message
idle_session_timeout=900
local_enable=YES
local_root=/var/ftp
log_ftp_protocol=NO
max_clients=10
max_per_ip=5
pasv_enable=YES
pasv_max_port=40500
pasv_min_port=40000
write_enable=YES
user_config_dir=/etc/vsftp_user_dir/
xferlog_enable=YES
download_enable=YES
```

if I comment out xferlog_enable, it works fine

---

### Post by jombeewoof on 2008-07-04
bump

---

### Post by windependence on 2008-07-04
Is this also a typo?

```
connect_from_port_20=YES
```

Should be port 21 I think.

-Tim

---

