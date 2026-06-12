---
title: "Samba share doesn't work, client is required login"
date: 2011-01-14
forum: Server Platforms
---

### Post by snakebob on 2011-01-14
Hello all gentleman
 
I am using Samba for my homenetwork file server in Ubuntu desktop 10.10
 
A client laptop is in MS windows7 32bit and if I try to access to samba from my laptop, share folder require ID/password.
 
Of course, this login process doesn't work. If I input my samba ID/password, samba keep asking ID/password and never proceeded further.
As a result, I can only read in the samba share folder but no writing anything in the folder
 
Actually, I set up my samba very simply by following
-----------------------------------------------
....(Just some general).....
Security = share
[Folder]
.....
writable = yes
.....
-----------------------------------------------
 
I doubted a lot for Windows 7 because this kind of things never happend before with Windows XP.
 
But, yesterday I found something from Ubuntu.
When I failed to move some file from Windows 7 to Samba in Ubuntu , I found some message from my ubuntu samba right after the failure
 
Please , see below
=============================================
sulnam@DW-NETFRAME:~$ sudo smbstatus
Samba version 3.5.4
PID Username Group Machine
-------------------------------------------------------------------
<processes do not show up in anonymous mode>
Service pid machine Connected at
-------------------------------------------------------
IPC$ 1688 192.168.0.3 Thu Jan 13 23:45:31 2011
SL DISK 1688 192.168.0.3 Thu Jan 13 23:45:31 2011
EFT &#51088;&#47308;&#49892; 1688 192.168.0.3 Thu Jan 13 23:44:31 2011
Locked files:
Pid Uid DenyMode Access R/W Oplock SharePath Name Time
--------------------------------------------------------------------------------------------------
1688 65534 DENY_NONE 0x100081 [COLOR=#ff0000]**RDONLY **[/COLOR]NONE /home/sulnam . Thu Jan 13 23:45:35 2011
sulnam@DW-NETFRAME:~$
=============================================
 
As you can see, Samba say that folder is in "[COLOR=red]**Readonly**[/COLOR]" mode and this is absolutely not true because I set up "Security = share" in /etc/samba/smb.conf
This folder mode is in 755.
 
Anyone can help me for this?
 
Thanks for your kind attention.

---

### Post by SeijiSensei on 2011-01-14
Try adding "guest ok = yes" to the share definition.  You'll need to check "guest account" as well to make sure the guests can write files into the share with proper permissions.  See "man smb.conf" for more details.

---

### Post by snakebob on 2011-01-14
> **SeijiSensei said:**
> Try adding "guest ok = yes" to the share definition. You'll need to check "guest account" as well to make sure the guests can write files into the share with proper permissions. See "man smb.conf" for more details.
 
Wow....perfect.
Now it works...
 
Thanks you

---

### Post by chrislynch8 on 2011-01-14
Do you want to be asked for the username and password? Did you create a samba username and password and did you enable that user so it works?

Rgds
Chris

---

