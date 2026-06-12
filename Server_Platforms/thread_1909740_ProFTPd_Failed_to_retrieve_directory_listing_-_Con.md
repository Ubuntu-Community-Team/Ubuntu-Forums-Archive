---
title: "ProFTPd Failed to retrieve directory listing - Connection closed by server"
date: 2012-01-15
forum: Server Platforms
---

### Post by kylemarlin on 2012-01-15
Hello everyone,

I was trying to set up an FTP and have reached my wit's end.  I worked out all the errors in setting it up, except for one.  Everytime I try to connect to this server, it fails to show me the directory listing.  I have no firewall, so I assume that it has something to do with the permissions.  I have been reading many topics on this, and have done all that they suggested, but to no avail.  **It appears that the problem is with the MLSD command, as the server closes the connection after that command.  Additionally, when the LIST command is sent to the server, it times out.**  I'm not sure what causes this, as Ubuntu and FTP are not my forte when it comes to computers.  As always, any help is greatly appreciated.  If I manage to figure out what the issue is, I will go ahead and post it.  Thanks to everyone.  Please find some code attached below.

For reference, I used all the suggestions in [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1182594[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1182594") and still had no working result.

Below are 2 quotes of the chatter between the FTP Client and Server.  This first one is from an external network running FileZilla as the client to the server, running ProFTPd.

[PHP]
Status:	Connecting to 24.239.84.211:65534...
Status:	Connection established, waiting for welcome message...
Response:	220 Marlin Family Server
Command:	USER kyle
Response:	331 Password required for kyle
Command:	PASS ******
Response:	230-Welcome to the Marlin Family Server, kyle
Response:	 
Response:	 You are user 1 out of a maximum of 10 authorized logins.
Response:	 Current time is Sun Jan 15 19:49:57 2012.
Response:	 The administrator can be reached here: [email address censored]
Response:	230 Anonymous access granted, restrictions apply
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PORT 192,168,2,103,228,226
Response:	500 Illegal PORT command
Command:	PASV
Response:	227 Entering Passive Mode (24,239,84,211,254,121).
Command:	MLSD
Error:	Connection closed by server
Error:	Failed to retrieve directory listing
[/PHP]

This second one is from my actual server to itself, using FileZilla as the client program, and ProFTPd as the server program.

[PHP]
Status:	Resolving address of localhost
Status:	Connecting to 127.0.0.1:65534...
Status:	Connection established, waiting for welcome message...
Response:	220 Marlin Family Server
Command:	USER kyle
Response:	331 Password required for kyle
Command:	PASS ******
Response:	230-Welcome to the Marlin Family Server, kyle
Response:	 
Response:	 You are user 1 out of a maximum of 10 authorized logins.
Response:	 Current time is Sun Jan 15 20:32:16 2012.
Response:	 The administrator can be reached here: [email address censored]
Response:	230 Anonymous access granted, restrictions apply
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (24,239,84,211,246,181).
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
[/PHP]

Finally, this last snippet of code should be where the problem lies.  This is the code behind my ProFTPd program, and I think the error is somewhere in the permissions section.  There is only one user, "kyle".  

[PHP]
ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "Marlin Family Server"
ServerAdmin [email address censored]
IdentLookups off
UseReverseDNS off
Port 65534
PassivePorts 60000 65534
MasqueradeAddress kylemarlin.endoftheinternet.org
TimesGMT off
MaxInstances 30
MaxLoginAttempts 5
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores on
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
TLSOptions AllowClientRenegotiation
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<IfModule mod_facts.c>
FactsAdvertise off
</IfModule>
<Limit LOGIN>
  Allow from all
  Deny from all
</Limit>

<Anonymous /test>
User kyle
Group group1
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>
[/PHP]

---

### Post by kylemarlin on 2012-01-16
Update: I still haven't been able to figure this out.  I've been trying to get an FTP up and running for about 50 total hours now, and still no luck.  I did something I did not want to, and tried to use Pure-FTPd, which I do not like at all.  I want a simple GUI like PrFTPd, but I figured I'd give it a shot.  I can't get Pure-FTPd working either, but I get a 530 invalid username, so I'm gonna try and see what I can do, but I'm finding Pure-FTPd to be awful when it comes to configuring.  Does anyone have any ideas, or any suggestions at all as to a good FTP with a good GUI?  Thanks again for everyone's consideration.

---

### Post by robdavidson on 2012-01-17
I am experiencing nearly the exact same issue with the exception that I am able to access the server and view directories via the local network.

Any real help is greatly appreciated.

Thanks in advance.

---

### Post by robdavidson on 2012-01-17
UPDATE:
Opening up the PASSIV ports in **/etc/proftpd/proftpd.conf** on or near line 47: **PassivePorts   49152 65534** appeared to have fixed this issue.
However, after disconnecting and reconnecting to the server, directory listings were once again inaccessible.
Additionally, directory listings are now intermittently working but there seems to be no rhyme or reason to its success or failure.

Completely flabbergasted, *(isn't that a cool word?)*, I continue to troubleshoot.

---

### Post by jacques_za on 2012-02-19
Also ran into this with ProFTPd.  I haven't solved it yet, but it seems to be something to do with the LIST/MLSD issue.  Try to force your client to use LIST instead of MLSD and see if that helps.

Or try connecting with a different client (like a web browser).

That seems to work for me, but I don't know what to change in ProFTPd to fix the compatibility. :(

---

### Post by Jumbs on 2012-05-28
> **jacques_za said:**
> Also ran into this with ProFTPd.  I haven't solved it yet, but it seems to be something to do with the LIST/MLSD issue.  Try to force your client to use LIST instead of MLSD and see if that helps.

Or try connecting with a different client (like a web browser).

That seems to work for me, but I don't know what to change in ProFTPd to fix the compatibility. :(

Same here.
Works fine in web, fails in Filezilla.

---

