---
title: "Pam + MySql + VSFTPD"
date: 2010-11-06
forum: Server Platforms
---

### Post by cfw34683 on 2010-11-06
I have been working on this for 3 days now to no light. I think i have everything right but i just can't login to the ftp. i can connect just fine.but every password is bad/wrong

this is what i have.

```
2010-11-06 22:20:51	home	vsftpd	pam_unix(vsftpd:auth): check pass; user unknown
2010-11-06 22:20:51	home	vsftpd	pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=tester rhost=127.0.0.1 
2010-11-06 22:20:51	home	vsftpd	pam_winbind(vsftpd:auth): getting password (0x00000388)
2010-11-06 22:20:51	home	vsftpd	pam_winbind(vsftpd:auth): pam_get_item returned a password

```

this is what i have in /etc/pam.d/vsftpd

```
# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-auth
@include common-session
auth	required	pam_shells.so
auth	required	/lib/security/pam_mysql.so user=web passwd=xxxxxxxx host=127.0.0.1 db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=2
account required	/lib/security/pam_mysql.so user=web passwd=xxxxxxxx host=127.0.0.1 db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=2
```

"XXXXX = current db pass for that user"

here is a pick of the database it says that its talking to.
[IMG]http://i55.tinypic.com/16ko17r.jpg[/IMG]

here is my vsftpd.conf file
```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
#use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=Welcome to Whitlow.Zapto.Org FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
#secure_chroot_dir=/var/www
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

as far as i can see there is nothing wrong. can anyone please help me figure this out. i can not connect with local (wich i dont want to) or mysql table entry's. please help

---

### Post by cfw34683 on 2010-11-07
does anyone have any ideas. or has everyone just given up on pam,mysql,vsftpd combo like it seems on the net. every where i look there is some half-cocked tut or no info at all.

---

### Post by chmac on 2011-02-08
Have you had any luck with this? I'm looking to do something almost identical soon, so you've done all the hard work for me. :-)

I don't have anything useful to add at this point, I haven't started looking into it yet. But when I do, I'll post back here if I find anything helpful.

PS> I just found this [link]("http://www.linux.com/archive/feature/125789") which claims to document the process. Don't know if it's helpful, but thought I'd post it anyway.

---

