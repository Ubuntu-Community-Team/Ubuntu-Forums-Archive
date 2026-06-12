---
title: "VSFTPD: error when attempting to secure connection"
date: 2011-02-05
forum: Server Platforms
---

### Post by andrewbrown22 on 2011-02-05
I'm trying to write a fairly simple vsFTPd configuration script in order to create a secure FTP connection from one machine running Ubuntu 8.04 with vsftpd installed and a machine running Windows XP Professional. [As a sidenote, I'm using this to transfer a backup file of fairly significant importance from one office to another and if SFTP isn't the best way to do so, by all means please mention a better solution!] 

The goals of this configuration are to be able to:
- mount a drive on the Windows machine using a local user's name and password on the Ubuntu box (the user is ftp-user-cbd, as you'll notice in the conf file below)
- have the Ubuntu machine's vsftpd script chown the files that are uploaded from the Windows machine to a user with more privileges so it can be removed from the /home/ftp folder location to the actual backup folder


However, at this point in my configuration I get the following error trying to connect to the ftp server using the vsftpd.conf file (in /etc) using filezilla on Ubuntu 10.04:

```
Status:	Connecting to 192.168.1.2:21...
Status:	Connection established, initializing TLS...
Error:	Connection timed out
Error:	Could not connect to server
```

and here's the current /etc/vfstpd.conf

```
# The KFM/CBD VSFTPD Configuration File
#
# No anonymous login
anonymous_enable=NO
# Let local users login
# If you connect from the internet with local users, you should enable TLS/SSL/FTPS
local_enable=YES

# Write permissions
write_enable=YES

# Allowing/Denying users
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

# change ownership upon upload
chown_uploads=YES
chown_username=kfm-admin


# this is the encryption part
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
listen_port=990

# certificate part
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

---

### Post by andrewbrown22 on 2011-02-07
Ok, I'm still having a large deal of trouble getting this configured. 

I've since read other articles about setting up SFTP using the openssh-server package.

What I'm trying to do is use SFTP (SSH) to encrypt traffic on a single directory for one user to be able to upload a file from a remote WinXP machine.

Does anyone have a suggestion of a tutorial to follow or care to help me out?

---

### Post by andrewbrown22 on 2011-02-07
I just tried to set it up with the following tutorial:
[http://ubuntuforums.org/showthread.php?t=858475](http://ubuntuforums.org/showthread.php?t=858475)

I followed the directions exactly, the only thing I didn't do was part 2a because I would like to be able to type in a user name and password to connect instead of key authentication if that is possible..

and I get the following error:

```
Status:	Connecting to 192.168.1.6...
Response:	fzSftp started
Command:	open "kfm@192.168.1.6" 22
Command:	Trust new Hostkey: Yes
Command:	Pass: *******
Error:	Connection reset by peer
Error:	Could not connect to server
Status:	Waiting to retry...
Status:	Connecting to 192.168.1.6...
Response:	fzSftp started
Command:	open "kfm@192.168.1.6" 22
Command:	Pass: *******
Error:	Connection reset by peer
Error:	Could not connect to server
```

---

### Post by andrewbrown22 on 2011-02-14
Well, I gave up on getting VSFTPD to do what I wanted as it was the wrong program for the job.

I was looking for a ssh wrapped FTP connection (SFTP). I was able to create a new user, only allow them the right to upload files via SFTP (using FileZilla client on *Nix and WinSCP for Windows automatic scripting of backups). I followed this guide to get the actual ssh/ftp set up:

[http://www.dkpw.co.uk/wp/?p=3428](http://www.dkpw.co.uk/wp/?p=3428)


Secondly I used this site in order to set up the Windows machine to automatically backup the files to the SFTP server:
[http://www.dualbotic.com/DasBlog/Configure+WinSCP+To+Upload+Automatically+To+SFTP.aspx](http://www.dualbotic.com/DasBlog/Configure+WinSCP+To+Upload+Automatically+To+SFTP.aspx)



I hope this provides more help than I was given.

---

