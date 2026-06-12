---
title: "[SOLVED] &amp;quot;View Computers&amp;quot; sees nothing, not even itself"
date: 2008-04-03
forum: Windows
---

### Post by jay019 on 2008-04-03
Hi all,

I have a windows xp (sp2) machine and a ubuntu laptop. From the ubuntu laptop I can grab shared files from the windows machine from within nautilus. Just discovered that smb://IP.OF.MACH.INE works faster, so no problems from the ubuntu side.

However, from windows, using the "View Workgroup" doesnt see any computers, not even the machine its running on. This is weird as I know that file sharing is on and works cause I can get to files from ubuntu, but have no idea how to see my laptop from the windows machine.

Anyone have any clues?

Cheers.

Jay

---

### Post by njparton on 2008-04-03
Do you have samba and smbfs installed and running in ubuntu?
 
Can you post your smb.conf file please?

---

### Post by jay019 on 2008-04-03
```


[global]
   workgroup = HOMENET
   server string = "Laptop"
   netbios name = Laptop019
   wins support = yes
   dns proxy = no
   name resolve order = host wins bcast lmhosts

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true



#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

;   security = user
   encrypt passwords = yes
   passdb backend = tdbsam
   obey pam restrictions = yes
   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
;   pam password change = no

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   valid users = %S
;   writable = no
;   create mask = 0600
;   directory mask = 0700

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

#[printers]
#   comment = All Printers
#   browseable = no
#   path = /var/spool/samba
#   printable = yes
#   public = no
#   writable = no
#   create mode = 0700

#[print$]
#   comment = Printer Drivers
#   path = /var/lib/samba/printers
#   browseable = yes
#   read only = yes
#   guest ok = no

;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[RouterDocs]
path = /home/jay019/Desktop/RouterDocs
available = yes
browsable = yes
public = yes
; writable = no
; valid users = jay019, guest


```


I have also just noticed that typing \\192.168.1.9 in the explorer address bar shows the windows shares, but trying \\192.168.1.19 still doesnt show the ubuntu shares.

---

### Post by njparton on 2008-04-03
is you windows workgroup set to HOMENET too?

---

### Post by njparton on 2008-04-03
also, you windows username must = your ubuntu username and you need to run ```
smbpasswd -a
``` to add a samba password in addition to your ubuntu password.

---

### Post by jay019 on 2008-04-03
The windows box has the same workgroup name and the windows username/pass has been added to ubuntu. Also, typing \\192.168.1.19 in the explorer address bar gives me the following message...

'Windows cannot find '\\192.168.1.19'. Yada, yada.'

Which is weird cause I am currently using this machine (XP) via VNC from my laptop (ubuntu)
I can also ping ubuntu from windows.

---

### Post by njparton on 2008-04-03
Maybe you have the samba ports blocked in iptables?
 
Also if you're connecting via a router you may need to forward those ports too.
 
These are long shots though if VNC is working.
 
Check your windows firewall (or zonealarm or whatever you use) to make sure the necessary file sharing services/ports aren't blocked for some reason.

---

### Post by jay019 on 2008-04-04
I've checked the firewall and I dont think that is the problem as its turned off for the router interface. 

I think its definately a windows problem instead of a ubuntu problem because it wont even see itself in the view workgroups window. But nevermind. I'll marke this as solved as I no longer care as long as the laptop has access to files on windows, thats all that matters.

---

