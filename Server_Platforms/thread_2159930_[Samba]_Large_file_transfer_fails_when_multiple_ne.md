---
title: "[Samba] Large file transfer fails when multiple network drives are set"
date: 2013-07-05
forum: Server Platforms
---

### Post by Katakana2 on 2013-07-05
Hi all, 
[FONT=-moz-fixed] 
I have the following problem which haunted me for a very long time, and  I did not found an solution for as long as I searched (no answer yet on samba mail lists...): 
Laptop: 
- Windows 8 Pro 64bit (happened also on Windows 7 Home Edition 64 bit) 
- 5 network drives are set up in this computer: 4 drives are guest  accesible and one is accessible using specific user and password  (retained by Windows) 
Server 1: Ubuntu Server 13.04, with Samba 3.6.9 with smb.conf file added  below, in a 192.168.72.0/24 LAN 
Server 2: Ubuntu Server 9.10, with Samba 3.4.0 with smb.conf file added  below, in a 192.168.1.0/24 LAN 
When accessing Server 1, Server 2 is not accessible and vice-versa  (different locations). 
When I try to copy large files (1-10 GB) from Laptop to Server 1, at  some intervals the transfer fails, with the message "Network error.  There is a problem accessing Z:\ Make sure that you're connected to the  network and try again.". 
The specific interesting section from the samba log is below. 

[2013/07/02 20:45:53.854564,  2] smbd/open.c:704(open_file) 
  nobody opened file xxx.mkv read=Yes write=Yes (numopen=3) 
[2013/07/02 20:45:57.915958,  2] smbd/close.c:696(close_normal_file) 
  nobody closed file desktop.ini (numopen=2) NT_STATUS_OK 
[2013/07/02 20:52:57.083125,  1] smbd/service.c:1114(make_connection_snum) 
  vr-pc (192.168.72.102) connect to service games initially as user  nobody (uid=65534, gid=65534) (pid 4580) 
[2013/07/02 20:52:57.086980,  1] smbd/service.c:1114(make_connection_snum) 
  vr-pc (192.168.72.102) connect to service diverse initially as user  nobody (uid=65534, gid=65534) (pid 4580) 
[2013/07/02 20:55:06.485696,  2] auth/auth.c:319(check_ntlm_password) 
  check_ntlm_password:  Authentication for user [VR] -> [VR] FAILED  with error NT_STATUS_NO_SUCH_USER 
--------------at this point the transfer fails on the  desktop------------------ 
[2013/07/02 20:55:10.611281,  1] smbd/service.c:1114(make_connection_snum) 
  vr-pc (192.168.72.102) connect to service P-Z initially as user  nobody (uid=65534, gid=65534) (pid 5842) 
[2013/07/02 20:55:10.614556,  1] smbd/service.c:1114(make_connection_snum) 
  vr-pc (192.168.72.102) connect to service 1-O initially as user  nobody (uid=65534, gid=65534) (pid 5842) 
------------------------------------------------------------------------------------------------------------------------------- 
I believe that my laptop tries to authenticate with the username set for  the share which is on Server 2, obviously not present on Server 1, and  when that authentication fails, Samba on Server1 resets all ongoing transfers. 
Now, this problem was not present when both servers were running same  Samba version, it only appeared when I installed Ubuntu 10.04 LTS on  Server 1. The problem stayed on a fresh install 
of Ubuntu 13.04. Please forgive me that I don't write the specific Samba  versions, but I think you understand the fundamental issue. 
Because that this problem was not present on older Samba version, and  because it doesn't seem logical it seems that this is a bug. However, if  anyone of you who has more knowledge about this specific issue knows  more, I would be happy to listen. 

Note: you may see some deprecated options in the smb.confs' below, is  because I tried some other fixes from internet just to be sure. 

Server 1 smb.conf file: 
------------------------------------------------------------------------------------------------------------------------------- 
[global] 
    log file = /var/log/samba/log.%m 
    read raw = no 
    write raw = no 
    passwd chat = [B]*Enter\snew\s*\spassword:* %n\n  [B]*Retype\snew\s*\spassword:* %n\n [B]*password\supdated\ssuccessfully* . 
    socket options = TCP_NODELAY 
    obey pam restrictions = yes 
    null passwords = yes 
    interfaces = 192.168.72.200/255.255.255.0 
    map to guest = bad user 
    encrypt passwords = true 
    winbind trusted domains only = yes 
    winbind use default domain = yes 
    passdb backend = tdbsam 
    passwd program = /usr/bin/passwd %u 
    wins support = true 
    dns proxy = no 
    server string = %h server (Samba, Ubuntu) 
    unix password sync = yes 
    workgroup = INFORM 
    os level = 20 
    debug level = 2 
    socket address = 192.168.72.200 
    syslog = 0 
    preferred master = yes 
    panic action = /usr/share/samba/panic-action %d 
    usershare allow guests = yes 
    max log size = 1000 
    pam password change = yes 


[printers] 
   comment = All Printers 
   browseable = no 
   path = /var/spool/samba 
   printable = yes 
   guest ok = no 
   read only = yes 
   create mask = 0700 

[print$] 
   comment = Printer Drivers 
   path = /var/lib/samba/printers 
   browseable = yes 
   read only = yes 
   guest ok = no 


[P-Z] 
    hide dot files = no 
    writeable = yes 
    public = yes 
    create mode = 775 
    path = /mnt/movies1 
    directory mode = 775 
        guest ok = yes 



[games] 
    writeable = yes 
    path = /mnt/diverse 
    guest ok = yes 
    hide dot files = no 
    create mode = 775 
    public = yes 
    directory mode = 775 

[1-O] 
    writeable = yes 
    delete readonly = yes 
    path = /mnt/movies2 
    hide dot files = no 
    create mode = 775 
    public = yes 
    directory mode = 775 
guest ok = yes 

[diverse] 
    writeable = yes 
    public = yes 
    path = /mnt/diverse2tb 
------------------------------------------------------------------------------------------------------------------------------- 





Server 2 smb.conf file: 
------------------------------------------------------------------------------------------------------------------------------- 

[global] 
    log file = /var/log/samba/log.%m 
    passwd chat = [B]*Enter\snew\s*\spassword:* %n\n  [B]*Retype\snew\s*\spassword:* %n\n [B]*password\supdated\ssuccessfully* . 
    hide unreadable = yes 
    obey pam restrictions = yes 
    interfaces = eth0 
    map to guest = bad user 
    encrypt passwords = true 
    veto files = /.??*/ 
    passwd program = /usr/bin/passwd %u 
    passdb backend = tdbsam 
    wins support = true 
    dns proxy = no 
    netbios name = server 
    server string = 
    remote announce = 192.168.1.255 
    workgroup = INFORM 
    os level = 20 
    security = user 
    syslog = 0 
    panic action = /usr/share/samba/panic-action %d 
    usershare allow guests = yes 
    max log size = 1000 
    bind interfaces only = yes 
    pam password change = yes 

[work] 
    delete readonly = yes 
    writeable = yes 
    path = /media/hdd1tb/work 
    revalidate = yes 
    valid users = removed user names 
    create mode = 775 
    allow hosts = 192.168.1., 127.,192.168.22. 
    directory mode = 775 
------------------------------------------------------------------------------------------------------------------------------- 

[/B][/B][/B][/B][/B][/B][/FONT]

---

