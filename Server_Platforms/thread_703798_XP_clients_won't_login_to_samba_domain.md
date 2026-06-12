---
title: "XP clients won't login to samba domain"
date: 2008-02-21
forum: Server Platforms
---

### Post by beaker15 on 2008-02-21
Hi, 

I have a small network with several Windows XP clients and an Ubuntu server (7.10) running Samba (3.0.26) as a Domain Controller but can't get the clients to login to the domain. Here's my smb.conf:

[global]
	name resolve order = wins lmhosts host bcast
	idmap gid = 10000-20000
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	admin users = test frc @Admin
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = SRV-01
	writeable = yes
	printing = cups
	idmap uid = 10000-20000
	local master = yes
	workgroup = CYSOL
	os level = 65
	printcap name = cups
	security = user
	max log size = 1000
	delete user script = /user/sbin/userdel -r %u
	log level = 3
	log file = /var/log/samba/log.%m
	load printers = yes
	add group script = /usr/sbin/groupadd %g
	socket options = TCP_NODELAY
	delete group script = /usr/sbin/groupdel %g
	add user to group script = /usr/sbin/usermod -G %g %u
	logon drive = L:
	domain master = yes
	interfaces = 127.0.0.0/8 eth0
	encrypt passwords = yes
	logon home = \\%N\%U
	printer admin = test frc @Admin
	passdb backend = tdbsam
	template shell = /bin/bash
	wins support = true
	server string = %h server (Samba %v, Ubuntu)
	path = /usr/network/
	unix password sync = no
	logon path = \\%N\%U\profile
	add user script = /usr/sbin/useradd -m %u
	valid users = test frc @Admin
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	domain logons = yes
	#winbind enable local accounts = no
	#winbind trusted domains only = yes
	#winbind enable local accounts = no

All the client machines have been added to samba as machine trust accounts and users have been added too. In Windows, I can join the domain with the user 'frc' which succeeds and brings up the message 'Welcome to the domain CYSOL'. Its only after restarting and trying to login at startup that it brings up the standard message saying the domain controller is unavailable or machine account not found. testparm shows the server as a PDC with no errors. Here's some lines I've picked out from a few of the logfiles:

smbd.log

[2008/02/21 15:55:37, 3] smbd/connection.c:yield_connection(76)
  yield_connection: tdb_delete for name  failed with error Record does not exist.
[2008/02/21 15:55:37, 3] smbd/server.c:exit_server_common(768)

[2008/02/21 15:55:38, 3] passdb/lookup_sid.c:store_gid_sid_cache(1133)
  store_gid_sid_cache: gid 10001 in cache -> S-1-5-32-545
[2008/02/21 15:55:38, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-21-2617085589-4112103509-674510089-1000]
[2008/02/21 15:55:38, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2008/02/21 15:55:38, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2008/02/21 15:55:38, 3] lib/util_seaccess.c:se_access_check(250)
[2008/02/21 15:55:38, 3] lib/util_seaccess.c:se_access_check(251)
  se_access_check: user sid is S-1-5-21-2617085589-4112103509-674510089-1000
  se_access_check: also S-1-5-32-544
  se_access_check: also S-1-1-0
  se_access_check: also S-1-5-2
  se_access_check: also S-1-5-11

SRV-01.log  [server]

[2008/02/21 15:42:14, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [CYSOL]\[frc]@[SRV-01] with the new password interface
[2008/02/21 15:42:14, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [CYSOL]\[frc]@[SRV-01]

[2008/02/21 15:42:14, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [frc] -> [frc] -> [frc] succeeded
[2008/02/21 15:42:14, 3] passdb/lookup_sid.c:fetch_gid_from_cache(1089)
  fetch gid from cache 10000 -> S-1-5-32-544
[2008/02/21 15:42:14, 3] passdb/lookup_sid.c:fetch_gid_from_cache(1089)
  fetch gid from cache 10001 -> S-1-5-32-545
[2008/02/21 15:42:14, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-21-2617085589-4112103509-674510089-3000]
[2008/02/21 15:42:14, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-0]
2008/02/21 15:42:14, 3] smbd/service.c:make_connection_snum(1033)
  srv-01 (127.0.0.1) connect to service IPC$ initially as user frc (uid=0, gid=0) (pid 4197)


CYCLE-05.log [client]

[2008/02/21 15:58:04, 3] lib/util_sid.c:string_to_sid(223)
  string_to_sid: Sid frc does not start with 'S-'.
[2008/02/21 15:58:04, 3] lib/util_sid.c:string_to_sid(223)
  string_to_sid: Sid @Admin does not start with 'S-'.
[2008/02/21 15:58:04, 2] smbd/uid.c:change_to_user(193)
  change_to_user: SMB user  (unix user nobody, vuid 101) not permitted access to share IPC$.
[2008/02/21 15:58:04, 0] smbd/service.c:make_connection_snum(928)
  Can't become connected user!



If this is a problem with SID/UID/GIDs how do i fix it or even test it?
I'm considering uninstalling samba and reinstalling because i'm running out of ideas on this so any suggestions are appreciated. Please ask if you need any more info or logfile stuff. 

thanks

---

### Post by lnx4me on 2008-02-21
Okay, 
   I see a few issues. Where are your share definitions? Where are your printer definitions? The Global section ??????  You dont have a NETLOGON share which is pretty much a requirement. 

Do you happen to have the original smb.conf file? I think your gonna need to take a second look at your choices.

Lastly, google samba 3 by example.

---

### Post by beaker15 on 2008-02-22
my mistake that, I do have those things but because they're at the bottom of the conf file below all the hashed comments, i forgot to include them in my post. here they are (without the hashed comments):

[homes]
   comment = Home Directories
   browseable = no

valid users = %S
writable = yes
;   create mask = 0600
  directory mask = 0700

[netlogon]
	path = /home/samba/netlogon
	comment = Network Logon Service
	share modes = no
	browsable = no
	available = yes

public = no
writable = no
[profiles]
	writable = no
	path = /home/samba/profiles
	create mask = 0600
	comment = Users profiles
	directory mask = 0700
	browsable = no
	public = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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


I haven't included the shares because i want to focus just on being able to login at the moment. If you can spot any mistakes in these please let me know.

---

### Post by astrotech226 on 2008-02-22
Your user or group database might not be correct.  Let's look at the user first.  What's the output of this?

 ```
pdbedit -v -u frc
```

---

