---
title: "Problems with gproftpd and PASV mode"
date: 2007-07-16
forum: Server Platforms
---

### Post by capnbenzo on 2007-07-16
Hey Everyone,

I am having a problem setting up GPROFTPD on Ubuntu.  I have forwarded all necessary ports and followed all the other howto's on here completely, as far as I can tell.  Clients outside my network seem to have connections time out when switching to PASV mode, even though passive is denied in my .conf file and on the client side.

Here is the client log.

[22:24:52] 220 My FTPD
[22:24:52] USER userftp
[22:24:52] 331 Password required for userftp.
[22:24:52] PASS (hidden)
[22:24:52] 230 Anonymous access granted, restrictions apply.
[22:24:52] SYST
[22:24:52] 215 UNIX Type: L8
[22:24:52] Detected Server Type: UNIX
[22:24:52] FEAT
[22:24:52] 211-Features:
[22:24:52]  MDTM
[22:24:52]  REST STREAM
[22:24:52]  SIZE
[22:24:52] 211 End
[22:24:52] PWD
[22:24:52] 257 "/" is current directory.
[22:24:52] TYPE A
[22:24:52] 200 Type set to A
[22:24:52] PASV
[22:24:52] 501 PASV: Operation not permitted
[22:24:52] Automatic failover of data connection mode from "Passive Mode (PASV)" to "Active Mode (PORT)".
[22:24:52] PORT 10,0,1,195,10,31
[22:24:52] 200 PORT command successful
[22:24:52] LIST -aL
[22:25:52] Timeout (60s).
[22:25:52] Active Help: [http://www.smartftp.com/support/kb/index.php/74](http://www.smartftp.com/support/kb/index.php/74)
[22:25:52] Client closed the connection.



Server log in next post!

---

### Post by capnbenzo on 2007-07-16
Here's my .conf file.

"ServerType standalone
DefaultServer on
Umask 022
ServerName "caseychopek.kicks-***.net"
ServerIdent on "My FTPD"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups off
UseReverseDNS off
Port 22
PassivePorts 49161 65534
#MasqueradeAddress None
TimesGMT on
MaxInstances 30
MaxLoginAttempts 113
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayFirstChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser userftp
  DenyALL
</Limit>
<Anonymous /var/ftp>
User userftp
Group userftp
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Limit EPSV PASV>
DenyAll
</Limit>
</Anonymous>

"


Thanks in advance for any help!

---

### Post by Mr. C. on 2007-07-16
Do you have a firewall / router ? 

Does it support non PASV FTP ?

MrC

---

### Post by capnbenzo on 2007-07-17
I do.  It's a Linksys WRT54G.  I did some googling and it looks like it might be a router problem.  Most people with the WRT54G can't run an FTP server behind it.  Hopefully I won't need a new router!  I guess I have 2 questions-

Are there any workarounds for this anyone knows of?

Is there a good wireless router anyone can suggest which DOES support running an FTP server?


Thanks

---

### Post by Mr. C. on 2007-07-17
Unless the router supports non-PASV (eg. PORT) based FTP, its firewall will block the data channel.

Forgive me if I'm being too elementary:

In FTP, the client connects to your open port 21 to create the command channel.  The client also sends an IP address and a port number where it can be reached for the data channel.  The server then makes the data connection from its port 20 to the client's randomly choosen high numbered port.  A NATing firewall must peek inside the TCP/IP packets for FTP to learn about which address pair is making the connection, so that it can add that pair to its NAT table.  Otherwise, it just sees your server's LAN ip making some outbound connection to the client, but sees the return inbound data addressed to your WAN IP, so the packets are dropped.

Please see FTP notes, Week 10 here:  [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by freebeer on 2007-07-17
I ran into the same problem.  I couldn't fix the problem (I didn't spend lots of time on it), chickened out and just use the active mode.

---

