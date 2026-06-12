---
title: "Won't Mount????"
date: 2006-05-31
forum: Server Platforms
---

### Post by NeoGreen on 2006-05-31
I have just installed NFS and Samba on to an Ubuntu File server, but here is my problem, I cannot mount the file for my client on to the server.  This the error message I get when I input this command: 

[SIZE="2"]neogreen@ubuntulinux:~$ sudo mount neoserver:/home/neogreen /mnt/private[/SIZE]
 
and this is the error message I get: 
mount: neoserver1:/home/neogreen failed, reson given by server: Permission Denied.

:confused:

---

### Post by Iowan on 2006-06-01
[QUOTE=NeoGreen]neogreen@ubuntulinux:~$ sudo mount [COLOR="Red"]neoserver[/COLOR]:/home/neogreen /mnt/private
 
and this is the error message I get: 
mount: [COLOR="red"]neoserver1[/COLOR]:/home/neogreen failed, reson given by server: Permission Denied.

:confused:[/QUOTE]I presume that's a typo?

---

### Post by NeoGreen on 2006-06-01
yeah, that's a typo.  Do I have to run that mount command on my server also?  Or just on the client.

---

### Post by NeoGreen on 2006-06-07
I tried it again and I still can't get the client to mount on the server.  What am I doing wrong?  What do I have to do to get this file server to work?  Ah ah ah ah ah ah ah!!!  I'll keep trying:confused:

---

### Post by Iowan on 2006-06-08
Mount should only be required on the client - but the server must be set up to share. There is a similar discussion in this thread:
[http://www.ubuntuforums.org/showthread.php?t=186063]("http://www.ubuntuforums.org/showthread.php?t=186063")

---

