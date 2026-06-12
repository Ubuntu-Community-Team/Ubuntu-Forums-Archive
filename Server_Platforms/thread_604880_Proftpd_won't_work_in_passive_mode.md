---
title: "Proftpd won't work in passive mode"
date: 2007-11-06
forum: Server Platforms
---

### Post by austin987 on 2007-11-06
I've got proftpd setup and running on xubuntu feisty. FTP works fine in active mode (both inside and outside lan), but passive only works from inside the lan. Ports 20-21 and 60000-61000 are open in firestarter (computer is the DMZ, so all ports are open in the router). Here is the FTP configuration. Any help would be appreciated.

```
ServerType standalone
DefaultServer on
Umask 022
ServerName "server_name"
ServerIdent on "FTP Server"
ServerAdmin admin_email@gmail.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 60000 61000
MasqueradeAddress address.dyndns.org
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayFirstChdir .message
User nobody
Group nobody
DirFakeUser on nobody
DirFakeGroup on nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 10
#gp_random_password_length 10
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine on
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
```

---

### Post by austin987 on 2007-11-07
bump

---

### Post by Daveski on 2007-11-08
> **austin987 said:**
> I've got proftpd setup and running on xubuntu feisty. FTP works fine in active mode (both inside and outside lan), but passive only works from inside the lan.

Had this problem myself and could not figure out where the problem was. The remote client was getting the correct public IP and a port number in my open port ranges. Just commented out my Masquerade lines and it all works now. Does removing your Masquerade lines work for you?

Looks like my NAT router has special provision for FTP and does the masquerading translation itself.

---

### Post by austin987 on 2007-11-13
Yes, thank you so much. It appears to be working from inside the firewall (using the external hostname), which didn't before. I'll test it from outside the firewall later tonight.

Thanks again!

---

### Post by austin987 on 2007-11-14
Tested outside as well, working great. Thanks again Daveski!

---

### Post by Daveski on 2007-11-14
Really glad this worked for you. Had me scratching my head for ages.

---

