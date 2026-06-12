---
title: "How to use Ubuntu 22.04LTS samba server to authenticate windows server 2016 r2 ADS?"
date: 2022-06-27
forum: Server Platforms
---

### Post by beninchurchil on 2022-06-27
[h=2]I have a windows server 2016 r2 standard DC with AD DS setup, I am building a samba server on the latest Ubuntu 22.04LTS Desktop. I need to create samba share on the ubuntu and use the active directory users and credentials to authenticate the samba shares and permissions accordingly.[/h][COLOR=#232629][FONT=-apple-system]WINDOWS SERVER IP 192.168.1.10 UBUNTU SERVER IP 192.168.1.47 As per this link I have completed the prerequisites[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][https://ubuntu.com/server/docs/service-sssd-ad](https://ubuntu.com/server/docs/service-sssd-ad)[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]i) I have a working Active directory service (Windows Server 2016 R2 Standard) IP address 192.168.1.10[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]The DC (Domain Controller) is acting as an authoritative DNS server for the domain.( I believe its the windows server they're talking about?)[/FONT]

[*][FONT=inherit]Updated and synced time with DC using NTP configuration[/FONT]

[*][FONT=inherit]Ran the following commands[/FONT]
[FONT=inherit]$sudo apt install sssd-ad sssd-tools realmd adcli[/FONT]

[*][FONT=inherit]Ran this command after successfully completed the installation[/FONT]
[FONT=inherit]$sudo realm -v discover 01itpdc001.raysrvr.com[/FONT]

[*][FONT=inherit]The discovery was successful and I connected to server using the following command[/FONT]
[FONT=inherit]$sudo realm join -v 01itpdc001.raysrvr.com -U benin[/FONT]

[*][FONT=inherit]I was able to join the domain successfully without any issues[/FONT]

[*][FONT=inherit]Ran the following command to check my sssd files as per the link[/FONT]
[FONT=inherit]$ sudo nano /etc/sssd/sssd.conf
[/FONT]
[h=2]I have a windows server 2016 r2 standard DC with AD DS setup, I am building a samba server on the latest Ubuntu 22.04LTS Desktop. I need to create samba share on the ubuntu and use the active directory users and credentials to authenticate the samba shares and permissions accordingly.[/h]WINDOWS SERVER IP 192.168.1.10 UBUNTU SERVER IP 192.168.1.47 As per this link I have completed the prerequisites
[https://ubuntu.com/server/docs/service-sssd-ad](https://ubuntu.com/server/docs/service-sssd-ad)
i) I have a working Active directory service (Windows Server 2016 R2 Standard) IP address 192.168.1.10

[LIST=1]
[*][FONT=inherit]The DC (Domain Controller) is acting as an authoritative DNS server for the domain.( I believe its the windows server they're talking about?)[/FONT]

[*][FONT=inherit]Updated and synced time with DC using NTP configuration[/FONT]

[*][FONT=inherit]Ran the following commands[/FONT]
[FONT=inherit]$sudo apt install sssd-ad sssd-tools realmd adcli[/FONT]

[*][FONT=inherit]Ran this command after successfully completed the installation[/FONT]
[FONT=inherit]$sudo realm -v discover 01itpdc001.raysrvr.com[/FONT]

[*][FONT=inherit]The discovery was successful and I connected to server using the following command[/FONT]
[FONT=inherit]$sudo realm join -v 01itpdc001.raysrvr.com -U benin[/FONT]

[*][FONT=inherit]I was able to join the domain successfully without any issues[/FONT]

[*][FONT=inherit]Ran the following command to check my sssd files as per the link[/FONT]
[FONT=inherit]$ sudo nano /etc/sssd/sssd.conf[/FONT]
[/LIST]
and this is its content
domains = RAYSRVR.COM
config_file_version = 2
services = nss, pam

[domain/RAYSRVR.COM]
default_shell = /bin/bash
ad_server = 01itpdc001.raysrvr.com
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = RAYSRVR.COM
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u@%d
ad_domain = RAYSRVR.COM
use_fully_qualified_names = True
ldap_id_mapping = True
access_provider = ad

[LIST=1]
[*]Now i to fetch the AD user from the domain using the following command
[/LIST]
 ~$ getent passwd [email]benin@raysrvr.com[/email]
[email]benin@RAYSRVR.COM[/email]:*:674601161:674600513:Benin Churchill:/home/benin@RAYSRVR.COM: /bin/bash

[LIST=1]
[*]Able to login to AD user from here using the followng command as well.
[/LIST]
rayoffice@rayfiles:~$ sudo login
rayfiles login: [email]benin@raysrvr.com[/email]
Password:
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-39-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

0 updates can be applied immediately.

Last login: Fri Jun 24 16:28:43 IST 2022 on pts/1
[email]benin@RAYSRVR.COM[/email]@rayfiles:~$

[LIST=1]
[*]Next I followed the below link to create a samba share with the AD user
[/LIST]
[https://ubuntu.com/server/docs/samba-active-directory](https://ubuntu.com/server/docs/samba-active-directory)

[LIST=1]
[*]Installed samba and the necessary utilities with commands given in the link above
[/LIST]
[FONT=inherit][/FONT]
sudo apt install samba cifs-utils smbclient

[LIST=1]
[*]As per the link below changes is what it said to make in the samba file in /etc/samba/smb.conf
[/LIST]


   workgroup = EXAMPLE
   ...
   security = ads
   realm = EXAMPLE.COM
   ...
   idmap backend = lwopen
   idmap uid = 50-9999999999
   idmap gid = 50-9999999999

[LIST=1]
[*]Here is my samba filE
[*]
[*][global]
[*]## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = RAYSRVR.COM
   security = ads
   realm = RAYSRVR.COM

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# We want Samba to only log to /var/log/samba/log.{smbd,nmbd}.
# Append syslog@1 if you want important messages to be sent to syslog too.
   logging = file

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller".
#
# Most people will want "standalone server" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = classic
# primary domain controller', 'server role = classic backup domain controller'
# or 'domain logons' is set
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)

   idmap backend = lwopen
   idmap uid = 50-9999999999
   idmap gid = 50-999999999

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 means that usershare is disabled.
#   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
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

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Marketing]

    comment = Marketing
    path = /marketing/
    valid users = @RAYSRVR.COM\"Domain Users"
    force group = marketing
    writable = yes
    read only = no
    force create mode = 0660
    create mask = 0777
    directory mask = 0777
    force directory mode = 0770
    access based share enum = yes
    hide unreadable = yes


But I get access denied error
[/LIST]
[/LIST]

---

