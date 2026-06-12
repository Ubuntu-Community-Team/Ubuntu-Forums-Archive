---
title: "Samba stopped working"
date: 2011-03-31
forum: Server Platforms
---

### Post by JBtje on 2011-03-31
A while ago I installer samba, thought after chaning all kind of configurations, I wasn't able to get it to work.
Yesterday I installer webmin (shame on me) and with one user i WAS able to login! Thought creating more users, did not result in them being able to login :|
 
After searching a whole day, I .... it up, and now also the user that did work yesterday, doesn't work anymore.
 
After searching for too many hours, I found out that 
```
Not shown: 996 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
901/tcp  open  samba-swat
2049/tcp open  nfs

```
 
So my question would be:
1) how do i get "samba" to listen to the ports it needs to listen too: 137/445(?)
2) what would u guys say of the config file, cuz I do think theyre are mistakes there too (else the 2nd account would work, i assume)
 
The situation:
Ubuntu server 10 (LTS), webmin installed.
The server must check by itself for the passwords/accounts, there is no LDAP or so.
There also is no Domain on this network and there are no other servers with a domain I care about (there are alot of servers on the network, just nog all are mine. The one i also have is a webserver which works perfectly)
 
Thank you for your time!
Jeffrey
 
Here is the smb config file
```
[global]
 log file = /var/log/samba/log.%m
 load printers = no
 guest account = 
 name resolve order = bcast host lmhosts wins
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 socket options = TCP_NODELAY
 obey pam restrictions = yes
 map to guest = bad user
 encrypt passwords = yes
 passdb backend = tdbsam
 passwd program = /usr/bin/passwd %u
 dns proxy = no
 server string = SOME NAME Fileserver
 writeable = yes
 path = /media/Disk1/
 unix password sync = yes
 revalidate = yes
 workgroup = OURWORKGROUP
 os level = 20
 debug level = 2
 comment = Disk1
 valid users = user1,user2,@group1,@group2
 syslog = 0
 panic action = /usr/share/samba/panic-action %d
 usershare allow guests = no
 max log size = 1000
 pam password change = yes
 log level = 2
 bind interfaces only = no
[Disk1]
 comment = some random name

```

---

