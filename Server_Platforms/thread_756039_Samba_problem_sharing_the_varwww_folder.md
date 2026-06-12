---
title: "Samba problem: sharing the /var/www folder"
date: 2008-04-15
forum: Server Platforms
---

### Post by cocotu on 2008-04-15
Below is my testparm, we want to share the var/www directory to allow win users to access the folder.  I already try this post: [http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653) but I only get a login window when I try to access the www folder not my home.  When I enter my login name/pass for the www directory nothing happens, it just adds the win computer name: <wincomputer>/rg to the login screen, meaning it does not give me an error message saying that I'm using an incorrect user/pass.  Thanks

[global]
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories

[www]
        comment = var/www
        path = /var/www
        valid users = %S
        force user = rg
        force group = www-users
        read only = No
        create mask = 0771
        directory mask = 0777
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

---

### Post by cdenley on 2008-04-15
I suspect the part in bold is your problem.

```

[global]
server string = %h server (Samba, Ubuntu)
obey pam restrictions = Yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
panic action = /usr/share/samba/panic-action %d
invalid users = root

[homes]
comment = Home Directories

[www]
comment = var/www
path = /var/www
[B]valid users = %S
force user = rg[/B]
force group = www-users
read only = No
create mask = 0771
directory mask = 0777
guest ok = Yes

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers 

```

I don't think the "force user" is unnecessary, and can only create problems. What exactly are you trying to do with "valid users = %S"? I think that would only allow the user "www" to use the share. Instead of those two lines, try
```

valid users = @www-users

```

---

### Post by cocotu on 2008-04-15
that didn't work, still same issue. thanks

---

### Post by cdenley on 2008-04-15
You restarted samba, right?
```

sudo /etc/init.d/samba reload

```

Post this output, replacing "username" with the user you're trying to log in as.
```

sudo pdbedit -u username
groups username
ls -ld /var/www

```

Are you sure you set a samba password for that user?
```

sudo smbpasswd username

```

---

### Post by cocotu on 2008-04-15
1. Yes I restarted samba.
2. sudo pdbedit <username>
rg:1000:Rudy,,,
   groups username
rg : rg adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin www-users
   ls -ld /var/www
drwxrwxrwx 8 771 www-users 4096 2008-04-14 09:32 /var/www

3. Yes, that user has a password

thanks.

---

### Post by cdenley on 2008-04-15
Then I can't help you, because it works correctly for me with all the settings you posted.

```

[global]
server string = %h server (Samba, Ubuntu)
obey pam restrictions = Yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
panic action = /usr/share/samba/panic-action %d
invalid users = root

[homes]
comment = Home Directories

[www]
comment = var/www
path = /var/www
valid users = @www-users
force group = www-users
read only = No
create mask = 0771
directory mask = 0777
guest ok = Yes

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

```

---

### Post by cocotu on 2008-04-15
do you need that **@** before www-users at valid users?  I made the smb.conf file exactly the same as yours.  Could it be a network error?  Does it ask you for user/password when you double click the www folder?

---

### Post by cocotu on 2008-04-15
the problem is that the login window doesn't tell me I don't have access to this folder, it just adds the windows' computer name to the username at the windows login prompt:

user:<WindowsComputername>/rg
pass: ***************

---

### Post by cdenley on 2008-04-16
I think when the user you are connecting to doesn't have samba permission to access a share, it will assume you want to connect as a different user and ask for another username and password. If it were a problem with your unix permissions, then I think it gives you an error.

> 
do you need that @ before www-users at valid users?

Definitely. The @ means it is followed by a group, not a user. The line means that anyone in the www-users group can use the samba share.

> 
Could it be a network error?

I doubt it. You can check the logs /var/log/samba/log.*

> 
Does it ask you for user/password when you double click the www folder?

It asks me for a user/password when I initially connect if the username and/or password on the local computer doesn't match. When I open any of the shares, the user has access, and I'm not prompted for another login.

---

### Post by cocotu on 2008-04-16
this is very strange.  Not sure what to do anymore. thanks cdenley.

---

### Post by cocotu on 2008-04-16
I found this at the logs:
[2008/04/16 11:35:18, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/04/16 11:35:18, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/04/16 11:35:18, 1] smbd/service.c:make_connection_snum(1033)
  cienfuegos (172.27.0.68) connect to service rg initially as user rg (uid=1000, gid=1000) (pid 8921)
[2008/04/16 11:35:29, 1] smbd/service.c:close_cnum(1230)
  cienfuegos (172.27.0.68) closed connection to service rg
[2008/04/16 11:39:29, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/04/16 11:39:29, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

not sure if it means something. thanks

---

### Post by cocotu on 2008-04-17
I found the problem, I had uncomment this section.

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

But now everyone can connect to it without an account. thanks

---

### Post by cocotu on 2008-04-17
It works by just using this:

[var]
        comment = var folder
        path = /var/www
        valid users = @www-users
        read only = No
        guest ok = Yes

Crazy, but it works. thanks

---

