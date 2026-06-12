---
title: "Using smb.conf to lock down share to Windows Domain Accounts"
date: 2008-10-30
forum: Server Platforms
---

### Post by queppu on 2008-10-30
Hi,

I've been trolling across the internet reading every bit of Ubuntu/Samba tutorials I can find on getting windows authentication going and I've got stuck on one aspect.  My Ubuntu server has joined my Windows Domain and is showing up in Active Directory.

I followed this tutorial [http://www.enterprisenetworkingplanet.com/netos/article.php/3487081](http://www.enterprisenetworkingplanet.com/netos/article.php/3487081) and everything appears to be working.  wbinfo -u/-g shows the correct information.

Now I want to create shares in smb.conf and lock them down to specific Windows users.  But that's where are running in problems.  I don't really know how to configure everything so my Domain\Username user can have access.

Here is my current smb.conf file:
```

[global]
workgroup = DOMAIN
realm = DOMAIN.COM.AU
preferred master = no
server string = Samba file server
security = ADS
encrypt passwords = yes
log level = 3
vlog file = /var/log/samba/%m
max log size = 50
winbind separator = +
idmap uid = 10000-20000
idmap gid = 10000-20000
template homedir = /home/winnt/%D/%U
template shell = /bin/bash

[web]
path = /var/www
available = yes
valid users = @DOMAIN+USERNAME
read only = no
browsable = yes
public = yes
writable = yes

```

But when I try to access the share I get a windows error, "You might not have permission to use this network resource: Logon failure unknown user name or bad password".

Now I know I've probably missed a step and not configured a file somewhere correctly but that's probably the main reason I'm asking for help because I really don't know what I'm doing from here lol.  Any assistance would be appreciated.

Thanks for taking the time to read my post!

---

### Post by alienprdkt on 2008-10-30
[INDENT]nano /etc/samba/smb.conf
[/INDENT]We're going to configure the samba server so you need a valid user and password to access the share. You don't want random people to have read/write access to your files now do we?[INDENT][global]
workgroup = WORKGROUP
netbios name = Gateway
server string = mysambaserver
security = user
username map = /etc/samba/smbusers
log file = /var/log/smb/samba.%m
max log size = 50
local master = no
 [public]
comment = shared
path = /home/smbtc
valid users = smbtc
guest ok = no
browseable = yes
writable = yes
[/INDENT]Now we need to add users to the PC and to samba.[INDENT]useradd smbtc
mkdir /home/smbtc
chown smbtc /home/smbtc -R
chgrp users /home/smbtc -R
usermod -d /home/smbtc smbtc
smbpasswd -a smbtc
[/INDENT]Now all we need to do is start the service and make it start up on boot.
 /etc/init.d/samba restart

---

### Post by queppu on 2008-10-30
Hi, thanks for your prompt reply!

I made the changes you suggested but I'm not getting the outcome I was after.  It prompts me for a username and password when I try to access the public share when I want it to recognise my Windows username and log me on automatically, just like NTFS permissions work for Windows shares.  Is this even possible?

I wouldn't mind typing a username and password in each time if I was only looking to do Windows file sharing but I'm also using Dreamweaver and I can't upload files across the network to these shares because it doesn't support supplying your own username and password for LAN connections.

I thought that because the machine is now part of my Active Directory Domain that when I try to authenticate with Samba it would do a Kerberos lookup for the authentication?  But I might be reaching here lol.

I'd love to ideally be able to lock down these Samba shares to specific Windows users or groups without requiring Ubuntu username and password authentication.  Is this even possible?

---

### Post by alienprdkt on 2008-10-31
If you want to integrate Samba to work with Windows AD Authentication (thats too dificult for me) btit can be done, and I can give you a link to an online book that can tell you how to do it;)
[Using Samba third edition]("http://safari.oreilly.com/0596007698/samba3-PREFACE-2")

hope it helps you out;)
any question anyone could ever have or want to do with Samba:D

---

### Post by queppu on 2008-10-31
Ok thanks very much for your help.  I will give this book a read and see how I go!

---

### Post by queppu on 2008-10-31
Hmm, not finding exactly what I need in this book.  I still don't see how I can setup my Ubuntu box so my windows users can log onto it or access the Samba shares.

I did notice that when I run smbstatus while accessing a public share on the Samba server it shows my computer as the username connected.  I did try however to enter this username into the "valid users" value in smb.conf but it still didnt' give me access.

Any other thoughts anyone?

---

### Post by alienprdkt on 2008-10-31
have a look at this page :

[http://oreilly.com/catalog/samba/chapter/book/ch06_05.html](http://oreilly.com/catalog/samba/chapter/book/ch06_05.html)
beginning of chapter is here ... 

[http://oreilly.com/catalog/samba/chapter/book/ch06_01.html](http://oreilly.com/catalog/samba/chapter/book/ch06_01.html)

---

