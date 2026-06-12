---
title: "samba create mask being ignored"
date: 2011-03-24
forum: Server Platforms
---

### Post by tbernard on 2011-03-24
Solved: Sorry, I shouldn't have been so quick on the draw.  I just solved it myself.  I made the assumption that when shares are nested that samba will keep checking permissions down the line.  Instead it appears that permissions for a share are set only when that share is accessed directly.  If you take a different route to the same directory the rules for that share won't be applied.
 
Original post:
I'm running into a weird situation where the create mask, force create mode, et al options are being ignored on one of my shares.
 
I'm using Ubuntu 10.04 with whatever version of Samba is the latest in the repositories. I dont know how to check version numbers with any more accuracy than that but hopefully that's enough info. All of the machines in the office are Windows 7.
 
My directory heirarchy is such. I have one directory called shares, this is the top directory, and the only one that is browsable. This way I can have a single map to [\\MyServer\Shares]("file://\\MyServer\Shares") for all my windows clients, and all the data is below this point. I have a home folder for each user that is visible only to them, and a shared folder that is (supposed to be) compay RWX.
 
The folder [\\MyServer\Shares\Shared]("file://\\MyServer\Shares\Shared") I want to have full permissions for owner and group only. So I set create mask, force create mode, and the other related functions all to 770. This way anyone can do anything to any file in this folder so long as they're an authenticated user, no matter who makes it. However when I create a file in the share from one of my windows 7 clients (all clients are win 7) the file is created with 744 permissions, regardless of what options I have set on the share.
 
Here is my smb.conf
```
 
 
[global]
workgroup = WORKGROUP
netbios name = MyServer
hide unreadable = Yes
 
#This is a stand in for home since the regular home folders were showing at the top of the heirarchy
[%S]
comment = Home Directory
path = /usr/lib/samba/shares/%S
valid users = %S, root
read only = No
browseable = No
 
[Shares]
comment = All Samba handled Data
path = /usr/lib/samba/shares
read only = No
valid users = @workgroup
 
[Shared]
comment = Company Shared Data
path = /usr/lib/samba/shares/shared
read only = No
valid users = @workgroup
browseable = No
 
create mask = 770
force create mode = 770
security mask = 770
force security  mode = 770
 
directory mask = 770
force directory mode = 770
directory security mask = 770
force directory security mode = 770

```
 
My latest thought which I'll test and respond here about, is that perhaps since I've already authenticated into the [Shares] directory, then samba lets the unix permissions take over from there and isn't applying the permissions I set on [Shared] and [%S]. Can anyone confirm or deny this?
 
Does anyone have any idea why the files I create from my guests are ignoring the my mask/mode options?

---

