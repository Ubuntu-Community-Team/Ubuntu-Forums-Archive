---
title: "VSFTP with pam_passwd file support"
date: 2008-08-04
forum: Server Platforms
---

### Post by BrandonLC on 2008-08-04
Hello

I've walked through several tutorials and sifted through these forums for hours, no luck yet.

All I want is VSFTP to authenticate users against a htpasswd file, and it won't. Maybe it is, but the password encryption between vsftp and htpasswd is different.

I added virtual users like this:

htpasswd -b /etc/vsftp/passwd brandon testpassword

which created an entry in /etc/vsftp/passwd as expected, but somehere there is a dissconnect between VSFTP and PAM.

Can anyone point me in the right direction?

vsftp.conf 
```

listen=YES
anonymous_enable=NO
local_enable=YES
virtual_use_local_privs=YES
write_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
guest_enable=YES
user_sub_token=$USER
local_root=/var/ftp_root/$USER
chroot_local_user=YES
hide_ids=YES
file_open_mode=0777
local_umask=0000
local_max_rate=100000
lock_upload_files=YES

```

/etc/pam.d/vsftp
```

# Standard behaviour for ftpd(8).
auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
#@include common-account
@include common-session

@include common-auth
auth	required pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required pam_permit.so

```

/var/log/auth.log
```

Aug  4 14:03:33 brandon-laptop pam_pwdfile[21323]: wrong password for user brandon
Aug  4 14:03:43 brandon-laptop vsftpd: pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=brandon rhost=127.0.0.1  user=brandon
Aug  4 14:04:56 brandon-laptop vsftpd: pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=brandon rhost=127.0.0.1  user=brandon


```

Thanks

---

### Post by YorYor on 2008-10-03
Had the same problem as you, and finally got it.
In /etc/pam.d/vsftpd, change
```
auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
@include common-auth
```
to
```
#auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
#@include common-auth
```

Resulting file should have only the following lines uncommented:
```
@include common-session
auth	required pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required pam_permit.so
```

---

