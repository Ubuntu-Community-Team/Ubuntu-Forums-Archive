---
title: "vsftpd virtual guests"
date: 2012-03-15
forum: Server Platforms
---

### Post by adidas56 on 2012-03-15
I cannot figure this out. I am trying to get virtual users set up on vsftpd, but for some reason they won't work. I just keep getting login errors. Can someone see what I am doing wrong?

Here is my vsftpd.conf
```
listen=YES
pasv_min_port=30000
pasv_min_port=30999
anonymous_enable=NO
local_enable=YES
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
guest_enable=YES
guest_username=virtual
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

I have added a user for virtual and it is pointing at /home/ftpsite which is owned by virtual and the virtual group and the permissions are 744.

The logins file that was used for the virtual users looks like this
```

guest
password
test
abc123

```

Then I am using the following command to create the db file

sudo db4.6_load -T -t hash -f logins.txt /etc/vsftpd_login.db

The pam file I have looks like this.

```

auth required /lib/security/pam_userdb.so db=/etc/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd_login

```
and I tried placing that in /etc/pam.d as ftp, vsftpd, and as both with no luck. When I do try to log in as a virtual user I get 530 Login incorrect. Login failed. However, if I try to login in with an actual system user then I can connect with no problems.  What gives? What am I missing?

Also, here is what a log entry looks for a failed attempt

```

Wed Mar 14 23:08:57 2012 [pid 2] CONNECT: Client "192.168.1.104"
Wed Mar 14 23:08:57 2012 [pid 1] [test] FAIL LOGIN: Client "192.168.1.104"

```

---

### Post by adidas56 on 2012-03-16
I realized my mistake. First of all, the basic example configs for vsftpd don't show you how to allow both virtual users and local users. That said, you need to change the PAM config to do this. However, I realized that I need to get just virtual users working alone which I have yet to do. I will do that tomorrow and report back.

---

### Post by adidas56 on 2012-03-22
Well here is part of the solution. Apparently, I don't have a

/lib/security/pam_userdb.so

instead it's at

/lib/i386-linux-gnu/security/pam_userdb.so

Once I changed my vsftpd config in the pam directory and restarted  vsftpd, and voilà I could access it via virtual user. Anyway, the rest seems to be fixing up my config to do what I want it to do.

I think this post will help me with the rest [http://www.linuxquestions.org/questions/linux-software-2/how-to-enable-both-virtual-and-local-vsftpd-logins-with-pam-365860/]("http://www.linuxquestions.org/questions/linux-software-2/how-to-enable-both-virtual-and-local-vsftpd-logins-with-pam-365860/")

---

### Post by adidas56 on 2012-03-30
Got it. I am a little uneasy with some of this but maybe someone could point out any potential issues.

Here is what my config looks like now.

```
listen=YES
pasv_min_port=30000
pasv_min_port=30999
anonymous_enable=NO
local_enable=YES
write_enable=NO
#anon_upload_enable=NO
#anon_mkdir_write_enable=NO
#anon_other_write_enable=NO
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
guest_enable=YES
guest_username=virtual
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
```

Here is an example of a local user's additional config

```
write_enable=YES
guest_username=adidas56
virtual_use_local_privs=YES
```

Here is an example of the read only virtual guest

```

guest_username=adidas56

```

Here is my PAM

```
# Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

#for virtual users
auth sufficient /lib/i386-linux-gnu/security/pam_userdb.so db=/etc/vsftpd_login
account sufficient /lib/i386-linux-gnu/security/pam_userdb.so db=/etc/vsftpd_login

#for local users
# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required pam_shells.so
```

Hope this helps someone else.

---

