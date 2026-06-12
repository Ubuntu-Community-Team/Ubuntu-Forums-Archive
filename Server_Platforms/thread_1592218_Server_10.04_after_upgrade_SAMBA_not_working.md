---
title: "Server 10.04 after upgrade SAMBA not working"
date: 2010-10-10
forum: Server Platforms
---

### Post by lmicu on 2010-10-10
I had a working server 9.04 on my network and I could access shares via Samba and MacFusion from Windows, ubutu and mac boxes. After the upgrade I can not access shares via Samba, I can ssh in it just fine (no change there) also Macfusion mounts the paths just fine.

Anybody had this problem with the upgrade? It must be samba ...... everything else is working (also I can't access any files from my Ubuntu Laptop running 10.10 Desktop edition)

Here is my smb.conf file:

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = yes
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast

;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   security = share
   encrypt passwords = yes
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
;   pam password change = no
   map to guest = bad user

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g

;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups

;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = yes

[homes]
   comment = Home Directories
   browseable = yes

   read only = no

   create mask = 0700

   directory mask = 0700
   valid users = %S
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @lpadmin

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

#share made by lucian micu on nov 29 2009

[USB Disk]
comment = public folder
path = /media/500/Media
public = yes
writable = no
guest ok = yes

[Music]
comment = public folder
path = /share
public = yes
writable = yes
guest ok = yes

[RemoteDocs]
comment = public folder
path = /share
public = yes
writable = yes
guest ok = yes

follow symlinks = yes
wide links = yes
unix extensions = no

[IPC$]
	hosts allow = 192.168.1.0/225 127.0.0.0/225
	hosts deny = 0.0.0.0/0
	path = /tmp
	csc policy = disable

interfaces = 192.168.1.6 192.168.1.14

---

### Post by sikander3786 on 2010-10-10
Check if smbd and nmbd are running.

```
sudo service smbd status
```

```
sudo service nmbd status
```

If not, you can try to start by replacing status with start from the above commands and post back the error encountered.

---

### Post by lmicu on 2010-10-10
lucian@server:~$ sudo service smbd status

smbd start/running, process 972


lucian@server:~$ sudo service nmbd status

nmbd start/running, process 1390


They are both running.

---

### Post by sikander3786 on 2010-10-10
Ok. When you try to access it from Windows what is the exact error message?

You can ping your Ubuntu box from other PCs? I know sounds dumb if you actually can SSH from them.

And did you try accessing your Ubuntu box by typing //ipaddress in the Run dialogue box on Windows?

---

### Post by lmicu on 2010-10-10
From Windows I can ping it just fine as well as from the other boxes. The SERVER shows up in network neiborhood but when i click on it it says that " bla bla not accessible ... contact your admin and it says at the bottom of the message, Path not found"

Tries to type in the IP and get the same error.

Keep in mind that I can see the server from all the boxes I can't access it from none of them.

---

### Post by sikander3786 on 2010-10-10
Have you enabled firewall on your Ubuntu box? Check if samba is allowed to make connections.

---

### Post by lmicu on 2010-10-10
I can't believe I did not paid attention to this, that was the problem, I disabled the firewall and everything started to work.

I wished after an upgrade not to have to modify the firewall settings, they should have been kept the same, no more upgrade for me for a while.

Thank you very much sikander3786!!

---

### Post by hawk2010 on 2010-10-10
Hey. It is not a good idea to disable the firewall .. do the following to make it safer

137/udp                    ALLOW       clientnetwork
138/udp                    ALLOW       clientnetwork
139/tcp                    ALLOW       clientnetwork
445/tcp                    ALLOW       clientnetwork

this will add more security.

---

### Post by lmicu on 2010-10-10
I know, I only disable it for the testing purposes, now I already open those ports.

This brings me to an older issue and I know I did not checked the firewall, I was trying to get netatalk and avahi going but with no avail. You know by any chance what ports they use?

---

### Post by sikander3786 on 2010-10-10
If you are using ufw, samba is predefined in Lucid.

```
sudo ufw allow samba
```

---

