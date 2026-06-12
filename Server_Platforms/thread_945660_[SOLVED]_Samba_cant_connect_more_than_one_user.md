---
title: "[SOLVED] Samba cant connect more than one user"
date: 2008-10-12
forum: Server Platforms
---

### Post by artilheiro.mz on 2008-10-12
hey everyone

i just created my first samba network

the thing is i created users and samba users for everyone, but when more than one wants to login, it gives a error message saying something like someone is already logged in with that name or that maximum multiple connection has reaches the limit

i think it has something to do with adding a prefix on the smb.con file about the maximum allowed parallel connections

anyone can help?

many thanks in advance

---

### Post by lykwydchykyn on 2008-10-12
can you post  your /etc/samba/smb.conf file?

---

### Post by artilheiro.mz on 2008-10-13
i dont have access to my original smb.conf file, but i have here a copy of the tests i was doing, its pretty much the same with just some changes to the folders in share

does this help? ill post the original smb.conf file as soon as i can

> ;
; /etc/samba/smb.conf
;
; Sample configuration file for the Samba suite for Debian GNU/Linux
;
; Please see the manual page for smb.conf for detailed description of
; every parameter.
;

[global]

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d
   printing = cups
   printcap name = cups
   load printers = yes
   guest account = nobody
   invalid users = root

; "security = user" is always a good idea. This will require a Unix account
; in this server for every user accessing the server.
   security = user

; Change this for the workgroup your Samba server will part of
   workgroup = TROPICALWEB

   server string = %h server (Samba %v)

; If you want Samba to log though syslog only then set the following
; parameter to 'yes'. Please note that logging through syslog in
; Samba is still experimental.
   syslog only = no

; We want Samba to log a minimum amount of information to syslog. Everything
; should go to /var/log/{smb,nmb} instead. If you want to log through
; syslog you should set the following parameter to something higher.
   syslog = 0;

; This socket options really speed up Samba under Linux, according to my
; own tests.
   socket options = IPTOS_LOWDELAY TCP_NODELAY SO_SNDBUF=4096 SO_RCVBUF=4096

; Passwords are encrypted by default. This way the latest Windows 95 and NT
; clients can connect to the Samba server with no problems.
   encrypt passwords = true
;   passdb backend = smbpasswd guest

; It's always a good idea to use a WINS server. If you want this server
; to be the WINS server for your network change the following parameter
; to "yes". Otherwise leave it as "no" and specify your WINS server
; below (note: only one Samba server can be the WINS server).
; Read BROWSING.txt for more details.
   wins support = no

; If this server is not the WINS server then specify who is it and uncomment
; next line.
;   wins server = 172.16.0.10

# If we receive WINS server info from DHCP, override the options above.
   include = /etc/samba/dhcp.conf

; Please read BROWSING.txt and set the next four parameters according
; to your network setup. There is no valid default so they are commented
; out.
;   os level = 0
;   domain master = no
;   local master = no
;   preferred master = no

; What naming service and in what order should we use to resolve host names
; to IP addresses
   name resolve order = lmhosts host wins bcast

; This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

; Name mangling options

   preserve case = yes
   short preserve case = yes

; This boolean parameter controlls whether Samba attempts to sync. the Unix
; password with the SMB password when the encrypted SMB password in the
; /etc/samba/smbpasswd file is changed.
   unix password sync = false

; For Unix password sync. to work on a Debian GNU/Linux system, the following
; parameters must be set (thanks to Augustin Luton
; <aluton@hybrigenics.fr> for sending the correct chat script for
; the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n
*Retype\snew\sUNIX\spassword:* %n\n .

; The following parameter is useful only if you have the linpopup package
; installed. The samba maintainer and the linpopup maintainer are
; working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

; The default maximum log file size is 5 MBytes. That's too big so this
; next parameter sets it to 1 MByte. Currently, Samba rotates log
; files (/var/log/{smb,nmb} in Debian) when these files reach 1000 KBytes.
; A better solution would be to have Samba rotate the log file upon
; reception of a signal, but for now on, we have to live with this.
   max log size = 1000

   obey pam restrictions = yes

; Some defaults for winbind (make sure you're not using the ranges
; for something else.)
;   winbind uid = 10000-20000
;   winbind gid = 10000-20000
;   template shell = /bin/bash

; ISOLATIN1 with euro sign
 unix charset = iso-8859-15
 display charset = iso-8859-15
 dos charset = 850

[homes]
   comment = Home Directories
   browseable = no

; By default, the home directories are exported read only. Change next
; parameter to "no" if you want to be able to write to them.
   read only = yes

; File creation mask is set to 0700 for security reasons. If you want to
; create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

; Directory creation mask is set to 0700 for security reasons. If you want to
; create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   guest ok = no
   read only = yes
   write list = knoppix

[printers]
   printer admin = knoppix
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700


[administracao]
path = /home/administracao
browseable = yes
force create mode = 0770
writable = yes


[gerente]
path = /home/gerente
browseable = yes
#read only = yes
write list = gerente, administracao
guest ok = no
writable = yes

[vendas]
path = /home/vendas
browseable = yes
read only = yes
guest ok = no
writeable = yes



[tecnica]
path = /home/tecnica
browseable = yes
#read only = yes
guest ok = no
writable = yes

[contabilidade]
path = /home/contabilidade
browseable = yes
#read only = yes
guest ok = no
writeable = yes

; A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes
;
; The next two parameters show how to auto-mount a CD-ROM when the
; cdrom share is accesed. For this to work /etc/fstab must contain
; an entry like this:
;
;       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
;
; The CD-ROM gets unmounted automatically after the connection to the
;
; If you don't want to use auto-mounting/unmounting make sure the CD
; is mounted on /cdrom
;
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


---

### Post by artilheiro.mz on 2008-10-13
I have finally found a solution for this problem

after doing some research, i found that the problem whas with the windows mapping the network drives

thing is, when i got the server up and running, i could loggin on every diferent computer without any problems

the stress just started to appear after in every computer, i mapped the network drives for each user..

after deleting the mapped network drives, that error message stopped appearing

now is this a samba/ubuntu error? or is it microsoft´s fault?
enjoy

---

### Post by lykwydchykyn on 2008-10-13
Without seeing the actual error, that'd be hard to say.

---

### Post by artilheiro.mz on 2008-10-14
the error was saying something like this:

> Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed.Disconnect all previous connections to the server or shared resource and try again.

is there any way we can get around having the drives mapped on each pc and still can connect?

---

### Post by artilheiro.mz on 2008-10-14
loving ubuntu btw

---

### Post by kah00na on 2008-12-22
I think it is a Windows issue.  From what I've seen, these errors come when a person connects to a share using one name and then tries to connect to the same share again using a different name.  

I think you can fix this by clearing the network share you have already established on your desktop.  Open a command prompt and type:

net use * /delete

This lists out your network shares and prompts you to confirm that you want to delete them all.  You can press "Y" to delete them all and try the connection again. 

If you see the server name listed in the list of shares, you can delete just that share instead of deleting them all with this command:

net use \\hostname\sharename /delete

This will leave all your other shares in place and just remove the one that is causing the problem.

---

