---
title: "Samba access problems with group users"
date: 2008-01-24
forum: Server Platforms
---

### Post by Nonney on 2008-01-24
I have spent too many hours on this and can't find anything in the forums to help, so would be really grateful for some help.

I am running Ubuntu server 7.10 with all latest updates applied.

I followed the HowTo at:

[http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend]("http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend")

several times to tryto set up my server to share files with the rest of the office, also LAMP server too for web dev.

Here is my smb.conf - some sections omitted:

[global]
workgroup = VIVACE
server string = %h server (Samba, Ubuntu)
obey pam restrictions = Yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
security = user
; username map = /etc/samba/smbusers
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
panic action = /usr/share/samba/panic-action %d
invalid users = root

[homes]
comment = Home Directories
path = /var/samba/shares/homes/%u
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = No

[allusers]
comment = All Users
path = /home/shares/allusers
valid users = nigel
; force group = users
create mask = 0660
directory mask = 0771
writable = yes

I can access home directory OK using user nigel.

I am having problems with allusers. I can access with smb.conf set as above with valid user = nigel, but if I enable force group = users I cannot access the share. Also if I set valid users = @users I cannot access the share either.

getent group | grep users returns

root@vslserver:~# getent group | grep users
users:x:100:nigel
root@vslserver:~#

confirming nigel is in the group users

permissions on the /home/shares/allusers were set as per the HowTo and users added in the same way too.

In the interest of a server remaining in a nice warm office and not out in the rain, I would be really grateful for some assistance.

I have posted this at the Howto Forge forums but no feedback.

Thanks in advance for advice.

---

### Post by cdenley on 2008-01-24
I have a similar share on my gutsy samba PDC, and it works fine.

```

[share]
   path = /samba/share
   guest ok = no
   browseable = yes
   writeable = yes
   create mask = 0660
   directory mask = 0770
   valid users = user1 user2 @ntadmins
   force group = ntusers

```

My admin account is also a member of ntusers. I am able to access it, and files I create have a group ownership of ntusers. Are you sure the permissions are set correctly? When you mentioned /home/share/allusers, I assume that was a typo. Could you post the output of "ls -ld /home /home/shares /home/shares/allusers"?

---

### Post by Nonney on 2008-01-24
Hi

Yes, well spotted the share should be shares.

Here is the output you asked for.

root@vslserver:/home# ls -ld /home /home/shares /home/shares/allusers
drwxr-xr-x 5 root root  4096 2008-01-24 14:20 /home
drwxr-xr-x 3 root root  4096 2008-01-23 18:34 /home/shares
drwxrwxr-x 2 root users 4096 2008-01-23 19:20 /home/shares/allusers
root@vslserver:/home#

BTW - I am running Samba 3.0.26a, I see on the Samba site there is a later release but not available via Ubuntu updates.

Also I have spent several hours googling and forum hunting and this seems to be a common problem.

---

### Post by cdenley on 2008-01-24
I tried the same setup as yours, and it works, so I'm out of ideas. What OS are you trying to connect from?

See if you can find a relevant difference between our global settings. I didn't notice any.
```

[global]
   netbios name = ubuntu
   store dos attributes = yes
   hide files = /desktop.ini/Desktop.ini/Thumbs.db/
   workgroup = MYDOMAIN
   server string = MYDOMAIN
   time server = no
   wins support = no
   dns proxy = no
   interfaces = 192.168.0.0/24 eth1
   smb ports = 139
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true 
   passdb backend = tdbsam
   obey pam restrictions = yes
   domain logons = yes
   logon path = \\%N\profiles\%U
   logon drive = H:
   logon home = \\%N\%U
   logon script = logon.cmd
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/groupmod -A %u %g
   delete user from group script = /usr/sbin/groupmod -R %u %g
   add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
   socket options = TCP_NODELAY
   os level = 35
   preferred master = Yes
   domain master = Yes
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   winbind enum users = yes
   winbind enum groups = yes

[allusers]
   comment = All Users
   path = /home/shares/allusers
   valid users = nigel
   force group = users
   create mask = 0660
   directory mask = 0771
   writable = yes

```

Same user setup
```

cdenley@www:~$ cat /etc/passwd|grep nigel
nigel:x:1001:1004:,,,:/home/nigel:/bin/bash
cdenley@www:~$ cat /etc/group|grep nigel
users:x:100:nigel
nigel:x:1004:

```

```

cdenley@www:~$ ls -ld /home /home/shares /home/shares/allusers
drwxr-xr-x 48 root root  4096 2008-01-24 09:07 /home
drwxr-xr-x  3 root root  4096 2008-01-24 09:07 /home/shares
drwxrwxr-x  3 root users 4096 2008-01-24 09:12 /home/shares/allusers

```

I don't think this is a problem with the version of samba you are running. I'm running the same version.

```

cdenley@www:~$ sudo dpkg -l|grep samba
ii  samba                                      3.0.26a-1ubuntu2.3       a LanManager-like file and printer server fo
ii  samba-common                               3.0.26a-1ubuntu2.3       Samba common files used by both the server a
```

---

### Post by Nonney on 2008-01-25
Hi cdenley

Thanks for all your help - I tried something different having read your previous post - I set up another group "samba", added the users to it and accessed the share OK.

Then tried the force group and couldn't access. Then retyped the force group on a new line and deleted the old - all OK now.

Then retried with "users" and all errored again.

Don't know why, maybe there is something odd about by "users" group; I don't intend to waste any more time trying to get it working with "users".

So once again many thanks for all your diligent support.

---

### Post by jonabyte on 2008-01-25
I use valid users for all users that need access to the drive, then I will group them and use permissions on folders that they need within the drive itself. HTH

---

### Post by ej00 on 2008-01-25
I was having the exact problem as you. My solution was to delete all of the entries (for my share) except the following from my smb.conf file note that I used admin users not valid users. I am very new to Linux so I am not sure wat the difference is. I just know it worked for me. Also, I am using my system as a file server at home so I am not so worried about security.

[SHARE]
path = /home/server/Desktop/Share/
guest ok = yes
read only = no
admin users = server,users

---

