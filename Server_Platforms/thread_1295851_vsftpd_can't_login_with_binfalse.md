---
title: "vsftpd can't login with /bin/false"
date: 2009-10-20
forum: Server Platforms
---

### Post by LepeKaname on 2009-10-20
Hello, I'm setting a FTP server with vsftpd. 
I created a group "ftp-users" and a user "ftptest". 

/etc/passwd:

ftptest:x:1001:1001::/var/www/testsite/:/bin/false

I recieve: 
530 Login incorrect.
Login failed.

But if I change it to:
ftptest:x:1001:1001::/var/www/testsite/:/bin/bash
I can login without a problem

I don't want to enable ssh login for the user, only ftp.
I did some tests in my local computer and here it works
without a problem with /bin/false and I'm using the same
settings.

These is my /etc/vsftpd.conf:

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=NO
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
chmod_enable=NO
hide_ids=YES
check_shell=NO
```

Any guess?

Thank you

I forgot to say that I set this permissions to /var/www/testsite:

drwxrwxr-x 19 root   ftp-users  testsite

and to files:

-rw-rw----  1 ftptest ftp-users index.html

---

### Post by LepeKaname on 2009-10-20
I solved the problem.

I found this thread:
[http://ubuntuforums.org/showthread.php?t=596484](http://ubuntuforums.org/showthread.php?t=596484)

and I added "/bin/false" to /etc/shell. 

For some reason I already had that value in my local computer. I wonder if its added by default in Jaunty?

---

### Post by Lars Noodén on 2009-10-20
> **LepeKaname said:**
> 

I don't want to enable ssh login for the user, only ftp.


FTP allows the username and password to get sniffed.  
FTPS, as you see, is a lot of hoops to hop through to tunnel FTP over SSL, and still leaves you with FTP on the system.

If you want secure file transfer via SFTP (different from FTPS), but not allow ssh, then you can use OpenSSH server to force groups of users


From /etc/ssh/sshd_config:

```

Subsystem sftp internal-sftp

Match Group sftp-only
   ChrootDirectory /home/%u
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

```

The for the user directories to be used, you must change the owner to someone other than the user who is loggin in, eg root, and it must not be writeable by the user, though individual files and subdirectories are allowed to be:

[INDENT][FONT="Courier New"]sudo chown root /home/ftptest
sudo chmod 750 /home/ftptest
sudo mkdir --mode 770 /home/ftptest/ftptest
[/FONT][/INDENT]

Filezilla works also with SFTP.


If you really want FTP tunneled over SSL, then vsftp is one way to go.

---

