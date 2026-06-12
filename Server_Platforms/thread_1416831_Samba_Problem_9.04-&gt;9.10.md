---
title: "Samba Problem 9.04-&gt;9.10"
date: 2010-02-26
forum: Server Platforms
---

### Post by Sensenseppl on 2010-02-26
Hello!

I recently upgraded our Ubuntu Server from 9.04 to 9.10.
In the progress our samba primary domain controller got updated from >3.2.0 to 3.4.0.

Now, access of the shares is still possible via direct access \\IP\share.

But all windows XP machines complain about not being able to reach the domain controller anymore.

**sudo pdbedit -L** successfully lists some machines and my main user, but not all configured samba users.

**nmblookup -A ASGARD** (ASGARD is the domain) returns the following:
```
Looking up status of 0.0.0.0
	ODIN            <00> -         H <ACTIVE> 
	ODIN            <03> -         H <ACTIVE> 
	ODIN            <20> -         H <ACTIVE> 
	..__MSBROWSE__. <01> - <GROUP> H <ACTIVE> 
	ASGARD          <1d> -         H <ACTIVE> 
	ASGARD          <1b> -         H <ACTIVE> 
	ASGARD          <1c> - <GROUP> H <ACTIVE> 
	ASGARD          <1e> - <GROUP> H <ACTIVE> 
	ASGARD          <00> - <GROUP> H <ACTIVE> 

	MAC Address = 00-00-00-00-00-00
```

**smbtree** successfully lists my shares.

I should mention that, during the update, some *.tdb files could have changed.

Here's the smb.conf:
```
[global]
   workgroup = asgard
   server string = %h server (Samba, Ubuntu)
   wins support = yes
   dns proxy = no

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   mangled names = no

   security = user
   encrypt passwords = true
   update encrypted = yes
#   passdb backend = tdbsam
#   obey pam restrictions = no
   unix password sync = no
#   map to guest = bad user

   unix extensions = no

   domain logons = yes
   logon path = \\%N\profiles\%U 
   logon home = \\%N\\profiles\%U
   logon script = logon.bat
   logon drive = Z:

#   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
#   add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
#   add group script = /usr/sbin/addgroup --force-badname %g

   load printers = no

   socket options = TCP_NODELAY
   domain master = auto
#   idmap uid = 10000-20000
#   idmap gid = 10000-20000
#   template shell = /bin/bash
#   winbind enum groups = yes
#   winbind enum users = yes
#   usershare max shares = 100
#   usershare allow guests = no


[home]
  comment = Network User Drive
  path = /home/%u
  read only = no
  browseable = yes
  writeable = yes
  create mode = 770
  directory mode = 2770
  force create mode = 770
  force directory mode = 2770

[netlogon]
  comment = Network Logon Service
  path = /daten/samba/netlogon
  guest ok = yes
  read only = yes
#  share modes = no

[profiles]
  comment = Windows User Profile
  path = /daten/samba/profiles
  writeable = yes
  create mode = 700
  directory mode = 0700
  force create mode = 00700
  force directory mode = 0700

[public]
  comment = Network Public Drive
  path = /daten/public
  read only = no
  browseable = yes
  writeable = yes
  create mode = 777
  directory mode = 2777
  force create mode = 777
  force directory mode = 2777

[backup]
  comment = Network Backup
  path = /daten/backup
  read only = no
  browseable = yes
  writeable = yes
  create mod = 777
  directory mode = 2777
  force create mode = 777
  force directory mode = 2777
```

Please help!

---

### Post by ubunterooster on 2010-02-26
sudo /etc/init.d/samba status
What's it say?

---

### Post by Sensenseppl on 2010-02-27
**sudo /etc/init.d/samba status:**
```
 * nmbd is running
 * smbd is running 
```

Furthermore **testparm** returns:
```
Load smb config files from /etc/samba/smb.conf
Processing section "[home]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[public]"
Processing section "[backup]"
Unknown parameter encountered: "create mod"
Ignoring unknown parameter "create mod"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

```

And **smbstatus** (with changed username/groupname):
```

Unknown parameter encountered: "create mod"
Ignoring unknown parameter "create mod"

Samba version 3.4.0
PID     Username      Group         Machine                        
-------------------------------------------------------------------
2815      myuser      mygroup      srvtest      (192.168.111.111)
2816      myuser      mygroup      srvtest      (192.168.111.111)

Service      pid     machine       Connected at
-------------------------------------------------------
home         2815   srvtest       Fri Feb 26 20:41:21 2010
public       2816   srvtest       Fri Feb 26 20:41:23 2010
IPC$         2814   srvtest       Fri Feb 26 20:41:14 2010

```

---

### Post by Sensenseppl on 2010-02-27
For any people having the same problem:
After migrating smbpasswd to tdbsam (see Configuration Changes: [http://www.samba.org/samba/history/samba-3.4.0.html](http://www.samba.org/samba/history/samba-3.4.0.html)), the Windows XP machines can log in again.

Windows 7 machines join after doing the following:
Adding the machine:
sudo useradd -g mysambagroup -d /dev/null -s /bin/false machinename$  (with the '$'!)
sudo smbpasswd -a -m -i machinename  (without the '$'!)

Setting registry entries according to: [http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)

EDIT: Thanks to #ubuntu-server and #samba on freenode! :)

---

