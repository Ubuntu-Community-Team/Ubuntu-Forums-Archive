---
title: "Need help sharing files with a Windows workstation"
date: 2006-06-05
forum: Server Platforms
---

### Post by lgyeresi on 2006-06-05
I'm trying to share a folder from an Ubuntu 6.06 server with my Windows XP workstation. I right-clicked on the folder, set it to use SMB, put in the correct domain and allowed browse permissions. On my Windows machine, I go to \\ubuntu-server-name and it asks me to authenticate. I tried both root and admin (user account I created), and neither one worked. What am I missing here?

---

### Post by Iowan on 2006-06-05
Does the windows user have a counterpart (same username) on the Ubuntu box (and on Samba)? (Depending on how your shares are defined, one/more may be unnececessary.)

---

### Post by lgyeresi on 2006-06-05
I created a counterpart on the ubuntu computer, but it still says the same message.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=lgyeresi]I created a counterpart on the ubuntu computer, but it still says the same message.[/QUOTE]

two choices:

-> wrong samba configuration (guest allowed / auth required?)
-> you didn't add the needed user account to samba (not the linux system!)?

Check your smb.conf (and maybe the related man page "man smb.conf") .... test it again. If it fails again, check the samba log files (stored in /var/log/samba/) for more details about the problem ...

If all fails and you can't get it work please post the smb.conf file (without the comments, of course, only the valid config items).

swat could be helpfull to configure samba and also contains explaining how to configure.

Thomas

---

### Post by LordHunter317 on 2006-06-05
Did you create a SMB password for your user via 'sudo smbpasswd -a username'?

If not, you will never be able to connect.

---

### Post by unicycler on 2006-06-05
Do you need to use Windows file sharing/SMB? Have you tried using an FTP connection?

---

### Post by lgyeresi on 2006-06-06
Here is what my smb.conf file looks like:


   workgroup = aiministry.org
   dns proxy = yes

   log file = /var/log/samba/log.%m
   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = root
;   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[Usrlocalbin]
path = /usr/local
available = yes
browseable = yes
public = yes
writable = yes

[firebird$]
path = /usr/firebird

[firebird$]

[firebird$]
available = yes

[firebird$]
browseable = yes

[firebird$]
public = yes

[firebird$]
writable = yes

[firebird$]

[firebird$]

[firebird$]

[firebird]
path = /usr/firebird
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by lgyeresi on 2006-06-06
[QUOTE=LordHunter317]Did you create a SMB password for your user via 'sudo smbpasswd -a username'?

If not, you will never be able to connect.[/QUOTE]

Yes I did. I typed in "sudo smbpasswd -a root ' and then whatever password I wanted.

---

### Post by LordHunter317 on 2006-06-06
You should ***never, ever, ever connect to Samba as root.  You should never, ever, ever have root be the guest account.*** 

Fix those things first.  No reason in helping you util you've done otherwise.  Frankly, I'm not even sure samba will start with that config file.

---

### Post by lgyeresi on 2006-06-06
I changed the config file. Here is what it reads now:


   workgroup = aiministry.org
   dns proxy = yes

   log file = /var/log/samba/log.%m
   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = admin
   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[Usrlocalbin]
path = /usr/local
available = yes
browseable = yes
public = yes
writable = yes

[firebird$]
path = /usr/firebird

[firebird$]

[firebird$]
available = yes

[firebird$]
browseable = yes

[firebird$]
public = yes

[firebird$]
writable = yes

[firebird$]

[firebird$]

[firebird$]

[firebird]
path = /usr/firebird
available = yes
browseable = yes
public = yes
writable = yes





I rebooted the server, because I couldn't think of any other way of starting samba. I'm still a noob.

---

### Post by lgyeresi on 2006-06-07
Bump. Can someone help me out?

---

### Post by Iowan on 2006-06-07
Run **testparm** to verify your smb.conf is valid.  If what you posted is really what you have, you'll probably want to delete some of those extra definitions of **firebird$**.  Also, I didn't notice a **security = ** statement.  Required??? My server uses  **security = user**, followed by **username map = /etc/samba/smbusers**.  I hear  **security = share** bypasses the password requirement, but bypassing security isn't high on my list.

---

### Post by lgyeresi on 2006-06-08
I got it working using the security = share line.

---

