---
title: "Samba Shared Folders No Longer Appearing in Network Discovery in Windows 8.1"
date: 2016-03-14
forum: Server Platforms
---

### Post by Patricrawley on 2016-03-14
I have a personal ubuntu server that I use for music and video streaming, and there were folders I would mount to play music and edit tags on my Windows computer so I wouldn't have to duplicate data. It all worked fine then I restarted my computer and I haven't been able to discover the server since. It's still running, I can ssh in and access the apache server and all of the relevant processes. Samba seems to be set up correctly but I can't find it, I can't even directly access the files from the Windows computer if I type in the IP. I have disabled SMB2&3 on the windows computer and reenabled them, nothing changed.

---

### Post by bab1 on 2016-03-14
> **Patricrawley said:**
> I have a personal ubuntu server that I use for music and video streaming, and there were folders I would mount to play music and edit tags on my Windows computer so I wouldn't have to duplicate data. It all worked fine then I restarted my computer and I haven't been able to discover the server since. It's still running, I can ssh in and access the apache server and all of the relevant processes. Samba seems to be set up correctly but I can't find it, I can't even directly access the files from the Windows computer if I type in the IP. I have disabled SMB2&3 on the windows computer and reenabled them, nothing changed.
Post the output you get when you ssh to the Ubuntu server and use this command```
pgrep -l mbd
```

---

### Post by Patricrawley on 2016-03-14
```
3827 nmbd
14670 smbd
14671 smbd
```

---

### Post by bab1 on 2016-03-14
> **Patricrawley said:**
> ```
3827 nmbd
14670 smbd
14671 smbd
```

The server is up.  Let's see if there are shares available to the network.  From the same terminal as before , post the output of this command```
smbtree
```

---

### Post by Patricrawley on 2016-03-15
```
WORKGROUP
        \\MADEYE

```

Correct workgroup and the name of the only other PC currently on the network (the one I'm trying to access the server from)

---

### Post by bab1 on 2016-03-15
> **Patricrawley said:**
> ```
WORKGROUP
        \\MADEYE

```

Correct workgroup and the name of the only other PC currently on the network (the one I'm trying to access the server from)

We need to use a little debug then.  Repeat the command with debug added```
smbtree -d3
```

---

### Post by Patricrawley on 2016-03-15
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface enp0s15 ip=2606:a000:1506:c04a:223:54ff:fee3:8e1c bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp0s15 ip=fd49:6f38:2db3:0:223:54ff:fee3:8e1c bcast= netmask=ffff:ffff:ffff:ffff::
added interface enp0s15 ip=192.168.1.113 bcast=192.168.1.255 netmask=255.255.255.0
Enter rowena's password:
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.126 ( 169.254.164.3 192.168.1.126 )
Connecting to 192.168.1.126 at port 445
Connecting to 192.168.1.126 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x55e8ac9f3f20] mpx_fde[(nil)] fd[9] - disabling
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.126 ( 169.254.164.3 192.168.1.126 )
Connecting to 192.168.1.126 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\MADEYE
resolve_lmhosts: Attempting lmhosts lookup for name MADEYE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MADEYE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MADEYE<0x20>
Connecting to 198.105.254.228 at port 445
Connecting to 198.105.254.228 at port 139
Connecting to 198.105.244.228 at port 445
Connecting to 198.105.244.228 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x55e8aca088d0] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x55e8aca09a50] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x55e8aca0a5d0] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x55e8aca0b060] mpx_fde[(nil)] fd[15] - disabling
```

---

### Post by bab1 on 2016-03-15
It appears that the Samba server NetBIOS name can't be resolved correctly.  I assume this is the host's IP address```
192.168.1.113
```

Let's take a stab at this and see what happens.  Reboot the 2 Samba daemons with these commands```
sudo service smbd restart

sudo service nmbd restart
```

Try again```

smbtree
```

If that doesn't work, I'll need to see the output of these 2 commands```

cat /etc/hosts

cat /etc/samba/smb.conf

```

---

### Post by Patricrawley on 2016-03-15
that worked! the nmbd seemed to do the trick, thank you very much

---

### Post by bab1 on 2016-03-16
> **Patricrawley said:**
> that worked! the nmbd seemed to do the trick, thank you very much
Great.  The nmbd is the name service daemon for Samba.

If this is solved, please mark it as "solved" using the thread tools menu.

---

