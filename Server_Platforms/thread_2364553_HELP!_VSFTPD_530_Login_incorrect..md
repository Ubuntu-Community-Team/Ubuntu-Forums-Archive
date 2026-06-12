---
title: "HELP! VSFTPD 530 Login incorrect."
date: 2017-06-24
forum: Server Platforms
---

### Post by gloriawan on 2017-06-24
I've read a lot of post today but cannot solve my problem. Any expert can help?

I've installed vsftpd want to make user directory to /opt/lampp/htdocs/folder

Response:	220 Welcome to Test FTP service.
Command:	USER myuser
Response:	331 Please specify the password.
Command:	PASS ******
Response:	530 Login incorrect.
Error:	Critical error
Error:	Could not connect to server

This is in my vsftpd.conf

```

chroot_local_user=NO
chroot_list_enable=YES

```

myuser is in /etc/vsftpd/chroot_list, myuser is not in the blocked list

Followed the instruction in different post I've this in the conf file pam_service_name=vsftpd

I'm not sure if this is correct, I don't have anything in this directory /etc/pam.d/ I created one with below and I'm not sure if this is right

```
# Standard behaviour for ftpd(8).
auth    required    pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed


# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.


# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required    pam_shells.so

```

[FONT=Verdana]Please help![/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by howefield on 2017-06-24
Thread moved to the "*Server Platforms*" forum.

---

### Post by gloriawan on 2017-06-25
I narrowed down is the permission. At least I manage to set anonymous to the right place.
The last step is to make my user to the same directory as the anonymous.

---

