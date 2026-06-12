---
title: "log.smbd INTERNAL ERROR"
date: 2005-03-08
forum: Server Platforms
---

### Post by steveM49 on 2005-03-08
I am getting the following log from log.nmdb after simplifying the smb.conf as much as possible:

[2005/03/06 06:25:04, 0] lib/fault.c:fault_report(36)
  ===============================================================
[2005/03/06 06:25:04, 0] lib/fault.c:fault_report(37)
  INTERNAL ERROR: Signal 11 in pid 4031 (3.0.7-Ubuntu)
  Please read the appendix Bugs of the Samba HOWTO collection
[2005/03/06 06:25:04, 0] lib/fault.c:fault_report(39)
  ===============================================================
[2005/03/06 06:25:04, 0] lib/util.c:smb_panic2(1456)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 4031]
/etc/samba/gdbcommands:1: Error in sourced command file:
Previous frame inner to this frame (corrupt stack?)
[2005/03/08 12:51:12, 0] lib/util.c:smb_panic2(1464)
  smb_panic(): action returned status 0
[2005/03/08 12:51:12, 0] lib/util.c:smb_panic2(1466)
  PANIC: internal error
[2005/03/08 12:51:12, 0] lib/util.c:smb_panic2(1474)
  BACKTRACE: 4 stack frames:
   #0 /usr/sbin/smbd(smb_panic2+0xfd) [0x81c2d5e]
   #1 /usr/sbin/smbd(smb_panic+0x19) [0x81c2c5d]
   #2 /usr/sbin/smbd [0x81b1ec2]
   #3 [0xffffe420]
[2005/03/08 12:52:06, 0] smbd/server.c:main(760)
  smbd version 3.0.7-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/03/08 12:52:06, 0] param/loadparm.c:service_ok(2619)
  No path in service netlogon - using /tmp


the smb.conf as simplified reads:
#
# Configuration file for the Samba suite for Debian GNU/Linux.
#
#  Simpler config SJM 3/6/05
#

#======================= Global Settings =======================

[global]
   workgroup = OLYMPUS
# Using Samba 2nd Edition page 122
   netbios name = hermes
   domain master = yes
   local master = yes
   preferred master = yes
   os level = 65
;   security = user
;   domain logons = yes
;   logon script = logon.bat
;   logon drive = H:
;   add user script = /usr/sbin/useradd -d /dev/null -g 100 -s /bin/false -M %u
   
# add via US2nd p 204
;   hosts allow = 192.168.1.

# add via US2nd p 220
;   wins support = yes

# server string is the equivalent of the NT Description field
;   server string = %h


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
;   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
;   max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
;   syslog = 2

# Do something sensible when Samba crashes: mail the admin a backtrace
;   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;   passdb backend = smbpasswd

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
;   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes
;   create mask = 0775
;   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
;   comment = Network Logon Service
;   path = /usr/local/samba/lib/netlogon
;   guest ok = no
;   writable = no
;   share modes = no

Than ks for any help you can give,
Steve M

---

