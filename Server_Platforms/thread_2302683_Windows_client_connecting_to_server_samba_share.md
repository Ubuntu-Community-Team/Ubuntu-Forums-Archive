---
title: "Windows client connecting to server samba share"
date: 2015-11-12
forum: Server Platforms
---

### Post by setchp on 2015-11-12
Setup is Ubuntu server 14.04, running samba 4.1.6-ubuntu, windows client (windows 7 pro).

There are over 20 workstations running a variety of windows, connecting successfully to a range of shares on the Ubuntu server.
One client as on first line, works OK until the workstation is shut down and restarted the following morning.
The workstation requests the user/password, but will not work with the correct values.
On the server running smbclient as that user returns NT_STATUS_LOGON_FAILURE.
Removing user via smbpasswd -x, and then adding with smbpasswd -a allows access, until the next reboot.
I could maybe understand a problem with windows forgetting the info, but can't see why the server is rejecting the account each morning.

Appreciate any thoughts.

---

### Post by bab1 on 2015-11-13
> **setchp said:**
> Setup is Ubuntu server 14.04, running samba 4.1.6-ubuntu, windows client (windows 7 pro).

There are over 20 workstations running a variety of windows, connecting successfully to a range of shares on the Ubuntu server.
One client as on first line, works OK until the workstation is shut down and restarted the following morning.
The workstation requests the user/password, but will not work with the correct values.
On the server running smbclient as that user returns NT_STATUS_LOGON_FAILURE.
Removing user via smbpasswd -x, and then adding with smbpasswd -a allows access, until the next reboot.
I could maybe understand a problem with windows forgetting the info, but can't see why the server is rejecting the account each morning.

Appreciate any thoughts.
How do you manage your user accounts?  What is the Samba classification type (standalone or ADS)? Do you sync the Samba password with the Linux user account password?  Some folks use the package libpam-smb to to automatically do the syncing, but you do not strictly need the package for Samba to perform correctly.

---

### Post by setchp on 2015-11-14
Thanks for the reply.

This setup is exactly the same as 18 other schools that we look after. The linux server runs as a workgroup, ie we do not log into a domain (they are mostly small schools). The users are added as linux users, and then added via smbpasswd. This installation is one where we have installed a newer replacement server to take over from an older one which had been running SuSE. All users were added afresh on the new server, only share data was transferred from the older server. The samba server is standalone. We don't synch passwords as we don't allow changes without our involvement. As I said above, this is the first time I've seen this in 15 years of managing servers. Once the pc is rebooted, the fault is on the server. The pc can be powered down, and then smbclient fails to connect until the user has been removed from the smb user list, and re-added again by smbpasswd. If the pc is left off, access via smbclient for that user works fine. Sorry if there isn't enough info to pin this down.

---

### Post by bab1 on 2015-11-15
> **setchp said:**
> Thanks for the reply.

This setup is exactly the same as 18 other schools that we look after. The linux server runs as a workgroup, ie we do not log into a domain (they are mostly small schools). The users are added as linux users, and then added via smbpasswd.

Starting with the PC first booted up (unable to log in) -- Does the user show up in the Samba users database? You can see all the Samba users with this command ```
sudo pdbedit -L
```
>  
This installation is one where we have installed a newer replacement server to take over from an older one which had been running SuSE. 
Are you using Ubunut Server?  How did you install Samba; did you use **tasksel** to do that?> 
All users were added afresh on the new server, only share data was transferred from the older server. The samba server is standalone. We don't synch passwords as we don't allow changes without our involvement.

Is the package libpam-smbpass installed?  Post the output of ```
dpkg -l libpam-smbpass
```
> 
Once the pc is rebooted, the fault is on the server. The pc can be powered down, and then smbclient fails to connect until the user has been removed from the smb user list, and re-added again by smbpasswd. 

If the pc is left off, access via smbclient for that user works fine. Sorry if there isn't enough info to pin this down.
These last two statements do not make sense.  Is the client a Linux host?  Where are you using smbclient from?  Are you saying that you can access the share if the PC in question is off?  Can the user access the share from another machine?

All authentication is done on the server side.  The user in question should be able to access the share from any machine on the network.  Does the symptom occur for this user at a different workstation?

---

