---
title: "vsftp config. problem cannot connect from Internet"
date: 2007-11-04
forum: Server Platforms
---

### Post by little_penguin on 2007-11-04
I'm trying to set up an FTP server with vsftp with local user login and keep hitting a wall. I'm confused about the various settings, I've tried loads of guides, but it still doesn't work. Can anyone help me out. 

I've set up an ftp-users group, and created a special directory called /home/ftp-files to which the user mark defaults when he logs in.

Logging in locally from the LAN is no problem. It doesn't work from the Internet though. The user is able to log in okay, but gets the following error message:

[....]
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
550 Permission denied.
ftp: bind: Address already in use
ftp>

Here is my vsftpd.conf file:

pasv_enable=YES
pasv_promiscuous=YES
port_enable=NO
listen=YES
hide_ids=YES
local_umask=022
anonymous_enable=NO
local_enable=YES
write_enable=NO
dirmessage_enable=NO
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to my FTP server. Please enter your username and password.
chroot_local_user=YES
chroot_list_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


BTW I have a Netgear RP614v4 wired router. I tried forwarding specific ports but probably did the wrong thing. Need an expert to help me out :o)

---

### Post by kentl on 2007-11-04
I had an vsftpd setup and got my install notes. But I don't have time to give them to you at the moment. Tomorrow if you can wait.

If your primary goal is just to setup an ftp-server you might be interested in pure-ftpd too? That's what I'm using at the moment. I have virtual accounts with quotas (so they can't fill up my disc). If you check out [this thread]("http://ubuntuforums.org/showthread.php?t=594335") you will see exactly how I set it up, and if you turn to [this thread]("http://ubuntuforums.org/showthread.php?t=595628") you will see my accompanying firewall configuration.

If you want my vsftpd notes and prefer vsftpd, I can give them to you in around 18 hours from now. ;)

---

### Post by little_penguin on 2007-11-05
@kentl - oh yes please, that'd be great :) Would love to get this puppy working...

---

### Post by little_penguin on 2007-11-06
I got it working at last, it was awkward I think mainly due to the SPI Firewall in the Netgear RP614v4 Websafe Router plus the software firewall "firestarter" which is a frontend to IPtables. I'm using passive mode FTP, I just tested it with a friend and he was able to connect okay, but I can't seem to get active FTP to work . I also found that I had no success with the command line ftp program that comes as standard, however Filezilla worked, it seems to be more advanced (probably due to more features?).

I mainly followed this guide [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup")

Here's my new vsftpd.conf, in case it helps anybody:

pasv_enable=YES
dirlist_enable=YES
pasv_min_port=1024
pasv_max_port=1029
port_enable=NO
listen=YES
connect_from_port_20=NO
ftp_data_port=5020
listen_port=5021
hide_ids=YES
anonymous_enable=NO
local_enable=YES
write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
ftpd_banner=Welcome to my FTP server. Please enter your username and password.
chroot_local_user=YES
chroot_list_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

Obviously the relevant ports also need to be forwarded for FTP in the router with the above ranges.

I will probably tweak this file with more security features, SSL and other stuff. But for now I'm just happy it works ;)

---

