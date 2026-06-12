---
title: "vsftpd - fxp to - vsftpd not working"
date: 2010-10-28
forum: Server Platforms
---

### Post by Digifreakske on 2010-10-28
Hi all,

I have 3 FTP servers running at home. My laptop and the 3 servers are on the same switch (so no firewall stuff ..).

1 of those servers (Fredje) is a Windows XP machine with Filezilla Server.
The other 2 (Shuttle and Stacker) are Ubuntu Server 10.04 machines with vsftpd (identical config's - see below).

I'm able to FXP between Fredje (the Windows machine) and one of those 2 Ubuntu machines (Shuttle or Stacker).
Except for this "error" in the FTP client log (Site to Site Transfer Failed! (Attempting alternative method) everything goes well and the file is transfered.

The problem is FXP'ing between the 2 Ubuntu servers (Stacker and Shuttle). The files fail to transfer.

I logged pretty much everything so you guys can take a look.

Login-log for Shuttle (Ubuntu Server 10.04 with vsftpd)
-------------------------------------------------------
[L] Connecting to 192.168.1.100 -> IP=192.168.1.100 PORT=21
[L] Connected to 192.168.1.100
[L] 220 Welcome to Fredje's Linux FTP Server.
[L] USER leech
[L] 331 Please specify the password.
[L] PASS (hidden)
[L] 230 Login successful.
[L] SYST
[L] 215 UNIX Type: L8
[L] FEAT
[L] 211-Features:
[L]  EPRT
[L]  EPSV
[L]  MDTM
[L]  PASV
[L]  REST STREAM
[L]  SIZE
[L]  TVFS
[L]  UTF8
[L] 211 End
[L] PWD
[L] 257 "/"
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,100,89,232).
[L] Opening data connection IP: 192.168.1.100 PORT: 23016
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 206 bytes in 0,03 seconds (6,3 KB/s)


Login-log for Fredje (Windows XP with Filezilla Server)
-------------------------------------------------------
[R] Connecting to fredje -> IP=192.168.1.101 PORT=21
[R] Connected to fredje
[R] 220 FileZilla Server version 0.9.36 beta written by Tim Kosse (Tim.Kosse@gmx.de) Please visit [http://sourceforge](http://sourceforge).
[R] USER Fredje
[R] 331 Password required for fredje
[R] PASS (hidden)
[R] 230 Logged on
[R] SYST
[R] 215 UNIX emulated by FileZilla
[R] FEAT
[R] 211-Features:
[R]  MDTM
[R]  REST STREAM
[R]  SIZE
[R]  MLST type*;size*;modify*;
[R]  MLSD
[R]  UTF8
[R]  CLNT
[R]  MFMT
[R] 211 End
[R] CLNT xxxxxxxxx
[R] 200 Don't care
[R] PWD
[R] 257 "/" is current directory.
[R] TYPE A
[R] 200 Type set to A
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,130)
[R] Opening data connection IP: 192.168.1.101 PORT: 1154
[R] LIST -al
[R] 150 Connection accepted
[R] 226 Transfer OK
[R] List Complete: 890 bytes in 0,06 seconds (14,0 KB/s)


Login-log for Stacker (Ubuntu Server 10.04 with vsftpd)
-------------------------------------------------------
[L] Connecting to 192.168.1.102 -> IP=192.168.1.102 PORT=21
[L] Connected to 192.168.1.102
[L] 220 Welcome to Fredje's Linux FTP Server.
[L] USER fredje
[L] 331 Please specify the password.
[L] PASS (hidden)
[L] 230 Login successful.
[L] SYST
[L] 215 UNIX Type: L8
[L] FEAT
[L] 211-Features:
[L]  EPRT
[L]  EPSV
[L]  MDTM
[L]  PASV
[L]  REST STREAM
[L]  SIZE
[L]  TVFS
[L]  UTF8
[L] 211 End
[L] CWD /
[L] 250 Directory successfully changed.
[L] PWD
[L] 257 "/"
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,223,67).
[L] Opening data connection IP: 192.168.1.102 PORT: 57155
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 1 KB in 0,05 seconds (21,9 KB/s)


==> So nothing wrong here right?

vsftpd.conf from Shuttle and Stacker
------------------------------------
root@fredjeshuttle:/home/leech# cat /etc/vsftpd.conf

pasv_enable=YES
port_enable=YES
#port_promiscuous=YES
listen=YES
#listen_ipv6=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
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
ftpd_banner=Welcome to Fredje's Linux FTP Server.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
hide_file={.*,lost+found, RECYCLER, System Volume Information}
pasv_promiscuous=YES
#pasv_min_port=3000


root@serverstacker:/home/fredje# cat /etc/vsftpd.conf

pasv_enable=YES
port_enable=YES
#port_promiscuous=YES
listen=YES
#listen_ipv6=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
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
ftpd_banner=Welcome to Fredje's Linux FTP Server.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
hide_file={.*,lost+found, RECYCLER, System Volume Information}
pasv_promiscuous=YES
#pasv_min_port=3000

Transfer-log between Fredje and Shuttle (Windows and Ubuntu)
------------------------------------------------------------

File from Shuttle to Fredje   (port_promiscuous=YES  ==> NOT COMMENTED)
----------------------------
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] TYPE I
[R] 200 Type set to I
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,100,183,98).
[R] PORT 192,168,1,100,183,98
[R] 200 Port command successful
[R] STOR xxxxxxxxxxxxxx.xxxxxx
[R] 150 Opening data channel for file transfer.
[L] RETR xxxxxxxxxxxxxxx.xxxxx
[L] 150 Opening BINARY mode data connection for xxxxxxxxxxxxxx.xxxxxxxxxx (xxxxxxx bytes).
[L] 226 Transfer complete.
[R] 226 Transfer OK
Transferred: xxxxxxxxxxxxxxx.xxxxxxxx xxxx MB in xxx seconds (xxxxxx KB/s)
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,100,163,254).
[L] Opening data connection IP: 192.168.1.100 PORT: 41982
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 91 bytes in 0,03 seconds (2,9 KB/s)
[R] TYPE A
[R] 200 Type set to A
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,137)
[R] Opening data connection IP: 192.168.1.101 PORT: 1161
[R] LIST -al
[R] 150 Connection accepted
[R] 226 Transfer OK
[R] List Complete: 431 bytes in 0,06 seconds (6,8 KB/s)
Transfer queue completed
Transferred 1 file totaling xxxxxxx MB in xxxxxxxxxx seconds (xxxxxxxxxx KB/s)

File from Shuttle to Fredje  (  WITH #port_promiscuous=YES ==> COMMENTED)
----------------------------
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] TYPE I
[R] 200 Type set to I
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,100,243,139).
[R] PORT 192,168,1,100,243,139
[R] 200 Port command successful
[R] STOR xxxxxxxxxxx.xxxx
[R] 150 Opening data channel for file transfer.
[L] RETR xxxxxxxxxxx.xxxx
[L] 150 Opening BINARY mode data connection for xxxxxxxxxxxxxx.xxxxx (xxxxxxxxxxx bytes).
[L] 226 Transfer complete.
[R] 226 Transfer OK
Transferred: xxxxxxxxxxxxxxx.xxxxx xxxxxxx MB in xxxxx seconds (xxxxxxxx KB/s)
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,100,90,184).
[L] Opening data connection IP: 192.168.1.100 PORT: 23224
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 189 bytes in 0,03 seconds (6,0 KB/s)
[R] TYPE A
[R] 200 Type set to A
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,18)
[R] Opening data connection IP: 192.168.1.101 PORT: 1042
[R] LIST -al
[R] 150 Connection accepted
[R] 226 Transfer OK
[R] List Complete: 1 KB in 0,03 seconds (60,5 KB/s)
Transfer queue completed
Transferred 1 file totaling xxxxxxxxx MB in xxxxxxxxxxx seconds (xxxxxxxxx KB/s)

File from Fredje to Shuttle (port_promiscuous=YES  ==> NOT COMMENTED)
-----------------------------

[R] TYPE I
[R] 200 Type set to I
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,148)
[L] PORT 192,168,1,101,4,148
[L] 200 PORT command successful. Consider using PASV.
[L] STOR xxxxxxxx.xxxxxxx
[L] 500 OOPS: vsf_sysutil_bind
[L] Transfer Failed!
[L] TYPE A
[L] 500 OOPS: priv_sock_get_cmd
[L] PASV
[L] Connection lost: 192.168.1.100
[R] TYPE A
[R] 200 Type set to A
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,149)
[R] Opening data connection IP: 192.168.1.101 PORT: 1173
[R] LIST -al
[R] 150 Connection accepted
[R] 226 Transfer OK
[R] List Complete: 1 KB in 0,05 seconds (34,5 KB/s)
Transfer queue completed
1 File failed to transfer

FILE TRANSFER FAILED!

==> #port_promiscuous=YES ==> COMMENTED and it worked for transfers from Windows FTP server to Ubuntu vsftpd.

			[L] TYPE I
			[L] 200 Type set to I
			[R] TYPE I
			[R] 200 Switching to Binary mode.
			[L] PASV
			[L] 227 Entering Passive Mode (192,168,1,101,4,166)
			[R] PORT 192,168,1,101,4,166
			[R] 500 Illegal PORT command.
			Site to Site Transfer Failed! (Attempting alternative method)
			[R] PASV
			[R] 227 Entering Passive Mode (192,168,1,100,161,76).
			[L] PORT 192,168,1,100,161,76
			[L] 200 Port command successful
			[R] STOR xxxxxxxxxxxxx.xxxxx
			[L] RETR xxxxxxxxxxx.xxxx
			[R] 150 Ok to send data.
			[L] 150 Opening data channel for file transfer.
			[L] 226 Transfer OK
			[R] 226 Transfer complete.
			Transferred: xxxxxxxxxx.xxxx xxxxx MB in xxxxx seconds (xxxxx KB/s)
			[L] TYPE A
			[L] 200 Type set to A
			[L] PASV
			[L] 227 Entering Passive Mode (192,168,1,101,4,167)
			[L] Opening data connection IP: 192.168.1.101 PORT: 1191
			[L] LIST -al
			[L] 150 Connection accepted
			[L] 226 Transfer OK
			[L] List Complete: 1 KB in 0,03 seconds (63,9 KB/s)
			[R] TYPE A
			[R] 200 Switching to ASCII mode.
			[R] PASV
			[R] 227 Entering Passive Mode (192,168,1,100,129,60).
			[R] Opening data connection IP: 192.168.1.100 PORT: 33084
			[R] LIST -al
			[R] 150 Here comes the directory listing.
			[R] 226 Directory send OK.
			[R] List Complete: 189 bytes in 0,05 seconds (3,9 KB/s)
			Transfer queue completed
			Transferred 1 file totaling xxxxx MB in xxxxxx seconds (xxxxx KB/s)


#################
I assume that (Site to Site Transfer Failed! (Attempting alternative method)) is normal now that it works with #port_promiscuous=YES?
#################


Transfer-log between Fredje and Stacker (Windows and Ubuntu) ==> (  WITH #port_promiscuous=YES ==> COMMENTED)
------------------------------------------------------------

File from Fredje to Stacker
----------------------------
[R] TYPE I
[R] 200 Type set to I
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,152)
[L] PORT 192,168,1,101,4,152
[L] 500 Illegal PORT command.
Site to Site Transfer Failed! (Attempting alternative method)
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,39,137).
[R] PORT 192,168,1,102,39,137
[R] 200 Port command successful
[L] STOR xxxxxxxxxxxxxxx.xxxxxxxxxxx
[R] RETR xxxxxxxxxxx.xxxxxxxxxxx
[L] 150 Ok to send data.
[R] 150 Opening data channel for file transfer.
[R] 226 Transfer OK
[L] 226 Transfer complete.
Transferred: xxxxxxxxxxxxx.xxxxxxxxx xxxxxxxx MB in xxxxxxxxxxx seconds (xxxxxxxxxx KB/s)
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,100,145).
[L] Opening data connection IP: 192.168.1.102 PORT: 25745
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 1 KB in 0,03 seconds (36,0 KB/s)
[R] TYPE A
[R] 200 Type set to A
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,153)
[R] Opening data connection IP: 192.168.1.101 PORT: 1177
[R] LIST -al
[R] 150 Connection accepted
[R] 226 Transfer OK
[R] List Complete: 1 KB in 0,03 seconds (52,3 KB/s)
Transfer queue completed
Transferred 1 file totaling xxxxxxxxxx MB in xxxxxxx seconds (xxxxxxxxx KB/s)

File from Stacker to Fredje
-----------------------------
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] TYPE I
[R] 200 Type set to I
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,248,105).
[R] PORT 192,168,1,102,248,105
[R] 200 Port command successful
[R] STOR xxxxxxxxxx.xxxxxxxxx
[R] 150 Opening data channel for file transfer.
[L] RETR xxxxxxxxxxx.xxxxxxxxx
[L] 150 Opening BINARY mode data connection for xxxxxxxxxxxxx.xxxxxxx (xxxxxxxxxxx bytes).
[L] 226 Transfer complete.
[R] 226 Transfer OK
Transferred: xxxxxxxxxxxxx.xxxxxxxxxxxx xxxxxxxxxx MB in xxxxxxxxxxx seconds (xxxxxxxxx KB/s)
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,43,204).
[L] Opening data connection IP: 192.168.1.102 PORT: 11212
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 1 KB in 0,03 seconds (36,0 KB/s)
[R] TYPE A
[R] 200 Type set to A
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,101,4,159)
[R] Opening data connection IP: 192.168.1.101 PORT: 1183
[R] LIST -al
[R] 150 Connection accepted
[R] 226 Transfer OK
[R] List Complete: 1 KB in 0,06 seconds (29,3 KB/s)
Transfer queue completed
Transferred 1 file totaling xxxxxxxx MB in xxxxxxxx seconds (xxxxxxxxxx KB/s)

########
Finally, here comes the trouble.
########


Transfer-log between Stacker and Shuttle (2 x vsftpd)
-----------------------------------------------------
File from Shuttle to Stacker
-----------------------------
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] TYPE I
[R] 200 Switching to Binary mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,222,227).
[R] PORT 192,168,1,102,222,227
[R] 500 Illegal PORT command.
Site to Site Transfer Failed! (Attempting alternative method)
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,100,201,93).
[L] PORT 192,168,1,100,201,93
[L] 500 Illegal PORT command.
Site to Site Transfer Failed!
[R] Transfer Failed!
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,200,194).
[L] Opening data connection IP: 192.168.1.102 PORT: 51394
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 2 KB in 0,05 seconds (45,8 KB/s)
[R] TYPE A
[R] 200 Switching to ASCII mode.
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,100,66,120).
[R] Opening data connection IP: 192.168.1.100 PORT: 17016
[R] LIST -al
[R] 150 Here comes the directory listing.
[R] 226 Directory send OK.
[R] List Complete: 189 bytes in 0,05 seconds (4,0 KB/s)
Transfer queue completed
1 File failed to transfer


File from Stacker to Shuttle
-----------------------------
[R] TYPE I
[R] 200 Switching to Binary mode.
[L] TYPE I
[L] 200 Switching to Binary mode.
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,100,133,100).
[L] PORT 192,168,1,100,133,100
[L] 500 Illegal PORT command.
Site to Site Transfer Failed! (Attempting alternative method)
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,146,93).
[R] PORT 192,168,1,102,146,93
[R] 500 Illegal PORT command.
Site to Site Transfer Failed!
[L] Transfer Failed!
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,106,23).
[L] Opening data connection IP: 192.168.1.102 PORT: 27159
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 2 KB in 0,02 seconds (134,6 KB/s)
[R] TYPE A
[R] 200 Switching to ASCII mode.
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,100,42,22).
[R] Opening data connection IP: 192.168.1.100 PORT: 10774
[R] LIST -al
[R] 150 Here comes the directory listing.
[R] 226 Directory send OK.
[R] List Complete: 189 bytes in 0,05 seconds (3,9 KB/s)
Transfer queue completed
1 File failed to transfer


#####
What's the problem between those 2 vsftpd's?
I've checked it with a 3rd ==> Same thing: 
Windows - Ubunutu = OK
Ubuntu - Ubuntu = NOT OK.
#####

Grz,
Digi

---

### Post by the_original_billq on 2010-10-28
Looks like you may have a conflict on port 20 on shuttle.  From stacker, in a terminal, try:

```

telnet shuttle 20

```

and see if something answers.

You can also do a 

```

netstat -pna|awk '$4 ~ /:20/ {print $7}'

```

on shuttle, and see what's running on port 20.

-Bill

---

### Post by Digifreakske on 2010-10-29
fredje@serverstacker:~$ telnet 192.168.1.100 20
Trying 192.168.1.100...
telnet: Unable to connect to remote host: Connection refused


leech@fredjeshuttle:~$ netstat -pna
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.1.100:22        192.168.1.104:50777     ESTABLISHED -               
tcp        0      0 192.168.1.100:22        192.168.1.102:40062     TIME_WAIT   -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     3848     -                   /var/run/acpid.socket
unix  5      [ ]         DGRAM                    3382     -                   /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     2530     -                   @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     4184     -                   /var/run/mysqld/mysqld.sock
unix  2      [ ]         DGRAM                    2638     -                   @/org/kernel/udev/udevd
unix  3      [ ]         STREAM     CONNECTED     4631     -                   
unix  3      [ ]         STREAM     CONNECTED     4630     -                   
unix  2      [ ]         DGRAM                    4491     -                   
unix  2      [ ]         DGRAM                    3936     -                   
unix  2      [ ]         DGRAM                    3847     -                   
unix  3      [ ]         DGRAM                    2674     -                   
unix  3      [ ]         DGRAM                    2673     -                   
unix  3      [ ]         STREAM     CONNECTED     2621     -                   @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2620     -



What's next?

---

### Post by the_original_billq on 2010-10-29
sorry, try that netstat using sudo....  We're looking for something that has port 20 open that isn't ftpd, so you could run:

```

sudo netstat -pna|grep ":20"

```

---

### Post by Digifreakske on 2010-10-29
I changed the ftp port from 21 to 201.
And played around with other settings, can't get it to work.

This is what i get with the command on the 2 servers:

root@serverstacker:/home/fredje# sudo netstat -pna|grep ":20"
tcp        0      0 0.0.0.0:201             0.0.0.0:*               LISTEN      1309/vsftpd



root@fredjeshuttle:/home/leech# sudo netstat -pna|grep ":20"
tcp        0      0 0.0.0.0:201             0.0.0.0:*               LISTEN      688/vsftpd

---

### Post by the_original_billq on 2010-11-04
> **Digifreakske said:**
> 

vsftpd.conf from Shuttle and Stacker
------------------------------------
root@fredjeshuttle:/home/leech# cat /etc/vsftpd.conf

pasv_enable=YES
port_enable=YES
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to Fredje's Linux FTP Server.
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
hide_file={.*,lost+found, RECYCLER, System Volume Information}
pasv_promiscuous=YES

Grz,
Digi

Hi,

I'd like you to try this.  Back up your existing vsftpd.conf, and replace it with this:

```


listen=YES
listen_port=2021
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_world_readable_only=YES
connect_from_port_20=NO
hide_ids=YES
pasv_min_port=6500
pasv_max_port=6550
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES
one_process_model=YES
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=50000


```

Then restart vsftpd and retry your transfer.

-Bill

---

### Post by Digifreakske on 2010-11-05
I just did what you suggested ==>

[R] Connecting to 192.168.1.100 -> IP=192.168.1.100 PORT=2021
[R] Connected to 192.168.1.100
[R] 500 OOPS: vsftpd: security: 'one_process_model' is anonymous only
[R] Connection failed
[R] Delaying for 120 seconds before reconnect attempt #1


I've set one_process_model to NO and i tried again ==>

[L] TYPE I
[L] 200 Switching to Binary mode.
[R] TYPE I
[R] 200 Switching to Binary mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,25,100).
[R] PORT 192,168,1,102,25,100
[R] 500 Illegal PORT command.
Site to Site Transfer Failed! (Attempting alternative method)
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,100,25,134).
[L] PORT 192,168,1,100,25,134
[L] 500 Illegal PORT command.
Site to Site Transfer Failed!
[R] Transfer Failed!
[L] TYPE A
[L] 200 Switching to ASCII mode.
[L] PASV
[L] 227 Entering Passive Mode (192,168,1,102,25,140).
[L] Opening data connection IP: 192.168.1.102 PORT: 6540
[L] LIST -al
[L] 150 Here comes the directory listing.
[L] 226 Directory send OK.
[L] List Complete: 1 KB in 0,02 seconds (110,4 KB/s)
[R] TYPE A
[R] 200 Switching to ASCII mode.
[R] PASV
[R] 227 Entering Passive Mode (192,168,1,100,25,126).
[R] Opening data connection IP: 192.168.1.100 PORT: 6526
[R] LIST -al
[R] 150 Here comes the directory listing.
[R] 226 Directory send OK.
[R] List Complete: 462 bytes in 0,02 seconds (28,2 KB/s)
Transfer queue completed
1 File failed to transfer


This seems to be a strange problem.
I'll try to send an email to the guys of vsftpd.


Grz,
Digi

---

