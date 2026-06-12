---
title: "Samba: Random disconnects"
date: 2011-03-06
forum: Server Platforms
---

### Post by mapsegarra on 2011-03-06
Hi all,

After searching, digging and testing I have no more ideas to try. I explain:

 I'm trying to setup a small local File Server (Ubuntu Server 10.04 and  Samba 3.4.7) After looking at the forums about the configurations of  Samba and Windows I managed to get all the network running at 99%. The  remaining 1% is that the connection to Samba from Windows 7 is performed  intermittently.

 XP pcs have no problem accessing, mount drives, read and write to the  Samba server. It seemed that Windows 7, after edit various, either. But  after a few minutes (sometimes seconds) Windows 7 is no access to the  server more, and after a few minutes reconnects.

 The access is done with user authentication and permissions are handled in Ubuntu

 I record somo traffic with Wireshark, but I'm not have enogh level to draw conclusions. If it is necessary I can post too.

 Best Regards!

 Ubuntu Server 4.10 + Samba:  185.0.200.151
 PC Windows 7                         185.0.200.56
[B]
smb.conf[/B]
```

[global]
    workgroup = NPG
    server string = SERV-FICHEROS
    netbios name = SERV-FICHEROS
    wins support = no
    dns proxy = no
    name resolve order = lmhosts host wins bcast
    interfaces = 127.0.0.0/8 eth0
;    bind interfaces only = yes
    deadtime = 0

    printcap name = /dev/null
    load printers = no
    printcap cache time = 0
    show add printer wizard = no
#### Win7 Support ####
    client ntlmv2 auth = yes    
    client lanman auth = yes
    lanman auth = yes
    ntlm auth = yes

#### Debugging/Accounting ####
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
####### Authentication #######
    security = user
    encrypt passwords = yes
    passdb backend = tdbsam
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user

############ Misc ############
#    SO_RCVBUF=8192 SO_SNDBUF=8192
    socket options = TCP_NODELAY

# Maximum number of usershare. 0 (default) means that usershare is disabled.
    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

############ Shares ############
[FICHEROS-NPG]
    path = /FICHEROS-NPG
    comment = Servidor Ficheros
    hide unreadable = yes
    read only = no
    browseable = yes
#    guest ok = yes
#    create mask = 0775
#    directory mask = 077

```**pc win7 (samba log)**

```

  ixd_miguel (185.0.200.56) connect to service FICHEROS-NPG initially as user Manuel (uid=1007, gid=1011) (pid 2180)
[2011/03/01 11:26:30,  1] smbd/service.c:1063(make_connection_snum)
  ixd_miguel (185.0.200.56) connect to service FICHEROS-NPG initially as user Manuel (uid=1007, gid=1011) (pid 2185)
[2011/03/01 11:26:42,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 11:26:42,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 11:26:42,  1] smbd/service.c:1240(close_cnum)
  ixd_miguel (185.0.200.56) closed connection to service FICHEROS-NPG
[2011/03/01 11:29:22,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 11:29:22,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 11:29:22,  1] smbd/service.c:1240(close_cnum)
  ixd_miguel (185.0.200.56) closed connection to service FICHEROS-NPG
[2011/03/01 11:31:30,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 11:31:30,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 11:31:30,  1] smbd/service.c:1240(close_cnum)
  ixd_miguel (185.0.200.56) closed connection to service FICHEROS-NPG
[2011/03/01 12:08:35,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 12:08:35,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 12:41:22,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 12:41:22,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

```

---

### Post by headvampyre@hotmail.co.uk on 2011-03-06
Im going to point out that the parameter:

deadtime = 0

would mean the server disconnects instantly. You should really set this to something like 15, or whatever suits your environment.

---

### Post by mapsegarra on 2011-03-06
> **headvampyre@hotmail.co.uk said:**
> Im going to point out that the parameter:

deadtime = 0

would mean the server disconnects instantly. You should really set this to something like 15, or whatever suits your environment.


Hi & Thanks for your comment,

I think "deadtime = 0" value is the default option to avoid auto-disconnections.

From the Samba man pages:
```

The value of the parameter (a decimal integer) represents the number of minutes of inactivity before a connection is considered dead, and it is disconnected. The deadtime only takes effect if the number of open files is zero.
This is useful to stop a server's resources being exhausted by a large number of inactive connections.
Most clients have an auto-reconnect feature when a connection is broken so in most cases this parameter should be transparent to users.
Using this parameter with a timeout of a few minutes is recommended for most systems.
A deadtime of zero indicates that no auto-disconnection should be performed.

Default: *[I]deadtime* = 0 [/I] 
Example: *[I]deadtime* = 15 [/I] 

```Anyway I will try to set it in 15. I will post too some of the traffic captured by Wireshark.


Results:

```

deadtime=15 
Result: NOK

```Thanks

---

### Post by gobbledigook on 2011-07-23
did this work for you? i'm having the same issue...

---

### Post by headvampyre@hotmail.co.uk on 2011-07-23
I always remembered that parameter meaning auto, most likely my Windows background D= Just a thought, have you enabled port 135 through the firewalls on both the clients and the server?

---

