---
title: "VSFTPD problems"
date: 2015-06-01
forum: Server Platforms
---

### Post by trash5 on 2015-06-01
I am a new Ubuntu-user (Ubuntu server with no GUI, couldn't find where to post so I post here) with a massive problem!

I have managed to get a Ubuntu Server up and running, I have managed to get Plex to work, I have managed to make Webmin to run, I have managed to get Samba to work, all I need now is to get SFTPD to work.
I have installed SFTPD, and I have managed to get a user that have access to the files I've mounted from my Samba-share and I have managed to log in to the ftp-server. But I still can't transfer any files larger than 1Mb (smaller files works fine).

I use FileZilla to transfer files and the response looks like this:


```
Status:	Directory listing of "/Music/And One - 1998 - 9.9.99 9 Uhr" successful
Status:	Retrieving directory listing of "/Music/And One - 1998 - 9.9.99 9 Uhr/CD"...
Status:	Directory listing of "/Music/And One - 1998 - 9.9.99 9 Uhr/CD" successful
Status:	Resolving address of XXXX.asuscomm.com
Status:	Connecting to 81.16.167.94:21...
Status:	Connection established, waiting for welcome message...
Status:	Connected
Status:	Starting download of /Music/And One - 1998 - 9.9.99 9 Uhr/CD/And One - 9.9.99 9 Uhr.mp3.cue
Status:	File transfer successful, transferred 1 328 bytes in 1 second
Status:	Starting download of /Music/And One - 1998 - 9.9.99 9 Uhr/CD/03. Evil Boys.mp3
Command:	PASV
Response:	227 Entering Passive Mode (XXX,XXX,XXX,XXX,84,235).
Command:	RETR 03. Evil Boys.mp3
Response:	150 Opening BINARY mode data connection for 03. Evil Boys.mp3 (6810976 bytes).
Error:	Connection timed out after 20 seconds of inactivity
Error:	File transfer failed
Status:	Resolving address of XXXX.asuscomm.com
Status:	Connecting to 81.16.167.94:21...
Status:	Connection established, waiting for welcome message...
Status:	Connected
Status:	Starting download of /Music/And One - 1998 - 9.9.99 9 Uhr/CD/03. Evil Boys.mp3

```

As you a timeout occurs when trying to transfer the larger file. My vsftpd.conf looks like this:

```
listen=YES
local_enable=YES
write_enable=NO
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
allow_writeable_chroot=YES

And I have tried with this uncommented;
#pasv_enable=Yes
#pasv_max_port=12000
#pasv_min_port=12500

```












In my router I have forwarded port 12000-12500, port 20 and port 21 (all on TCP) to the server, I have also forwarded port 32400 for Plex (and that works without any hickups).

What have I done wrong, what else do you need to know?

I have googled, I have tried every single How to on the subject but no one seems to have this problem. I'm not very good at networking or Linux but with almost everything in place I wish I didnt have to write myself my own ftp-server in order to get this to work.

---

### Post by TheFu on 2015-06-01
If you install **openssh-server**, you get sftp automatically. No need for VSFTPD at all.
sftp defaults to port 22, the ssh port.

---

### Post by trash5 on 2015-06-02
But how do I chroot my users and stop them from ssh into my server using openssh?

I've managed to connect through port 22 using sftp but I have yet to find any clear tutorials on how to stop users from browsing the entire system and stopping them from using ssh, ftp is a more suitable solution for my needs and "everyone" claims it is simple to setup when it clearly isnt.

---

### Post by TheFu on 2015-06-02
> **trash5 said:**
> But how do I chroot my users and stop them from ssh into my server using openssh?

I've managed to connect through port 22 using sftp but I have yet to find any clear tutorials on how to stop users from browsing the entire system and stopping them from using ssh, ftp is a more suitable solution for my needs and "everyone" claims it is simple to setup when it clearly isnt.

A few options. Most good server-admin book have steps too.
[https://askubuntu.com/questions/134425/how-can-i-chroot-sftp-only-ssh-users-into-their-homes](https://askubuntu.com/questions/134425/how-can-i-chroot-sftp-only-ssh-users-into-their-homes)
[http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657)

There is always the sshd_config manpage:
> ChrootDirectory
             Specifies the pathname of a directory to chroot(2) to after authentication.  All components of the pathname must
             be root-owned directories that are not writable by any other user or group.  After the chroot, sshd(8) changes
             the working directory to the user's home directory.

             The pathname may contain the following tokens that are expanded at runtime once the connecting user has been
             authenticated: %% is replaced by a literal '%', %h is replaced by the home directory of the user being authenti&#8208;
             cated, and %u is replaced by the username of that user.

             The ChrootDirectory must contain the necessary files and directories to support the user's session.  For an
             interactive session this requires at least a shell, typically sh(1), and basic /dev nodes such as null(4),
             zero(4), stdin(4), stdout(4), stderr(4), arandom(4) and tty(4) devices.  For file transfer sessions using
             “sftp”, no additional configuration of the environment is necessary if the in-process sftp server is used,
             though sessions which use logging do require /dev/log inside the chroot directory (see sftp-server(8) for
             details).

             The default is not to chroot(2).


> Specifying a command of
             “internal-sftp” will force the use of an in-process sftp server that requires no support files when used with
             ChrootDirectory.

> Subsystem
 ...
Alternately the name “internal-sftp” implements an in-process “sftp” server.  This may simplify configurations
             using ChrootDirectory to force a different filesystem root on clients.
...

[https://www.debian-administration.org/article/94/How_to_restrict_users_to_SFTP_only_instead_of_SSH](https://www.debian-administration.org/article/94/How_to_restrict_users_to_SFTP_only_instead_of_SSH)

FTP should have been killed off in 1993.  sftp uses 1 port which makes it firewall friendly. Plain FTP wasn't designed in a world with security considerations. ;(
Everything is easier AFTER you've done it once.

---

### Post by trash5 on 2015-06-02
Finally! Got it working (using sftp).

It is not very simple, people should stop saying that since people saying that are experienced users. I could argue that programming my own ftp-server is simple since I am an experienced programmer but that doesn't make it simple for other people.

So to the tricks needed to setup something (in my case) useful:

create a usergroup, in my case ftpusers, 
create a common homefolder
make root own the folder
create a user with that folder as home
assign password to the user

```

sudo groupadd ftpusers
sudo mkdir /home/ftp
sudo chown root:root /home/ftp/
sudo adduser --home /home/ftp --shell /usr/sbin/nologin --no-create-home ftpuser
sudo passwd ftpuser

```

edit the sshd_config
```
sudo nano /etc/ssh/sshd_config
```

Add the following to the default file:
```

Subsystem sftp internal-sftp


Match Group ftpusers
#   ChrootDirectory %h <- should work, couldnt get it to work
   ChrootDirectory /home/ftp
   ForceCommand internal-sftp

   AllowTcpForwarding no
   PermitTunnel no
   X11Forwarding no

```

Restart ssh
```
sudo service ssh restart
```

Connect using FileZilla, protocol = SFTP, User = ftpuser, do not forget to open up a port on your router if needed

Simple like understanding a woman or open the last can of beer after the first 19 cans!

---

