---
title: "Win7 Roaming Profile recently broke"
date: 2013-01-21
forum: Server Platforms
---

### Post by kjwkjw on 2013-01-21
I'm stumped.  I used to have roaming profiles working, but they recently stopped, and I can't figure out how to get it working again.  Specifically, *new* profiles aren't getting created.  Instead I get a 30 second timeout and "You have been logged on with a temporary profile".  If I log in with an existing profile, it gets downloaded and used and logouts write the changes back to the server.  I can even browse to the share, and create files in the new $USER.V2/ profile dir that's created (it's empty).  So it's not a file permissions issue; after logging in I can create files there no problem.  But logging in always gets me a temporary profile, and logging out never writes it to the server.  Help!


Config:
apt-get upgrade says nothing to upgrade (now = 2013.01.21-01:40)
ip = 10.10.221.8
dns A records exist for ldap.leei.com mega.sj.leei.com profiles.leei.com
** The remote office resolves profiles.leei.com to a local (different) IP!  They don't have a BDC either.
smbstatus shows no files open or locked (like when downloading the roaming profile) whatsoever.

# cat /etc/issue
Ubuntu 12.04.1 LTS \n \l
# uname -a
Linux mega 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686 i686 i386 GNU/Linux
# dpkg -l samba | tail -1
ii  samba               2:3.6.3-2ubuntu2.3  SMB/CIFS file, print, and login server for Unix

# hostname
mega

root@mega:/etc/samba# egrep -v '^ *[;#]' smb.conf | egrep -v '^$'
[global]
log level = 3
   workgroup = LEEI
   server string = %h server (Samba, Ubuntu)
wins support = yes
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = ldapsam:ldap://ldap.leei.com
   ldap suffix = dc=leei,dc=com
   ldap user suffix = ou=people
   ldap group suffix = ou=groups
   ldap machine suffix = ou=computers
   ldap idmap suffix = ou=Idmap
   ldap admin dn = cn=admin,dc=leei,dc=com
   ldap ssl = start tls
   ldap passwd sync = yes
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   domain logons = yes
   logon path = \\profiles.leei.com\Profiles\%U
   add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"
load printers = yes
printing = bsd
printcap name = /etc/printcap
   usershare allow guests = yes
[homes]
   comment = Home Directories
   browseable = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
   path = %H/samba
[Public]
   comment = Shared with all
   path = /d/export/Public
   guest ok = no
   read only = no
   browseable = yes
   create mask = 0770
   directory mask = 0770
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no
[Profiles]
   comment = Roaming Profiles
   path = /d/export/Profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700
   read only = No
   profile acls = Yes
[Desktop Software]
   path = /d/export/DesktopSoftware
   read only = Yes
[Printers]
   comment = All Printers
   browseable = yes
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
   write list = root,kjw

Win7 side, I reboot, and type in the user name/pass, and press enter at Mon Jan 21 01:01:05 PST 2013

root@mega:/var/log/samba# vi log.india
...too big, can't attach... [http://rightsock.com/~kjw/tmp/log.india.txt](http://rightsock.com/~kjw/tmp/log.india.txt)

I notice there are some errors about not being able to find "well known groups".  I see the same queries being passed into LDAP, but I don't know whether these are fatal.  Windows has a very very long list of standardized groups.  for example:
[FONT="Courier New"][2013/01/21 01:01:10.489529,  3] groupdb/mapping.c:772(pdb_create_builtin_alias)
  pdb_create_builtin_alias: Could not get a gid out of winbind
[2013/01/21 01:01:10.489670,  2] auth/token_util.c:479(finalize_local_nt_token)
  WARNING: Failed to create BUILTIN\Users group! Can Winbind allocate gids?
[/FONT]

The below is an expected error; I don't create HOMES share directories except for myself:
[FONT="Courier New"][2013/01/21 01:01:18.977632,  0] smbd/service.c:1022(make_connection_snum)
  canonicalize_connect_path failed for service elee, path /home/elee/samba
[/FONT]

Here is the list of well knows groups that I have defined # net groupmap list
Domain Admins (S-1-5-21-3316127529-1793056107-4204239575-512) -> Domain Admins
Domain Users (S-1-5-21-3316127529-1793056107-4204239575-513) -> Domain Users
Domain Guests (S-1-5-21-3316127529-1793056107-4204239575-514) -> Domain Guests
Domain Computers (S-1-5-21-3316127529-1793056107-4204239575-515) -> Domain Computers
Administrators (S-1-5-32-544) -> Administrators
Account Operators (S-1-5-32-548) -> Account Operators
Print Operators (S-1-5-32-550) -> Print Operators
Backup Operators (S-1-5-32-551) -> Backup Operators
Replicators (S-1-5-32-552) -> Replicators


... so what am I overlooking?

Note that I got impatient and changed the network timeout from the default 30s to 7s.  That is:

Start -> gpedit.msc
Local Computer Policy / Computer Configuration / Administrative Templates / System / User Profiles ->
"Set maximum wait time for the network if a user has a roaming user profile or a remote home directory"
Enabled, 7s

Lastly, the windows event logs show nothing that looks particularly interesting.  Previous logout attempts did include the error """Windows detected your registry file is still in use by other applications or services.  The file will be unloaded now.  The applications or services that hold your registry file may not function properly afterwards."""

---

