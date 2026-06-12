---
title: "Windows 7 ignores samba user authentication"
date: 2010-06-11
forum: Server Platforms
---

### Post by memeri on 2010-06-11
Although I've tried to configure samba to require user authentication, windows 7 logs onto both of my ubuntu accounts automatically.

ubuntu 9.10.
/etc/samba/smb.conf:

```
#======================= Global Settings =======================

[global]

   workgroup = usnthem
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

####### Authentication #######
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes
   read only = no

#  This seems to help
   path = /home
   valid users = %S
```

Possibly relevant:

```
$ sudo pdbedit -L -w
nobody:65534:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:
mary:1001:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:159EA51341BD0FB531D630F25B2672BD:[U          ]:LCT-4C114AC6:
mark:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:32C5FA7B2B28B47B6959536DC914C4D0:[U          ]:LCT-4C11755A:
```

Win 7 just gives instant access to the complete directory trees of mark and mary without presenting a logon dialog. Thoughts?

---

### Post by srivo on 2010-06-11
windows 7 professional or Home edition?

---

### Post by memeri on 2010-06-11
It's "Windows 7 starter" that comes loaded on a new EeePC netbook.

---

### Post by srivo on 2010-06-12
Check that package libpam-smbpass is installed. Even it may be possible that it doesn't work!

I have a similar problem with Vista home edition. My personal Laptop is Windows XP professional and work fine, but the one of my wife is Windows Vista and doesn't. It's alway mapped as a bad user all access work except personal folder on ther server

---

### Post by Morbius1 on 2010-06-12
Just so you know there are two design flaws ( my opinion ) in every Windows I've ever used ( WinNT3.51, WinNT4, Win2K, WinXP,.. ). 

(1) This has to do with how the Windows client browses the network. Along with the  request to view available shares it will actually pass it's local  Windows login username and password. If it matches the samba username  and password then no authentication is required because it's already  been supplied.

(2) If you successfully connect to a remote share with the proper username and password credentials, Windows will save and automatically reuse those credentials  - forever. There's actually a way to turn that off in Windows ( WinXP instructions ):
[http://www.iss.net/security_center/reference/vuln/winxp-credential-storage-allowed.htm](http://www.iss.net/security_center/reference/vuln/winxp-credential-storage-allowed.htm)

It's easy enough to test all of this though and that's to change the password on the server. When Windows attempts to connect again it should prompt for credentials.

---

### Post by memeri on 2010-06-12
Thanks you guys.

srivo, libpam-smbpass is installed and working.  Morbius1, mark has an account with the same password on both computers, but the windows computer knows nothing about mary, it shouldn't be granted access to her account. Changing the samba password didn't help either.

Still wondering.

---

### Post by CharlesA on 2010-06-12
testparm would show any problems with the smb.conf, wouldn't it?

Is the mark user allowed to access the mary user's home dir via being added to that group?

---

### Post by srivo on 2010-06-13
I'm testing that with my wife laptop and it didn't succeeded yet! I try to force is user account in typing [\\server_name\account_name]("file://\\server_name\account_name") in windows explorer. The good thing is that it asked me for a credential! I enter user account and password but the system tell me that the user is not allowed!
:confused:

---

### Post by memeri on 2010-06-14
Morbius1, you were right. I hadn't changed my password, as I thought I had, mark has permissions to access mary's forlder, and my user name and passwd are the same on ubuntu and win7. So I've got it working now. Thanks a million.

---

