---
title: "vsftpd stopped working"
date: 2008-11-19
forum: Server Platforms
---

### Post by Panos on 2008-11-19
Hello,

I had vsftpd running fine on my headless hardy server. However, some time ago it stopped working (I suspect because of an update or sth). Now I really need to have it work again, but I can't make it, no matter what I try. I have port forwarding enabled in my router, from an external port number to port 21 in my server. I can use ftp from inside my LAN and everything works fine, but nobody can connect from the Internet. Firefox can't establish connection, IE times out, Filezilla starts listing directories then hangs...

Anyway, here is my vsftpd.conf. I have also included the commented options:

```

listen=YES
#listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
# local_umask=022
anon_upload_enable=NO
anon_mkdir_write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=myuser
xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
idle_session_timeout=6000
data_connection_timeout=1200
#nopriv_user=ftp
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=Welcome to My FTP server.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
#secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
ssl_enable=NO
#rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/media/FTP
download_enable=YES

```

Any help would be much appreciated.

Thanks,

Panos

---

### Post by Philio on 2008-11-19
Are your given any errors when starting the service?
Are you able to connect locally on the box?

---

### Post by cdenley on 2008-11-19
You're able to connect from the LAN, but not the internet? Wouldn't that be a problem with your router? Or possibly your ISP? Do you have a business ISP, or a residential one which doesn't permit you to host servers?

---

### Post by Panos on 2008-11-19
> **Philio said:**
> Are your given any errors when starting the service?
Are you able to connect locally on the box?

Hi,

No, no errors when I start the service. Also,I watch the vsftp.log while somebody tries to connect, and there are no errors - the log reports there is a successful login but the client cannot connect. As I said in my previous message, I can connect through ftp from anywhere in my LAN (and locally from the server).

Thanks.

---

### Post by Panos on 2008-11-19
> **cdenley said:**
> You're able to connect from the LAN, but not the internet? Wouldn't that be a problem with your router? Or possibly your ISP? Do you have a business ISP, or a residential one which doesn't permit you to host servers?

I've been thinking about it too, but I haven't changed ISP. FTP was working fine some months ago and AFAIK they haven't changed anything security wise (that is, I can still use standard server ports for FTP, HTTP, SSH, etc).

---

