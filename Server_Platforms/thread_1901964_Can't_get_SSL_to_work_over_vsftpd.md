---
title: "Can't get SSL to work over vsftpd"
date: 2011-12-29
forum: Server Platforms
---

### Post by bbyam on 2011-12-29
I've been trying and searching online for days now, but can't seem to get SSL working on vsftpd.  I have it set up right now where SSL is not required - I can log in just fine and everything works perfectly with normal FTP.  However, as soon as I try to use Implicit SSL, Auth SSL, or Auth TLS with FireFTP it just plain doesn't work.  I tried Filezilla as well with no luck (connecting from a Windows machine).  I'm using Ubuntu server 10.04.2 with vsftpd 2.2.2.

[LIST]
[*]**FireFTP No encryption port 21**: works fine
[*]**FireFTP Implicit SSL port 21**:
Unable to make a connection. Please try again.
[*]**FireFTP Auth SSL port 21**:
220 (vsFTPd 2.2.2)
       AUTH SSL
234 Proceed with negotiation.
       PBSZ 0
And that's it, just doesn't connect.
[*]**FireFTP Auth TLS port 21**:
220 (vsFTPd 2.2.2)
       AUTH TLS
234 Proceed with negotiation.
       PBSZ 0
And that's it, just doesn't connect.
[*]**Filezilla no encryption port 21**: works fine
[*]**Filezilla Require Implicit FTP over TLS**:
Status:	Connecting to xx.xxx.xxx.xx:21...
Status:	Connection established, initializing TLS...
Error:	Could not connect to server
[*]**Filezilla Require Explict FTP over TLS**:
Status:	Connecting to xx.xxx.xxx.xx:21...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.2.2)
Command:	AUTH TLS
Response:	234 Proceed with negotiation.
Status:	Initializing TLS...
Error:	Could not connect to server
[/LIST]

Anyone have any ideas what might be wrong, or what logs I might be able to look at?  /var/log/vsftpd.log has nothing of interest.  I'd like to always force SSL.

Here's my vsftpd.conf:
```

virtual_use_local_privs=YES
ssl_enable=YES
force_local_data_ssl=NO
force_local_logins_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
require_ssl_reuse=NO

write_enable=YES
guest_enable=NO
user_sub_token=$USER
chroot_local_user=YES
chroot_list_enable=NO
local_root=/srv/fshome/ftp_accounts/$USER
hide_ids=YES

local_umask=0111

listen_port=21

pasv_enable=YES
pasv_min_port=36000
pasv_max_port=36010

listen=YES
anonymous_enable=NO
local_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

---

### Post by bbyam on 2011-12-30
Okay, it turns out it was some sort of firewall issue where I was testing access.  It is as if only plaintext data is allowed on both port 21 and 990, as the TCP connection works but no data transfer is allowed.  Testing from a different internet connection worked fine.

From reading various forum posts, this text-only on port 21 seems to be a common restriction, so I decided to switch to sftp instead after my searching revealed that OpenSSH now supports chroot jails which I can jail them on the external file storage drive I'm using.

---

