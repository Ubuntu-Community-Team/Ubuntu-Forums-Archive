---
title: "Issues with Samba and create permissions (again)!"
date: 2009-03-11
forum: Server Platforms
---

### Post by djbon2112 on 2009-03-11
_Background:_ I have a file server at home that contains a RAID array that I want to be completely public, read/write to any user on the network via an account called "samba" (no password), who owns the files on the array. Said files have permissions of 0777. The server is running Debian 5.0 and my primary client is Ubuntu Studio 8.10. Everything is configured as needed on the server (Users, Samba, etc.).

_The issue:_ I can read/write fine from the Windows hosts on my network, but my Ubuntu host doesn't create files correctly. If I create a directory, the correct permissions (full read/write/execute i.e. 0777), however not the correct user, are applied. If I create a file, however, I get both the incorrect user and incorrect permissions. I have tried other options, such as forcing the user ("samba"), removing "guest ok", removing the "force mode" lines, and messing around with the various mask/mode values (changing them to 3777, 0775, etc.), but to no avail. I can end up with less permissions, but never more, and never the correct user ("samba"), which is what I need. 

Any tips or suggestions would be greatly appreciated. This is the third time this has happened, and the last two times (both using Ubuntu Server 8.04 instead of Debian 5.0), a hack solution has worked, however this time those same solutions aren't working, and I'd rather get to the root cause of the issue and fix it rather than just messing around until it works!

```
## /etc/samba/smb.conf

[global]
	socket options = TCP_NODELAY
	server string = %h (Samba)
	workgroup = LAN
	security = share

[raid]
       path = /mnt/raid/public
	comment = Fileserver RAID device

	public = yes
	writeable = yes
	guest ok = yes

	create mask = 0777
          force create mode = 0777
	directory mask = 0777
          force directory mode = 0777
```
```
joshua@W01-Zeus:/mnt/fileserver/test$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/* local filesystems omitted for clarity */
//192.168.0.201/raid	/mnt/fileserver	smbfs	user=samba,password= 	0	0
```

Here's what happens when I try to work with files on the array. 1001 is an alias for "samba". As you can see in the fstab above, I am "logged in" with the user samba.
```
[COLOR="Navy"]joshua@W01-Zeus:/mnt/fileserver$[/COLOR] ls -l
total 0
drwxrwxrwx  2   1001 1001 0 2009-03-11 13:24 test
[COLOR="Navy"]joshua@W01-Zeus:/mnt/fileserver$[/COLOR] cd test
[COLOR="Navy"]joshua@W01-Zeus:/mnt/fileserver/test$[/COLOR] mkdir test1
[COLOR="Navy"]joshua@W01-Zeus:/mnt/fileserver/test$[/COLOR] touch test2
touch: setting times of `test2': Permission denied
[COLOR="Navy"]joshua@W01-Zeus:/mnt/fileserver/test$[/COLOR] touch test3
touch: setting times of `test3': Permission denied
[COLOR="Navy"]joshua@W01-Zeus:/mnt/fileserver/test$[/COLOR] ls -l
total 0
drwxrwxrwx 2 nobody nogroup 0 2009-03-11 13:24 test1
-rw-r--r-- 1 nobody nogroup 0 2009-03-11 13:24 test2
-rw-r--r-- 1 nobody nogroup 0 2009-03-11 13:24 test3
```

---

### Post by bryanl on 2009-03-11
try mounting the share with the nounix option and perhaps the file and directory default permission options. For example 

```

mount.cifs //server/sharename mountpoint -o user=workgroup/user%password,noperm,file_mode=0666,dir_mode=0777,nounix

```

---

### Post by djbon2112 on 2009-03-11
> **bryanl said:**
> try mounting the share with the nounix option and perhaps the file and directory default permission options. For example 

```

mount.cifs //server/sharename mountpoint -o user=workgroup/user%password,noperm,file_mode=0666,dir_mode=0777,nounix

```

Well I'll be! Works perfectly now. Thanks!

---

