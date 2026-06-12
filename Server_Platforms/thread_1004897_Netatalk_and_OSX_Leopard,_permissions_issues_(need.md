---
title: "Netatalk and OSX Leopard, permissions issues (need a Mac person for this one)"
date: 2008-12-07
forum: Server Platforms
---

### Post by samosamo on 2008-12-07
I am not sure if this is a Netatalk issue, or a Leopard issue, so I posted it on Apple discussion forums also.

Basically, when copying files from an AFP server, Leopard is not having the file inherit the permissions of the parent folder. It is inheriting the permissions of the file within /Volumes.

I am accessing an AFP share point on a server that has files that are 644 (readable by everyone, but only writable by the owner). I am not the owner. When viewing the AFP volume on my client within /Volumes/whatever the permissions appear to be 400 (unwriteable by the owner, no access to anyone else). When I copy the file over to desktop, the permissions remain as 400 when they should obviously be 600.

What does this mean? Even though I am NOW the owner, and it is on MY desktop, I am unable to write to the file unless I chmod it. Very, very annoying and this behavior is unique to Leopard. Tiger does not mangle the permissions.

The server is ubuntu-8.10-server running Netatalk.
The test clients are Leopard 10.5.5 and Tiger 10.4.11

On the server:

> $ pwd
/srv/www

$ ls -l
-rw-r--r-- 1 www-data www-data 1024 2008-11-23 23:29 test.doc

On the Leopard client:

> $ pwd
/Volumes/www

$ ls -l
-r-x------@ 1 sauce staff 1024 Nov 23 23:29 test.doc

$ cp test.doc ~/Desktop

$ ls -l ~/Desktop/test.doc
-r-x------@ 1 sauce staff 1024 Dec 7 00:21 /Users/sauce/Desktop/test.doc

Relevant config lines:
> $ cat /etc/netatalk/AppleVolumes.default | grep www
/srv/www "www" cnidscheme:cdb

$ cat /etc/netatalk/afpd.conf
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh -icon

$


---

### Post by samosamo on 2008-12-09
ttt

---

