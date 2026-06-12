---
title: "Samba stopped working after update"
date: 2014-04-01
forum: Server Platforms
---

### Post by JBtje on 2014-04-01
Hello,

Recently I've updated my Ubuntu fileserver to the latest kernel and removed all older ones (/boot dir was 100% used). Now however, samba does allow me to browse, yet not to open/download files. I've encountered many errors and tried to fix them. Currently I don't see any useful errors anymore, while the problem still exists.

The server functions as some sort of proxy, i.e. I have two servers, one with a 2TB disk and its own sabma setup (this server works excellent) and a second small server (512MB ram, 1GB disk, 1cpu) that uses the 2TB disk via NFS and does allow exploring, but not downloading...

The server is running Ubuntu 10.0404 LTS, kernel 2.6.32-56-server

The NFS disk is mounted via:
mount -t nfs -o rw,defaults,nfsvers=3 xxx.xxx.xxx.xxx:/media/Data/someName /media/someName

Using command line, I can easily open any file on the mounted NFS disk, from which I conclude that the mount should not be the problem.

The configuration file /etc/samba/smb.conf:
```

[global]
        workgroup = someName
        server string = someName Fileserver
        update encrypted = Yes
        allow trusted domains = No
        username map = /etc/samba/smbusers
        log file = /var/log/samba/log.%m
        max log size = 50
        dns proxy = No
        create mask = 2664
        force create mode = 2664
        directory mask = 2775
        force directory mode = 2775
        case sensitive = No
        access based share enum = Yes
[A - Algemeen]
        comment = A - Algemeen
        path = /media/someName/A-Algemeen
        valid users = user1, user2
        read only = No

```
The users shown "exist" and logging in from a windows machine to the server does work (for all users).

I found quite some errors like thisone:
posix_fcntl_getlock: WARNING: lock request at offset 655360, length 61440 returned
for which I added
        ```
posix locking = no
```
to the global region of the config
        
Another frequently occurring error is:
write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
for which I added (not sure if it is correct)
```
smb ports = 445
```

Taking a look at the last edited log file, it contains this:
```

[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  Error writing 39 bytes to client. -1. (Transport endpoint is not connected)
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  Error writing 39 bytes to client. -1. (Transport endpoint is not connected)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2014/04/01 14:51:51,  1] smbd/service.c:1240(close_cnum)
  utwks03843 (::ffff:130.89.155.213) closed connection to service B - Bestuur
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2014/04/01 14:51:51,  1] smbd/service.c:1240(close_cnum)
  utwks03843 (::ffff:130.89.155.213) closed connection to service B - Bestuur
[2014/04/01 14:51:51,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2014/04/01 14:51:51,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
  Error writing 39 bytes to client. -1. (Transport endpoint is not connected)
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2014/04/01 14:51:51,  0] lib/util_sock.c:743(write_data)
[2014/04/01 14:51:51,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2014/04/01 14:51:51,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2014/04/01 14:51:51,  1] smbd/service.c:1240(close_cnum)
  utwks03843 (::ffff:130.89.155.213) closed connection to service B - Bestuur
[2014/04/01 14:54:01,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2014/04/01 14:54:01,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused

```

I am quite certain that the user rights of the files are correct, since this has worked for the past year.
so... what to do to solve the problem, and allow reading of the files again?

Thanks,
Jeffrey

---

