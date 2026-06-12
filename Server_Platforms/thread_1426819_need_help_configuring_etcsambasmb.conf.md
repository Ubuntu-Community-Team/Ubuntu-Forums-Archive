---
title: "need help configuring /etc/samba/smb.conf"
date: 2010-03-10
forum: Server Platforms
---

### Post by Hathadar on 2010-03-10
I am having trouble getting my smb.conf setup correctly.

I am working on a public and a private share.
The private share seems to work fine.
```
[private]
   comment = Private Share
   path = /media/largedrive/privateshare
#   browseable = yes
   read only = no

```
There is some strange behavior here though.  When I enable the browseable = yes, I can no longer see the private share in windows 7.

The public share is showing up but it times out when I try to open it in windows.
```
[public]
   comment = Public Share read-only
   path = /media/largedrive/publicshare
   writable = no
   public = yes
   create mask = 0777
   directory mask = 0777
   guest ok = yes
   force user = nobody
   force group = nogroup
#   browseable = yes
   guest account = nobody

```
I have tried both options for browseable and removing it all together.

Further strange activity.  Upon executing testparm, I get this:
```
[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etcsamba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[private]
        comment = Private Share
        path = /media/largedrive/privateshare
        read only = No

[public]
        comment = Public Share read-only
        path = /media/largedrive/publicshare
        force user = nobody
        force group = nogroup
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

```

note that browseable and browsable show up under printers, even though I have commented browseable out.

---

### Post by Hathadar on 2010-03-10
Also, I found this log file under /var/log/samba
```
  smb_pwd_check_ntlmv1: incorrect password length (84)
[2010/03/10 17:32:05,  0] smbd/service.c:1009(make_connection_snum)
  '/media/largedrive/publicshare' does not exist or permission denied when connecting to [public] Error was Permission denied
[2010/03/10 17:32:05,  0] libsmb/ntlm_check.c:54(smb_pwd_check_ntlmv1)
  smb_pwd_check_ntlmv1: incorrect password length (84)
[2010/03/10 17:32:05,  0] libsmb/ntlm_check.c:54(smb_pwd_check_ntlmv1)
  smb_pwd_check_ntlmv1: incorrect password length (84)
[2010/03/10 17:32:05,  0] libsmb/ntlm_check.c:54(smb_pwd_check_ntlmv1)
  smb_pwd_check_ntlmv1: incorrect password length (84)
[2010/03/10 17:32:06,  0] libsmb/ntlm_check.c:54(smb_pwd_check_ntlmv1)
  smb_pwd_check_ntlmv1: incorrect password length (84)
[2010/03/10 17:32:06,  0] smbd/service.c:1009(make_connection_snum)
  '/media/largedrive/publicshare' does not exist or permission denied when connecting to [public] Error was Permission denied
[2010/03/10 17:32:19,  0] lib/util_sock.c:537(read_socket_with_timeout)
[2010/03/10 17:32:19,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

```

---

### Post by Hathadar on 2010-03-10
[]("http://ubuntuforums.org/showthread.php?t=163882")Ok, the log file gave me the idea that it wasnt the config file but rather the file permissions for the folder.
I tried using sudo chmod to change the permissions.  The command would run without complaint but no changed would take effect.

After some searching, I found [this thread]("http://ubuntuforums.org/showthread.php?t=163882") which suggested changing the umask for my fat32 drive to 0000.
After reboot, I found it changed all permissions for all files on the drive to rwxrwxrwx.  sudo chmod sill will not change file permissions.

How can I get chmod to work?

---

