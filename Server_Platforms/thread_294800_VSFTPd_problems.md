---
title: "VSFTPd problems"
date: 2006-11-07
forum: Server Platforms
---

### Post by Fonskar on 2006-11-07
Hi,


I'm using edgy and vsftpd and i have 2 questions about it.
  1)I want it to use passive mode so i configured it as shown below:
```

anonymous_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO
anon_world_readable_only=NO
ascii_download_enable=yes
chroot_local_user=YES
dual_log_enable=YES
guest_enable=YES
listen=YES
local_enable=YES
pasv_enable=YES
setproctitle_enable=YES
use_localtime=YES
userlist_deny=NO
userlist_enable=YES
write_enable=NO

accept_timeout=30
anon_max_rate=70000
connect_timeout=30
data_connection_timeout=60
idle_session_timeout=30
local_max_rate=70000
listen_port=20000
max_clients=5
max_per_ip=4
pasv_min_port=50001
pasv_max_port=50101

ftpd_banner=
guest_username=virtual
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
userlist_file=/etc/vsftpd.user_list

```


ports 21 and 50001-50101 are open in firestarter and in my nat gateway.
Everything works fine on standard port but i i want to change the listen_port -20000 for example- to something else i have this message( of course i opened this port as well)
```
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
500 Illegal PORT command.
ftp: bind: Address already in use
```
I read some things dealing with ip_conntrack like ```
$sudo modprobe ip_conntrack_ftp ports=21,20000

``` but it still doesn't work.





2) I'd like to be able to monitor the users connecting and the progress of their downloads. I set set_proctitle=YES and a ```
ps aux | grep vsftpd
``` but i can only see who is connecting but i neither can see their DL/UL rates or the progress within a file.

Is it possible? when i do this i can sometimes get informations about it but i don't know when. I mean i'd like to get infos before the DL/UL ends. It works sometimes but it seems to be random...
```
$tail /var/log/vsftpd.log
$Mon Nov  6 22:43:19 2006 [pid 13382] [zorglub] OK DOWNLOAD: Client "82.24x.xxx.xxx", "/Jazz.zip", 12915100 bytes, 62.93Kbyte/sec

```




3) About modifing VSFTPD.CONF. I tried yesterday to modify the local_max_rate while somebody was DL and then a ```
$sudo /etc/ini.d/vsftpd reload
``` it doesn't change anything. In fact i have to kill the process and restart the server and of course client gets disconnected.


Well if you know something about it that would be greaat!! :cool:

---

