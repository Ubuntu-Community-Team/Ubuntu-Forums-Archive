---
title: "Shared printer"
date: 2006-06-13
forum: Server Platforms
---

### Post by Tobas on 2006-06-13
Hi,

i have followed the tutorial on how to instal a Lexmark printer and everything works ( local )
But when i try to print with it from a winXP pc the i get a permission denied error.
When i instal the printer on the winXP machine i see it so its shared.

Heres my smb conf 

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]   
workgroup = WERKGROUP
netbios name = hostel
server string = %h server (Samba, Ubuntu)      
passdb backend = tdbsam   
security = user   
username map = /etc/samba/smbusers   
name resolve order = wins bcast hosts   
domain logons = yes   
preferred master = yes   
wins support = yes      
# Set CUPS for printing   
printcap name = CUPS   
printing = CUPS      
# Default logon   
logon drive = Z:   
#logon script = scripts/logon.bat   
logon path = \\hostel\profile\%U   
# Useradd scripts   
add user script = /usr/sbin/useradd -m %u   
delete user script = /usr/sbin/userdel -r %u   
add group script = /usr/sbin/groupadd %g   
delete group script = /usr/sbin/groupdel %g   
add user to group script = /usr/sbin/usermod -G %g %u   
add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u   
idmap uid = 15000-20000   
idmap gid = 15000-20000   
# sync smb passwords woth linux passwords   
passwd program = /usr/bin/passwd %u   
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .   
passwd chat debug = yes   
unix password sync = yes      
# set the loglevel   
log level = 3
[homes]   
comment = Home   
valid users = %S   
read only = no   
browsable = no
[printers]   
comment = All Printers   
path = /var/spool/samba   
printable = yes   
guest ok = yes   
browsable = no
[netlogon]   
comment = Network Logon Service   
path = /home/samba/netlogon   
admin users = Administrator   
valid users = %U   
read only = no
[profile]   
comment = User profiles   
path = /home/samba/profiles   
valid users = %U   
create mode = 0600   
directory mode = 0700   
writable = yes   
browsable = no
[allusers]  
comment = All Users  
path = /home/shares/allusers  
valid users = @users  
force group = users   
create mask = 0660  
directory mask = 0771  
writable = yes
[downloads]  
comment = Downloads  
path = /var/downloads  
valid users = @users  
force group = users   
create mask = 0660  
directory mask = 0771  
writable = yes

```

and this is my Cupsd.conf

```

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
Listen localhost:631
192.168.1.65:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic
AuthGroupName shadow

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow 192.168.1.0/24
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
#    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#

```

Someone have a idea ??


Tobas

---

### Post by Tobas on 2006-06-15
**bump**

---

### Post by givré on 2006-06-16
[https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu) ;) 
I hope it could help

---

