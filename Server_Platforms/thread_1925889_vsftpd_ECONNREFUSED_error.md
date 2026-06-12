---
title: "vsftpd ECONNREFUSED error"
date: 2012-02-15
forum: Server Platforms
---

### Post by Jstall on 2012-02-15
Hello all,

I have Ubuntu Server running and am trying to set up a vsftp server. I have run into difficulties. What I want to do is allow ftp login using unix user credentials. I have a user set up specifically for FTP login. 

I am following the setup guide here: [http://www.noob2geek.com/linux/setup-vsftpd-debian-ubuntu/](http://www.noob2geek.com/linux/setup-vsftpd-debian-ubuntu/)

I have followed all the steps but when I try to connect to the FTP server I get the message:
**Connection attempt failed with "ECONNREFUSED - Connection refused by server"**

I don't know what I could be doing wrong and the message is not very descriptive. Here is my vsftpd.conf file in it's entirety(with comments removed)
```

listen=YES
#listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=NO
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
#ftpd_banner=Welcome to blah FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
userlist_file=/etc/vsftpd.userlist
userlist_enable=YES
userlist_deny=NO 

```
The file /etc/vsftpd.userlist has one entry, which is the name of the ftp user's account. 

I know the FTP account credentials are correct as I can SSH in with them. If anyone could give me a suggestion as to what I am doing incorrectly or could even offer a way to debug this issue it would be very much appreciated. Thanks!
[]("http://www.noob2geek.com/linux/setup-vsftpd-debian-ubuntu/")

---

### Post by Lars Noodén on 2012-02-15
> **Jstall said:**
> ... What I want to do is allow ftp login using unix user credentials. ...

I know the FTP account credentials are correct as I can SSH in with them. If anyone could give me a suggestion as to what I am doing incorrectly or could even offer a way to debug this issue it would be very much appreciated. Thanks!
...

You do realize that allowing FTP login using Unix user credentials is to transmit the username, password and data unencrypted.  It makes the account trivially easy to crack by sniffing the connection.  

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

Since you have SSH running, you already have SFTP installed and configured.  I would recommend uninstalling the FTP server and using SFTP instead.  That way your credentials remain safe and the connection is strongly encrypted.  It's not only secure, but also less work.

You can still use Nautilus, Filezilla, and Dolphin for your SFTP connections.

---

### Post by Jstall on 2012-02-15
Thank you for your reply Lars Noodén. You make very good points. I am going to follow your advice and use SFTP. Thanks again!

---

