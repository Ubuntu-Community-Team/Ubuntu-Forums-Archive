---
title: "Samba free space issue, dfree command not working"
date: 2016-12-28
forum: Server Platforms
---

### Post by aalexis78 on 2016-12-28
I have a Samba server running Ubuntu 16.04.1 serving some btrfs subvolumes. These subvolumes have btrfs quotas set through btrfs qgroup.
  In order to reflect the quota to the clients, I want to use a custom dfree command.

  My problem is that Samba seems to never call my dfree command, and just shows the btrfs filesystem's available free space.
  ```
username@NAS:~$ smbd --version
Version 4.3.11-Ubuntu
```
  My smb.conf:

  ```
[global]
max log size = 1000
usershare allow guests = yes
dns proxy = no
pam password change = yes
workgroup = WORKGROUP
map to guest = bad user
obey pam restrictions = yes
server role = standalone server
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
passwd program = /usr/bin/passwd %u
passdb backend = tdbsam
encrypt passwords = yes
server string = %h server (Samba, Ubuntu)
panic action = /usr/share/samba/panic-action %d
log file = /var/log/samba/log.%m
log level = 10
syslog = 0
dfree cache time = 0

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

[username_backup]
path = /backup_tank/username
browsable = yes
force group = username
directory mode = 750
force user = username
guest ok = no
valid users = username
create mode = 650
writable = yes
security = user
**dfree command = /usr/local/bin/df_btrfs**

```  
My script in /usr/local/bin/df_btrfs (owner root:root and 700 rights):  
  ```
#!/bin/bash

STR=$(/bin/btrfs qgroup show -rF --raw /backup_tank/username/ | /usr/bin/tail -1)

SIZE=$(/usr/bin/expr `/bin/echo $STR | /usr/bin/cut -d \  -f 4` / 1024)
USED=$(/usr/bin/expr `/bin/echo $STR | /usr/bin/cut -d \  -f 2` / 1024)
AVAIL=$(/usr/bin/expr $SIZE - $USED)

/bin/echo $SIZE $AVAIL
```
  When I run this script (as root because of the btrfs command), it gives me the right numbers, in the format expected by Samba:
  ```
username@NAS:~$ sudo /usr/local/bin/df_btrfs
734003200 196187016
```
  What I've tried unsuccessfully (samba keeps giving me the same numbers, logs show no error or sign of the script being run):

[LIST]
[*]```
chmod 777 /usr/local/bin/df_btrfs
``` 
[/LIST]
 
[LIST]
[*]Replace the /usr/local/bin/df_btrfs content with:
   ```
#!/bin/bash
/bin/echo "734003200 196187016"
``` 
[*]Replace the dfree command setting with
  ```
dfree command = 734003200 196187016
``` 
[*]Replace the dfree command setting with a non existing file path
  ```
dfree command = /usr/local/bin/df_btrfs_nonexistant  
```
  (still no error in the logs even though this file doesn't exist) 
[/LIST]


[LIST]
[*]Trying the things above with dfree command in **[global]** 
[/LIST]
  I restarted the smbd service between each try, and then even the server and client machines.
  The only sign of the dfree command or /usr/local/bin/df_btrfs in smbd's logs are:
  ```
[2016/12/27 12:16:52.059912,  5, pid=23203, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:1325(free_param_opts)
doing parameter dfree command = /usr/local/bin/df_btrfs
doing parameter dfree cache time = 0
```

---

