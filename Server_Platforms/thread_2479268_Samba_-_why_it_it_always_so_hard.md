---
title: "Samba - why it it always so hard"
date: 2022-09-20
forum: Server Platforms
---

### Post by pook2022 on 2022-09-20
I have a machine I've upgraded from 18.04 running Samba.
I've recently created a new machine and installed 22.04 on it and I tried to replicate the Samba shares.
Everything looks the same, same users, same smb.conf etc.

It looks like it's working but I can't connect to it from a windows machine or from my other Ubuntu machine.

```
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1204146/smbd
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1204146/smbd
tcp6       0      0 :::445                  :::*                    LISTEN      1204146/smbd
tcp6       0      0 :::139                  :::*                    LISTEN      1204146/smbd
udp        0      0 192.168.75.255:137      0.0.0.0:*                           1199100/nmbd
udp        0      0 192.168.75.240:137      0.0.0.0:*                           1199100/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1199100/nmbd
udp        0      0 192.168.75.255:138      0.0.0.0:*                           1199100/nmbd
udp        0      0 192.168.75.240:138      0.0.0.0:*                           1199100/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1199100/nmbd

```
all I get is 
```
smbclient -L new_machine
do_connect: Connection to new_machine failed (Error NT_STATUS_HOST_UNREACHABLE)

root@old_machine:~# ping new_machine
PING new_machine (192.168.75.240) 56(84) bytes of data.
64 bytes from new_machine(192.168.75.240): icmp_seq=1 ttl=64 time=0.451 ms



```and the Windows 10 equivalent, when I try and connect.

I thought it might be an app_armor issue, I don't have the profiles installed though, and I have read some posts about app_armor blocking Samba even when it's in complain.

testparm 
```
root@new_machine:/# testparm
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed


Server role: ROLE_STANDALONE

```

```

root@old_machine:/home# telnet new_machine 445
Trying 192.168.75.240...
telnet: Unable to connect to remote host: No route to host
```


Has anyone been able to get Samba working on a fresh 22.04?

UPDATE:
Changed smb.conf to use the network interface instead of any

```

root@new_machine:/etc/samba# netstat -tulpn | egrep "samba|smbd|nmbd|winbind"
tcp        0      0 192.168.75.240:139      0.0.0.0:*               LISTEN      20861/smbd
tcp        0      0 192.168.75.240:445      0.0.0.0:*               LISTEN      20861/smbd
udp        0      0 192.168.75.255:137      0.0.0.0:*                           20938/nmbd
udp        0      0 192.168.75.240:137      0.0.0.0:*                           20938/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           20938/nmbd
udp        0      0 192.168.75.255:138      0.0.0.0:*                           20938/nmbd
udp        0      0 192.168.75.240:138      0.0.0.0:*                           20938/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           20938/nmbd

```
Still can't connect though
```
root@old_machine:/home# telnet 192.168.75.240 445
Trying 192.168.75.240...
telnet: Unable to connect to remote host: No route to host
```

I installed ufw and opened 445 and 139 but that had no effect so I disabled ufw.

Where is this magic firewall?

-Pook

---

### Post by pook2022 on 2022-09-20
ahh ok, it was firewalld.
Didn't realise it was a thing.
:(

---

### Post by LHammonds on 2022-09-20
firewalld is not installed by default on Ubuntu Server 22.04 LTS.

UFW is a front-end for iptables and both are installed by default.  UFW does not start off as active or add rules on the fly by itself.

Besides Samba changes and configuration options changing (add/remove), Windows also is a moving target and you have to adjust over time such as smb protocols being disabled by default on newer Windows platforms.

LHammonds

---

### Post by pook2022 on 2022-09-23
Maybe Virtualmin installed it.
It's new with Samba/Apache2/Postfix/Dovecot/Webmin/Virtualmin installed.

---

### Post by TheFu on 2022-09-23
firewalld is used on RPM-based systems, not Ubuntu.
Is there anything you'd like to tell us?

Some tools that claim to make things easier, just don't. They muck up the innards and should be avoided. I consider all web-app system management tools to be in that group.  Don't make things harder for yourself. Use the CLI.

---

