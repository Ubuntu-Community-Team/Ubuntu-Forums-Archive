---
title: "Problem with proftpd server"
date: 2011-04-16
forum: Server Platforms
---

### Post by princebouja on 2011-04-16
Hello everyone,

I set an ftp server using proftpd on my ubuntu 10.10. but when I connect to it from another computer with FileZilla, the option "download" is disabled and I can't download any file. I tried to modify the permissions of the files on the server so they can be accessible by everyone (444), but the option "download" of FileZilla is still disabled (the option "downlod" is enabled only on the server). is there any solution to fix this problem? thank you.

this is my /etc/proftpd/proftpd.conf:

```
ServerType standalone
DefaultServer on
Umask 022
ServerName "41.229.1.54"
ServerIdent on "theeptbook"
ServerAdmin email@example.org
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120

User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode ascii
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores on

SystemLog /var/log/secure
RequireValidShell off

<Limit LOGIN>
  AllowUser eptbook
  DenyALL
</Limit>


<Anonymous /home/ftp>
User eptbook
Group eptbookgroup
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"

<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  STOR STOU  APPE  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>
```

---

### Post by usatonycuba on 2011-04-16
I do not see any reference to ( [TimeoutStalled]("http://www.proftpd.org/docs/directives/linked/config_ref_TimeoutStalled.html"), [TransferRate]("http://www.proftpd.org/docs/directives/linked/config_ref_TransferRate.html") or [MaxRetrieveFileSize]("http://www.proftpd.org/docs/directives/linked/config_ref_MaxRetrieveFileSize.html") ) in your conf file... ?

---

### Post by princebouja on 2011-04-17
I thought that their default values would be affected... Anyway, i added these lines to my conf:

```
TimeoutStalled 3600
MaxStoreFileSize *
TransferRate RETR 10000
TransferRate APPE,STOR 10000
```

but the problem isn't solved yet :(

---

### Post by princebouja on 2011-04-17
After trying other computers, I noticed that comptuers that run on linux can download the files on the server with filezilla, the problem exist only for the computers which run on Windows (I tried only Windows 7). Unfortunately, I can't oblige everyone one who access to my server to use Linux, so i must fix this problem, so all the computers could download the files on the server.

---

### Post by usatonycuba on 2011-04-17
have you tried **UseReverseDNS on** ..?

> Normally, incoming active mode data connections and outgoing passive mode data connections to Have Performed reverse DNS lookup on the remote host's IP address. In a chroot environment (Such as <Anonymous> or DefaultRoot), the / etc / hosts file can not be checked and the only possible resolution is via DNS. If for Some reason, DNS is not available or Improperly configured this CAN result in proftpd blocking ("stalling") Until the libc resolve code times out. Disabling this directive Prevents proftpd from Attempting to reverse-lookup data connection IP addresses.

Have you used the **site manager**..  is better in order to avoiding going to whole the network wizard. You can easy edited your connection with the network wizard ("but there can be a few problems")..(if you can already see that you can connect to your ftp some how). So.. with the site manager, you have to set up the **login type** allowing you to **save** your ftp user and password, make your type set to **account**.. it should have not problems connecting. In the wizard, to make choose **get ip address from** (if dynamic ip) will be the FileZilla project... so you can change "WHATEVER_YOUR_USING_HERE.dyndns.org" to "http://ip.filezilla-project.org/ip.php"... that way should be straight up the problem


> If we follow one of the many manuals that are on the net about installing and configuring an FTP server using proftpd, we will not have too many problems to work within the local network... But if we try to connect from the outside is very possible that we have to make some adjustments if we are in a local network router.

It should be added to / etc / proftpd.conf, below the line of port 21, these two:

MasqueradeAddress xxx.xxx.xxx.xxx (server's public IP)
PassivePorts 60001 60005 (may be another range of ports)

There are redirected to our router ports 21, 60001, 60002, 60003, 60004 and 60005 to the local IP where we installed the server... It is recommended to enable the firewall to prevent unwanted connections.

---

