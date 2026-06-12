---
title: "curlftpfs file permissions problem"
date: 2011-01-09
forum: Server Platforms
---

### Post by pdc124 on 2011-01-09
I can mount a livedrive  ftp store using curlftpfs , but am having problems copying files to the store 

I can initiate the connection. I had to add the user (server2) to the fuse group 

> 
$ curlftpfs -d [ftp://user:pass@ftp.livedrive.com](ftp://user:pass@ftp.livedrive.com) /mnt/livedrive
FUSE library version: 2.8.4
nullpath_ok: 0
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56
INIT: 7.14
flags=0x0000007b
max_readahead=0x00020000
   INIT: 7.12
   flags=0x00000011
   max_readahead=0x00020000
   max_write=0x00020000
   unique: 1, success, outsize: 40

and I  send this file  
> server2@server2:~$ ls -la /tmp/test
-rw-r--r-- 1 server2 server2 20 2011-01-09 18:09 /tmp/test
and i try and send it 

> cp /tmp/test /mnt/livedrive 


and the curlftpfs process ( initiated by user server2 ) cant read the file ( created my server2)
> unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 56
getattr /
   unique: 2, success, outsize: 120
unique: 3, opcode: LOOKUP (1), nodeid: 1, insize: 45
LOOKUP /test
getattr /test
ftpfs: operation ftpfs_getattr failed because No such file or directory
   unique: 3, error: -2 (No such file or directory), outsize: 16
unique: 4, opcode: LOOKUP (1), nodeid: 1, insize: 45
LOOKUP /test
getattr /test
   unique: 4, error: -2 (No such file or directory), outsize: 16
unique: 5, opcode: CREATE (35), nodeid: 1, insize: 61
create flags: 0x80c1 /test 0100644 umask=0022
ftpfs: operation ftpfs_getattr failed because No such file or directory
ftpfs: operation ftpfs_chmod failed because Operation not permitted
   create[149707680] flags: 0x80c1 /test
getattr /test
ftpfs: operation ftpfs_getattr failed because No such file or directory
release[149707680] flags: 0x80c1
   unique: 5, error: -2 (No such file or directory), outsize: 16

if i change the permissions 
> server2@server2:~$ ls -la /tmp/test
-rw-rw-rw- 1 server2 server2 20 2011-01-09 18:09 /tmp/test


I can send it 
> unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 56
getattr /
   unique: 2, success, outsize: 120
unique: 3, opcode: LOOKUP (1), nodeid: 1, insize: 45
LOOKUP /test
getattr /test
   NODEID: 2
   unique: 3, success, outsize: 144
unique: 4, opcode: OPEN (14), nodeid: 2, insize: 48
open flags: 0x8001 /test
   open[142702144] flags: 0x8001 /test
   unique: 4, success, outsize: 32
unique: 5, opcode: SETATTR (4), nodeid: 2, insize: 128
truncate /test 0
getattr /test
   unique: 5, success, outsize: 120
unique: 6, opcode: GETXATTR (22), nodeid: 2, insize: 68
   unique: 6, error: -38 (Function not implemented), outsize: 16
unique: 7, opcode: WRITE (16), nodeid: 2, insize: 100
write[142702144] 20 bytes to 0 flags: 0x8001
   write[142702144] 20 bytes to 0
   unique: 7, success, outsize: 24
unique: 8, opcode: FLUSH (25), nodeid: 2, insize: 64
flush[142702144]
   unique: 8, success, outsize: 16
unique: 9, opcode: RELEASE (18), nodeid: 2, insize: 64
release[142702144] flags: 0x8001
   unique: 9, success, outsize: 16


I don't want to chmod 666 everything i want to send. 
Its a user/group problem i think, but what one ?

---

