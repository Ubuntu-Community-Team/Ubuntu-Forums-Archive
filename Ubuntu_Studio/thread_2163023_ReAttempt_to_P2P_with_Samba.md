---
title: "ReAttempt to P2P with Samba"
date: 2013-07-16
forum: Ubuntu Studio
---

### Post by hbnmgr on 2013-07-16
I used to be able to connect to my WinXP PC using Samba under Ubuntu Studio. After several updates, it seems no longer installed.
Here is my output in terminal;
```

stephen@Linus2us:~$ sudo /etc/init.d/samba stop
[sudo] password for stephen: 
sudo: /etc/init.d/samba: command not found
stephen@Linus2us:~$ sudo /etc/samba stop
sudo: /etc/samba: command not found
stephen@Linus2us:~$ sudo /etc/init.d/samba stop
sudo: /etc/init.d/samba: command not found
stephen@Linus2us:~$ samba stop
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4
You will have to enable the component called 'universe'
stephen@Linus2us:~$ net usershare info --long
stephen@Linus2us:~$ smbtree
Enter stephen's password: 
HBNET
    \\MAINSYS                
stephen@Linus2us:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "null passwords" option is deprecated
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = HBNET
    netbios name = MAINSYS
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    idmap config * : backend = tdb

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    print ok = Yes
    browseable = No

[MyFiles]
    path = /home/samba/
    force user = stephen
    force group = stephen
    read only = No
    create mask = 0644
stephen@Linus2us:~$ sudo apt-get install samba4
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'samba4' has no installation candidate
stephen@Linus2us:~$ 


```

How do we now connect to a WinXP machine on a local network? I connect through a router from PC to PC. The Router is connected to Modem/Net.
Is there another Tuturorial besides the one I followed which apparently is now outdated?

ANY help is appreciated.
Thanks!
hbnmgr

---

