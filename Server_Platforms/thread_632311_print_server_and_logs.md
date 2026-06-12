---
title: "print server and logs"
date: 2007-12-05
forum: Server Platforms
---

### Post by amazilia on 2007-12-05
Hi,

I have a print server on gutsy using samba and  cups.

all users are able to print from the server and their name appear on the logs (i am using phpprintanalyzer)

if I try to print from another pc, it works fine but then the name of the user is nobody instead 

how to make sure that the name of the user will be inscribed into the log when the user is on a remote machine. 


thanks in advance

Philippe


smb.conf : 
```

[global]


        workgroup = ATC
        netbios name = SERVATC
	passwd chat = *New*Password*      %n\n*Re-enter*new*password* %n\n *Password*changed*
	username map = /etc/samba/smbusers
	syslog = 0
	name resolve order = wins bcast hosts
	printcap name = CUPS
	show add printer wizard = No
	add user script = /usr/sbin/useradd -m %u
	delete user script = /usr/sbin/userdel -r %u
	add group script = /usr/sbin/groupadd %g
	delete group script = /usr/sbin/groupdel %g
	add user to group script = /usr/sbin/usermod -G %g %u
	add machine script = /usr/sbin/useradd       -s /bin/false -d /dev/null %u
	logon script = %a.bat
	logon path = 
	domain logons = Yes
	os level = 75
	preferred master = Yes
	wins support = no
	load printers = yes
        printing = cups
	printcap name = cups
        printer admin = root

        print command = 
	lpq command = %p
	lprm command = 
	security = user

[homes]
	comment = Dossiers personnels
	valid users = %S
	read only = No
	browseable = No

[printers]
	browseable = No
	printable = Yes
	path = /var/spool/samba
	comment = système d'impression
	public = yes
	printer admin = root
	use client driver = Yes

[netlogon]
	comment = serveur de scripts
	path = /home/samba/netlogon/%U
	valid users = %S
	read only = No

[print$]
	browseable = yes
	comment = drivers pour imprimantes
	public = yes
	write list = root
	path = /etc/samba/printers

[public]
	comment = Acces libre
	path = /media/archives
        create mask = 0777
        directory mask = 0777
	read only = No
	guest ok = Yes

[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no
   guest ok = no



```

---

