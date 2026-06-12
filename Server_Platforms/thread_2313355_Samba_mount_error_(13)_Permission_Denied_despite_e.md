---
title: "Samba mount error (13): Permission Denied despite everything seeming correct"
date: 2016-02-11
forum: Server Platforms
---

### Post by perrti02 on 2016-02-11
I have an issue with samba not letting me mount a share which exists on my server. I am trying to mount the share "Odin" on a VM inside Proxmox. As the title suggests the error is (13) permission denied and this seems to be whether I try to use a guest log on or a specific user. I have looked at various suggestions relating to changing the type of security, etc none of which seem to make any difference. I am slightly at a loss of what to do so any help would be appreciated.

The command I am using to mount the share is

```
mount -t cifs //192.168.1.200/Odin /mnt -o guest
```

and this works from the server but not the client (i.e. the server can mount its own share but the client can't mount the server's share). This makes me think Samba itself is configured correctly but something else is causing the problem.

---

### Post by bab1 on 2016-02-11
> **perrti02 said:**
> I have an issue with samba not letting me mount a share which exists on my server. I am trying to mount the share "Odin" on a VM inside Proxmox. As the title suggests the error is (13) permission denied and this seems to be whether I try to use a guest log on or a specific user. I have looked at various suggestions relating to changing the type of security, etc none of which seem to make any difference. I am slightly at a loss of what to do so any help would be appreciated.

The command I am using to mount the share is

```
mount -t cifs //192.168.1.200/Odin /mnt -o guest
```

and this works from the server but not the client (i.e. the server can mount its own share but the client can't mount the server's share). This makes me think Samba itself is configured correctly but something else is causing the problem.

Are you issuing this command as root (via sudo)?  Does the client have the package ***cifs-utils*** installed?

---

### Post by nerdtron on 2016-02-11
Add the -v option to your mount command so that we'll see a verbose output:

```
sudo mount -vt //192.168.1.200/Odin /mnt -o guest 
```

Also, try not to mount as guest ( just to make sure that the network and that samba is working properly).

```
sudo mount -vt //192.168.1.200/Odin /mnt -o user=admin,pass=adminpassword 
```

---

### Post by MAFoElffen on 2016-02-12
Check to see if the system you are mounting to uses ntlm or ntlmssp in the encryption method used in the passing of credentials. This new option change happened in mount.cifs about a year ago... 

For example, if one or the other, then what nerdtron suggested would change to something similar to:
```

sudo mount -vt //192.168.1.200/Odin /mnt -o user=admin,pass=adminpassword,sec=ntlm

```

Next, you didn't say what the virtualized guest was that is hosting the share. If either Windows or a Samba share, and it works with a privileged local user and their credentials, then check the options on permissions of Guest. It could be marked as Shared, but not accessible by Guest.

---

### Post by perrti02 on 2016-02-13
I am logged in as root so the client does have the required privileges. I have also made sure that cifs-utils is installed and is up to date.

The client is Ubuntu 15.04 server.

I have run the command again with a specific user and the result is as follows.

```
root@plex:/etc/samba# mount -vt cifs //192.168.1.200/Odin /mnt -o user=odin,pass=password,sec=ntlmpss
mount.cifs kernel  mount options: ip=192.168.1.200,unc=\\192.168.1.200\Odin,sec=ntlmpss,user=odin,pass=********
mount error(13): Permission denied
 Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I get the same results without specifying the security of specifying sec=ntlm.

The user "odin" can mount the share if the command is run from the server itself so I know the password is correct and the permissions are correct.

---

### Post by darkod on 2016-02-13
First, we are all fishing in the dark unless you post the global section and the share section of your smb.conf, so we can take a look at the settings.

Second, if trying to use the odin user have you added it as samba user? Can you try doing that? It would be something like:
```
sudo smbpasswd -a odin
```

Enter its password if prompted. Then try again. Is the share configured to have odin in the allowed users?

Accessing as guest should work if your settings are correct (hence I mentioned posting the smb.conf relevant parts).

Apart from the above, if this share is mostly to be used with a linux client, you can consider using something like nfs or even iscsi. Samba shares are mostly for use with windows clients. I might be wrong, but I think nfs or iscsi would give you much better performance and are more common if the client is also running linux. But that's moving the topic to another direction...

---

### Post by perrti02 on 2016-02-13
The smb.conf is as follows

```
# This is the main Samba configuration file. You should read the# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not many any basic syntactic errors. 
#
#======================= Global Settings =====================================
[global]


# workgroup = NT-Domain-Name or Workgroup-Name, eg: REDHAT4
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
   server string = Samba Server


# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
   hosts allow = 192.168.1. 127.


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes
   printing = cups
   rpc_server:spoolss = external
   rpc_daemon:spoolssd = fork


# you may wish to override the location of the printcap file
   printcap name = cups


# on SystemV system setting printcap name to lpstat should allow
# you to automatically obtain a printer list from the SystemV spool
# system
;   printcap name = lpstat


# It should not be necessary to specify the print system type unless
# it is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx
;   printing = bsd


# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
;  guest account = pcguest


# this tells Samba to use a separate log file for each machine
# that connects
   log file = /usr/local/samba/var/log.%m


# Put a capping on the size of the log files (in Kb).
   max log size = 50


# Security mode. Most people will want user level security. See
# security_level.txt for details.
   security = user


# Use password server option only with security = server
# The argument list may include:
#   password server = My_PDC_Name [My_BDC_Name] [My_Next_BDC_Name]
# or to auto-locate the domain controller/s
#   password server = *
;   password server = <NT-Server-Name>


# Note: Do NOT use the now deprecated option of "domain controller"
# This option is no longer implemented.


# You may wish to use password encryption. Please read
# ENCRYPTION.txt, Win95.txt and WinNT.txt in the Samba documentation.
# Do not enable this option unless you have read those documents
encrypt passwords = yes


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /usr/local/samba/lib/smb.conf.%m


# Most people will find that this option gives better performance.
# See speed.txt and the manual pages for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY 


# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
;   interfaces = 192.168.12.2/24 192.168.13.2/24 


# Browser Control Options:
# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
   local master = yes


# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
;   os level = 33


# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
;   domain master = yes 


# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
   preferred master = yes


# Enable this if you want Samba to be a domain logon server for 
# Windows95 workstations. 
;   domain logons = yes


# if you enable domain logons then you may want a per-machine or
# per user logon script
# run a specific logon batch file per workstation (machine)
;   logon script = %m.bat
# run a specific logon batch file per username
;   logon script = %U.bat


# Where to store roving profiles (only for Win95 and WinNT)
#        %L substitutes for this servers netbios name, %U is username
#        You must uncomment the [Profiles] share below
;   logon path = \\%L\Profiles\%U


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
   wins support = yes


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#	Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one	WINS Server on the network. The default is NO.
;   wins proxy = yes


# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
   dns proxy = no 


   map to guest = bad user


#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes


# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /usr/local/samba/lib/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no




# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /usr/local/samba/profiles
;    browseable = no
;    guest ok = yes




# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
;[printers]
;   comment = All Printers
;   path = /usr/spool/samba
;   browseable = yes
# Set public = yes to allow user 'guest account' to print
;   guest ok = no
;   writable = no
;   printable = yes


# This one is useful for people to share files
;[tmp]
;   comment = Temporary file space
;   path = /tmp
;   read only = no
;   public = yes


# A publicly accessible directory, but read only, except for people in
# the "staff" group
;[public]
;   comment = Public Stuff
;   path = /home/samba
;   public = yes
;   writable = yes
;   printable = no
;   write list = @staff


# Other examples. 
#
# A private printer, usable only by fred. Spool data will be placed in fred's
# home directory. Note that fred must have write access to the spool directory,
# wherever it is.
;[fredsprn]
;   comment = Fred's Printer
;   valid users = fred
;   path = /homes/fred
;   printer = freds_printer
;   public = no
;   writable = no
;   printable = yes


# A private directory, usable only by fred. Note that fred requires write
# access to the directory.
;[fredsdir]
;   comment = Fred's Service
;   path = /usr/somewhere/private
;   valid users = fred
;   public = no
;   writable = yes
;   printable = no


# a service which has a different directory for each machine that connects
# this allows you to tailor configurations to incoming machines. You could
# also use the %U option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.
;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes


# A publicly accessible directory, read/write to all users. Note that all files
# created in the directory by users will be owned by the default user, so
# any user with access can delete any other user's files. Obviously this
# directory must be writable by the default user. Another user could of course
# be specified, in which case all files would be owned by that user instead.
;[public]
;   path = /usr/somewhere/else/public
;   public = yes
;   only guest = yes
;   writable = yes
;   printable = no


# The following two entries demonstrate how to share a directory so that two
# users can place files there that will be owned by the specific users. In this
# setup, the directory should be writable by both users and should have the
# sticky bit set on it to prevent abuse. Obviously this could be extended to
# as many users as required.
;[myshare]
;   comment = Mary's and Fred's stuff
;   path = /usr/somewhere/shared
;   valid users = mary fred
;   public = no
;   writable = yes
;   printable = no
;   create mask = 0765


[printers]
  comment = All Printers
  browseable = yes
  path = /var/spool/samba
  printable = yes
  guest ok = yes
  read only = yes
  create mask = 0700


[print$]
  comment = Print Drivers
  path = /var/lib/samba/printers
  browseable = yes
  read only = yes
  guest ok = yes


[Media]
   comment = media on odin
   path = /srv/samba/Odin/Media
   valid users = odin
   writable = yes
   browseable = yes


[Downloads]
   comment = Downloads on Odin
   path = /srv/samba/Odin/Downloads
   valid users = odin
   writeable = yes
   browseable = yes


[Odin]
   comment = All files on Odin
   path = /srv/samba/Odin
   guest ok = yes
   guest account = odin
   writeable = yes
   browseable = yes


[TimeMachine]
   comment = Time Machine backup
   path = /srv/samba/Odin/TimeMachine
   valid users = odin
   writeable = yes
   browseable = yes


[test]
   comment = test
   path = /srv/samba/Odin
   guest ok = yes
   force user = odin



```

I have run the smbpasswd command and set the password as "password" in the past. As far as I can tell the odin user is one of the allowed users but I don't know how to check. I can use this server from other machines running Windows or OS X but Ubuntu seems not to work. I did also try NFS which seems to give similar results. It seems to be set up correctly but fails to connect. I don't know if this is related problem or whether I just don't know how to set up either.

---

### Post by darkod on 2016-02-13
I see you have three shares inside the Odin folder, which makes them inside the Odin share. I am no samba expert, I guess this should work, but still I wouldn't create the Odin share and then three more shares inside it. Either have only the Odin share and then you can browse to any subfolder as needed, or have the three shares and delete the Odin share. Not one within another.

But for a quick test, leave them be right now. Lets test with your test share (at the end of the smb.conf). From the test share definition remove the force user = odin. Also in the global section, switch the security = user option to security = share. Restart the smbd and nmbd services.

Try to mount the //192.168.1.200/test as guest. See if that works out.

Also, you should clear out your smb.conf a bit. No need to leave all those default options and comments if you are not using many of them. You can still keep an original copy of the file, but the smb.conf should be little bit cleaner so that you can spot things much more easily. But that is also not relevant right now, leave it for later...

Try the above test and let us know.

---

### Post by perrti02 on 2016-02-13
I have made the changes as specified with no change. The output is as follows:

```
root@plex:/etc/samba# mount -vt cifs //192.168.1.200/test /mnt -o guest
mount.cifs kernel mount options: ip=192.168.1.200,unc=\\192.168.1.200\test,user=,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

---

### Post by darkod on 2016-02-13
It shouldn't be the issue but just to check linux file permissions post the output of:
```
cd /srv/samba
ls -l
```

---

### Post by perrti02 on 2016-02-13
Output as follows:

```
odin@odin:/srv/samba$ ls -l
total 16
drwxrwxrwx 1 root root 186 Dec  6 20:36 Odin
```

---

### Post by MAFoElffen on 2016-02-13
But there is some initial problems and limitations... Let me download his smb.conf to an editor and comment what I see there... Then I'll test it from there in one of my VM's.

Wait one... I'll post soon.

---

### Post by MAFoElffen on 2016-02-13
Here's the first problem, You have:
```

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
   hosts allow = 192.168.1. 127.

```
If 192.168.1.127 is the node you are trying to connect from, you have a typo there, which in essence, is saying to restrict all access to just that invalid IP address. At the moment, the shares are locked down to no valid access. Either comment the hosts allow line out (you have user passwords enabled) or change that to 
```

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
   hosts allow = 192.168.1.127

``` 
More recommendations to follow, but that should get you going for now.

---

### Post by bab1 on 2016-02-13
> **MAFoElffen said:**
> Here's the first problem, You have:
```

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
   hosts allow = 192.168.1. 127.

```
If 192.168.1.127 is the node you are trying to connect from, you have a typo there, which in essence, is saying to restrict all access to just that invalid IP address. At the moment, the shares are locked down to no valid access. Either comment the hosts allow line out (you have user passwords enabled) or change that to 
```

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
   hosts allow = 192.168.1.127

``` 
More recommendations to follow, but that should get you going for now.
Nah...

It's good that way he had it.  It is the segment of 192.168.1 and the segment of 127. (i.e. his local LAN and loopback)

[COLOR="#0000FF"]Edit: Of course the default is nothing which allows all IP addresses.  Just comment out the line.[/COLOR]

---

### Post by perrti02 on 2016-02-13
I have now commented out the hosts allow line but it still doesn't work. Worth a try though.

---

### Post by MAFoElffen on 2016-02-13
I only see two other things... Try commenting out 
```

wins support = yes

```
And add
```

name resolve order = bcast host lmhosts wins

```
Other than that... Wait...
You say 
```

encypt passwords = yes

```
But nothing else..

Although, I do pam and you are different, look at the first comments in mine:
```

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


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

```

---

### Post by darkod on 2016-02-13
Just a reminder, you are restarting the samba services (which should be smbd and nmbd) after each modification of the smb.conf, right?

This issue you have is very strange and in your place I would strip dosn the smb.conf completely. Samba actually needs very few basic settings for basic sharing. After that works, you can start adding up "more complex" options...

This is what I would comment out (I am going by your posted smb.conf, you already commented some options that we mentioned):
```
hosts allow
security = user (actually in the new smba I don't think you need security = share, just comment out security = user)
encrypt passwords
local master
preferred master
wins support
```

I hope that could get you going. In the share definition just use:
```
[test]
   path =
   guest ok = yes
   read only = no
```

Also, another thing... The samba password you mentioned for user odin is the same as the linux password, right? But in the above case we are trying to make it work as guest user anyway...

Also, please post samba version:
```
samba -V
```

This is because there are small differences between samba3 and latest samba4.

---

### Post by MAFoElffen on 2016-02-13
+1 with Darkod.

if you say security = user, then you have to set up how that works beyond the default. You started by saying passwords are encrypted, but did not say by what system and the details of that (as I posted from mine). On Wins support, that is pre-XP. We are talking netbios, 2k, Win Server 2003. Even Microsoft says that is not needed anymore on their own servers. Many of my colleagues say, turning that option on causes problems with theirs.

On the name resolve order I posted. That was a change a few years ago that fixed mount errors, when something about that time changed the previous default order from working.

On "local master"??? idk. I don't use that option at all, so idk.

---

### Post by bab1 on 2016-02-13
> **darkod said:**
> Just a reminder, you are restarting the samba services (which should be smbd and nmbd) after each modification of the smb.conf, right?

This issue you have is very strange and in your place I would strip dosn the smb.conf completely. Samba actually needs very few basic settings for basic sharing. After that works, you can start adding up "more complex" options...
...

This is because there are small differences between samba3 and latest samba4.
+1 on the simple sharing setup with Samba.

A couple of things to note for the OP.  By *default the security setting is [I]security = users*.  It doesn't need to be listed in the smb.conf file at all.  When restarting Samba you only need to start the smbd daemon.  The daemon rereads the smb.conf file and picks up the changes.

If you are using Samba as a standalone file server only then the default smb.conf file with only the share added at the bottom is all you need for Ubuntu and Windows file sharing (from XP to Win10).

I'm with Darko, replace the modified smb.conf file with the default smb.conf file and add the one share.  Test and report back.

---

### Post by perrti02 on 2016-02-14
I have overwritten the smb.conf I had with the default and simply added the share [test] at the bottom. The file now reads

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


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


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


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
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
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
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


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


[test]
   comment = All files on Odin
   path = /srv/samba/Odin
   browseable = yes
   read only = no
   guest ok = yes



```

This still gives the same results when trying to mount the test share as guest. 

My samba version is 4.1.6-Ubuntu

The samba password for Odin is not the same as the login password. I had issues with my password since it has an ! in it but if it needs to be the same I can change it to test. However, mounting as guest still doesn't work.

---

### Post by MAFoElffen on 2016-02-14
for guest, in [test], try adding this line
```

force user = Odin

```
that would assign that users permissions as the default user of that share, and not violate underlying Linux user permissions. Guest is defaulted to nobody nobaody has no permissions as a default. Your share directory, user nobody does not have permissions there... so that would get around that. Unless your set permissions of that to allow nobody as a user, access to that... so trip the last bit on the permissions to allow. So in the model user/group/world, you set the permissions for world.

Another method would be to go to a terminal and change the group permissions of the specific directory of that share for the group "sambashare"... I just did this in a VM test... sand if I change a directory to that group permission with chmod, then it doesn't even have to be defined in smb.conf ... and it shows up as browseable in smbclient through network browse from a desktop client. So like was said previously, if you create a group... and that group to the permission of that specific directory, then a user how is a meber of that group would have those permissions.

---

### Post by perrti02 on 2016-02-14
I have added this to the share but no change. As I understand it, the permissions on the directory are already set to allow everyone to do everything (777). Is it worth trying to change any permissions or will this not affect anything?

---

### Post by MAFoElffen on 2016-02-14
No. Samba permission can add restriction to, but not add access to what is closed by Linux permissions. So if 777, is already open to the world/everyone.
```

sudo chmod -R 777 /srv/samba/Odin

```
would open that directory to the world

Samba's doc's says changing this line to
```

[global]
 guest account = samba_guest
 map to guest = bad user

```
Will give authentication to any user in your Samba password database that it can still authenticate, as long as the username and credentials used is correct.

---

### Post by bab1 on 2016-02-14
> **MAFoElffen said:**
> No. Samba permission can add restriction to, but not add access to what is closed by Linux permissions. So if 777, is already open to the world/everyone.

But the user must have permissions all the way down the path to the shared folder.  From /srv on.

---

### Post by perrti02 on 2016-02-14
I have set the permissions for /srv as 777 all the way through. I have also added the line "guest account = samba_guest" to smb.conf but there is no affect.

Am I right in understanding that Samba is trying to authenticate with any user that is allowed but still failing? If so, does that mean that I have no valid samba users?

---

### Post by MAFoElffen on 2016-02-14
But I thought you said the "Odin" user gets permission, right? But guest did not?

Did your last post say that no one does?

---

### Post by perrti02 on 2016-02-14
Before changing the smb.conf I could mount the share from the server (i.e. on 192.168.1.200 I would run "sudo mount -t cifs //192.168.1.200/test /mnt -o user=odin,password=password" and it would successfully mount) but if I ran it from the client it would fail to mount with permission denied. Exactly the same command but from a different machine.

I have just tried it now and mounting from the server gives the error "Unable to find suitable address". The client machine still gives the permission denied message.

---

### Post by MAFoElffen on 2016-02-14
So what if you try this:
```

sudo chown -R :sambashare /srv/samba

```

---

### Post by bab1 on 2016-02-14
> **perrti02 said:**
> I have set the permissions for /srv as 777 all the way through. I have also added the line "guest account = samba_guest" to smb.conf but there is no affect.

Am I right in understanding that Samba is trying to authenticate with any user that is allowed but still failing? If so, does that mean that I have no valid samba users?
What did you do to create this account (samba_guest)?  By default the user is named **nobody**.  That user is a Linux user```
getent passwd nobody
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
```
Is samba_guest a Linux user?

---

### Post by MAFoElffen on 2016-02-14
Typically "noboby" or another generic user account that you setup just for a generic samba user. For instance, I do not have guest accounts active on my machines.

---

### Post by perrti02 on 2016-02-15
I have had a look at a few things and discovered that smbd isn't actually running and I am unable to get it to start. Every time I run "sudo service smbd restart" or "sudo /etc/init.d/smbd start" or variations on that the syslog output is 

```
Feb 15 08:26:32 odin kernel: [35067.232824] init: smbd main process (28076) terminated with status 1Feb 15 08:26:32 odin kernel: [35067.232837] init: smbd main process ended, respawning
Feb 15 08:26:32 odin kernel: [35067.261116] init: smbd main process (28080) terminated with status 1
Feb 15 08:26:32 odin kernel: [35067.261128] init: smbd main process ended, respawning
Feb 15 08:26:32 odin kernel: [35067.289430] init: smbd main process (28084) terminated with status 1
Feb 15 08:26:32 odin kernel: [35067.289442] init: smbd main process ended, respawning
Feb 15 08:26:32 odin kernel: [35067.317750] init: smbd main process (28088) terminated with status 1
Feb 15 08:26:32 odin kernel: [35067.317761] init: smbd respawning too fast, stopped
```

and checking the status of smbd gives the following

```
odin@odin:~$ sudo service smbd status
smbd stop/waiting
```

Trying to google a solution to this and the only results I can find reference to are about samba not starting at boot. Most of the solutions seem to be to update Samba and it will fix itself, but my version is up to date and still misbehaving.

I am wondering if I should just start again with this server. It is running on fairly old hardware and I did set it up a while go before I had any idea what I was doing. It might be better to just reinstall the operating system.

---

### Post by darkod on 2016-02-15
It is usually enough to purge and reinstall only samba, but if you prefer reinstalling the whole OS, go for it.

Also, I wouldn't share /srv (and subfolders) or any similar system folder. Create a new mount point dedicated for shares and do it like that. That way you can control its permissions without messing with permissions on system folders. Sometimes the OS does not like that. For example, if you do 777 on your ssh key file, the ssh key authentication will stop working. That is just one example that comes into my mind right away.

I don't know how /srv will react to 777 and it is not good practice to do it. But you do not seem to want to listen to our advice... Keep your shares separate from the system folders. If you do want to modify/upload some files to a system folder, put it in the share first, then log in by ssh session and move it to the system folder.

---

### Post by MAFoElffen on 2016-02-15
LOL, I asked if is was accessible by anyone...

On sharing: This this where I agree with Darkod, and and not with something bab1 had said. I've been doing Unix since, '88, Linux Since '05... I know I have a lot of old habits, and some of them are ingrained... but... I also learn new things each day.

I agree with Darko, that /srv (itself) should not be shared to the world, which disagrees with bab1. What he said was just not clear and could be confusing...He had said that is needed to go all the way back up through parent /srv(?)... That is not specifically true.

Doc's say:
> /srv contains site-specific data which is served by this system.

  This main purpose of specifying this is so that users may find the location of the data files for particular service, and so that services which require a single tree for readonly data, writable data and scripts (such as cgi scripts) can be reasonably placed. Data that is only of interest to a specific user should go in that users' home directory. 

  The methodology used to name subdirectories of /srv is unspecified as there is currently no consensus on how this should be done. One method for structuring data under /srv is by protocol, eg. ftp, rsync, www, and cvs. On large systems it can be useful to structure /srv by administrative context, such as /srv/physics/www, /srv/compsci/cvs, etc. This setup will differ from host to host. Therefore, no program should rely on a specific subdirectory structure of /srv existing or data necessarily being stored in /srv. However /srv should always exist on FHS compliant systems and should be used as the default location for such data.

Distributions must take care not to remove locally placed files in these directories without administrator permission.

This is particularly important as these areas will often contain both files initially installed by the distributor, and those added by the administrator.

So I put smb and NFS shares there, that is what I was taught. I start the permission of admin groups from those subdirectories. Other subgroups from sub-directories of those.. But not the parent /srv, the big reason for that is /srv is also the default installation directory for webroot. 

I do not give permissions to the user "nobody", as anything beyond read-only to an un-accredited, and non-verified user makes me paranoid.

Then on permissions. I am careful on groups. Granting a group access to a directory is fine by me. Granting world access (77[COLOR=#ff0000]7[/COLOR]) is too much for /srv/smb/... but would be okay by me for something like /srv/smb/Public or /home/Public. But how permissions work between Linux and Samba. Precedence says Linux, Samba. I am more inclined to close off the world bit of permissions accept on controlled public containers. 

But again, that is just what my opinion is, and the best practices I was taught.

But another practice is to leave the /srv tree as readonly and to create another tree for shares...

---

### Post by bab1 on 2016-02-15
> **MAFoElffen said:**
> LOL, I asked if is was accessible by anyone...

On sharing: This this where I agree with Darkod, and and not with something bab1 had said. I've been doing Unix since, '88, Linux Since '05... I know I have a lot of old habits, and some of them are ingrained... but... I also learn new things each day.

I agree with Darko, that /srv (itself) should not be shared to the world, which disagrees with bab1. He had said that is needed to go all the way back up through parent /srv(?)... That is not true.

I never said that you should (or should not) "share" /srv.  I said the Linux permissions should allow the user r-X permissions at the very least from / on down to the shared directory.  The permissions are applied to /srv/<some_dir> and below, not just to <some_dir> or below.

---

### Post by MAFoElffen on 2016-02-15
@ bab1- I know you didn't. I just said what you said could be mistakenly misinterpreted by some .. and tried to save you some grief by anyone who might read it that way. I knew your intent and it was good. I get blindsided by that sometimes. (We are good.)

I saw you get blasted by someone in another thread ... by someone who took offense by them thinking you told them they couldn't do something... I knew what you meant, and felt your pain.

What some ask here is possible, but not what is good practice. Sometimes we just have to make them aware of both sides. Right?

I don't know everything... But if I don't, i try to find out about it. Luckily for me, I have enough resources here to find out a lot of things hands-on. And if I say something, I invite others to tell me if I am wrong or unclear.

---

### Post by perrti02 on 2016-02-15
@darkod, I tried purging and reinstalling but the problem remained. You say that I don't seem to want to listen to your advice but I have been trying to the best of my ability. I have been playing with these sorts of things for a while but I don't really understand them. If I have done things that contradict what you have suggested it is not because I am ignoring advice, it is because I simply misinterpreted what was said. I do wonder if this is part of the problem I am having. In my blind fumblings I may well have broken something that is now causing the problem. Trying to fix it is probably beyond me.

@MAFoElffen, at one stage I could access the share from the server but I was never able to access it from a Ubuntu client. Windows and OS X could access but now can't. Whatever is going on is beyond my understanding so starting afresh might be the only way I can get it working again.

All your help has been much appreciated.

---

### Post by darkod on 2016-02-15
Well, if you tried purging and if you suspect other things may have gone wrong too, a new clean install is probably the fastest way. It depends also if you have other stuff on this server that you would need to configure again after the clean install.

Otherwise, configuring only samba is very fast and should be easy...

PS. If you have important data on the main root partition, or on any partition, be careful when doing the new install not to delete it. Especially if you don't have it backed up. That's why usually on server I never keep data on the same root partition. That allows you to format and reinstall without destroying any data. You only need to configure again the services you are running on the server but the data is safe on its own partitions.

---

### Post by perrti02 on 2016-02-15
I am still playing around with it and it is back to where it was. It is looking like a problem with the client. I have a VM with a GUI which connects using the file browser without any issue but I have now tried two clients which don't have a GUI and neither work. If cifs-utils the only package that needs to be installed to mount the share?

---

