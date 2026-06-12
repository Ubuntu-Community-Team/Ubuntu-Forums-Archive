---
title: "Samba - XP roaming profiles"
date: 2008-08-09
forum: Server Platforms
---

### Post by eltodd on 2008-08-09
I'm trying to setup roaming profiles on a workstation on my samba PDC, in smb.conf logon path is set to \\%L\profiles\%U logon drive is set to H:
The workstation is joined to the domain fine, and I can log in as any of my users but they all recieve a "windows cannot locate the server copy of your roaming profile..." error message on logon, 
The share is set up as follows

[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   writable = yes
   default case = lower
   preserve case = no
   case sensitive = no
   hide files = /desktop.ini/ntuser.ini/NTUSER.*/
   write list = @users @root
   csc policy = disable
   create mask = 0600
   directory mask = 0700
   read only = No
   store dos attributes = yes
   printable = no

For now the profiles folder has full readwrite permissions for all users.
The windows users can navigate to the folder in their explorer window fine, and can create files and folders in it, so it appears they have appropriate permissions.
I also made sure that the groups the users are in on the samba server (Domain Admins, Domain Users) are added to the local workstations Administrators and Users groups. Any advice would be appreciated.

---

### Post by Mauler5858 on 2008-08-10
I am having the same problem. 

bump

---

