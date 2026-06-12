---
title: "sudo won't work"
date: 2009-05-21
forum: Server Platforms
---

### Post by andyrowe on 2009-05-21
Hi all:
I just don't seem to be able to not screw this thing up! Running Ubuntu server with samba to serve files to MS AD domain. All was working well. Edited /etc/nsswitch.conf to put winbind in front of files so it would authenticate against winbind first. example line in file:
passwd: winbind files
Now when I try to sudo something on linux box I get incorrect password.
Any help?

---

### Post by andyrowe on 2009-05-22
this is so strange. I can log off and log back on using my username and password, even was able to change my password, but can't sudo. Odd thing is, now my prompt line says [EMAIL="LINUXSERVER+username@LinuxServer:~$"]LINUXSERVER+username@LinuxServer:~$[/EMAIL] when before this happen it said [EMAIL="username@LinuxServer:~$"]username@LinuxServer:~$[/EMAIL] 
Any help would be really appreciated

---

### Post by andyrowe on 2009-05-22
well in case anybody finds this thread, I cured my problem by restarting the machine (yes the brutal way... unplugging it, as I couldn't run the shutdown command without sudo) and dropped into the recover mode during bootup (by pressing the escape key while booting) and then dropped to root shell and fixed the file in question. resumed normal boot and sudo is working again

---

### Post by Iowan on 2009-05-22
I'm used to seeing Winbind activated differently:```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```Glad you found/fixed the problem.

---

