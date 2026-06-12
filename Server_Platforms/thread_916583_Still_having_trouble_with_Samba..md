---
title: "Still having trouble with Samba."
date: 2008-09-11
forum: Server Platforms
---

### Post by grs on 2008-09-11
I've being messing about with /etc/samba/smb.conf and I think I still have to setup samba users and passwords. 

When I type sudo pdbedit -L -v I get a list showing the one user on the server, is this the same user I setup when installing Ubuntu Server? (I've trying so may things now I've lost track of 
what I've done!!) If not, how do I create samba users and passwords and then give those users access to`the directories I have added to samba, with permissions to read, write and run (execute?) the files.

So far, on Windows Explorer, I can see the server unser Network Places but when I try to access it 
I get an access denied message saying I need permissions.

I've read through man pdbedit but I'm still lost.

---

### Post by kamaji792 on 2008-09-11
Have you done:
```
sudo smbpasswd -a <user_name>
```
You will be then asked to set a password.  

If the user_name and password are the same as what you use to log on to your windows box you should be able to connect without having to enter a user name and password.  If not, when you click on the share, you will have to enter the user_name and password.

All the best

---

### Post by grs on 2008-09-11
> **kamaji792 said:**
> Have you done:
```
sudo smbpasswd -a <user_name>
```
You will be then asked to set a password.  

If the user_name and password are the same as what you use to log on to your windows box you should be able to connect without having to enter a user name and password.  If not, when you click on the share, you will have to enter the user_name and password.

All the best

I've just used the command above to create a user, its the same name as the one I user to log onto Ubuntu Server but slightly different to that on Windows.
When I went Windows Explorer it still tells me I don't have permissions to access the storage server.

---

### Post by kamaji792 on 2008-09-11
If the ubuntu and windows user names are not the same I guess you will not get a home share.  So I guess you need to create a share.

Try adding the following to the samba configuration file (/etc/samab/smb.conf)

```
[public]
   path = /usr/somewhere/else/public
   public = yes
   writable = yes

```

The **path** variable needs to point to the directory you want to share on the ubuntu  box.

Good luck.

---

### Post by grs on 2008-09-11
That didn't make any difference. Below is what I have for one of the directories I want to sharing. I copied it from a pervious storage server I had setup, that setup did everything for me through a GUI.
What should the Global setting in the smb.conf file look like?

```


[Films]
comment = Feature Films
path = /mnt/films
writable = yes
public = yes
guest only = yes
browseable = yes
read only = no
valid users = grs
write list = grs


```

---

### Post by bab1 on 2008-09-11
I suggest reading  [[COLOR="Red"]**Samba3 by Example**[/COLOR]]("http://us1.samba.org/samba/docs/man/Samba-Guide/").  The examples cover all types of installations.  It describes very basic to complex domain wide installations.

---

### Post by Krupski on 2008-09-11
> **grs said:**
> I've being messing about with /etc/samba/smb.conf and I think I still have to setup samba users and passwords.

IF you want Windows users to be able to access Samba shares WITHOUT restriction, passwords or Unix accounts, use the following Samba config:

```

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
# [COLOR="Red"]**WARNING! THIS CONFIGURATION OFFERS NO SECURITY!**[/COLOR]
# [COLOR="Red"]**USE ONLY IF YOU TRUST ALL USERS ON YOUR NETWORK!**[/COLOR]
#
#======================= Global Settings =======================

[global]
        server string = Storage Drive
        security = SHARE
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        os level = 65
        preferred master = Yes
        wins support = Yes
        create mask = 0644
        directory mask = 0755
        guest ok = Yes
        store dos attributes = Yes
        dos filemode = Yes

[shared]
        comment = storage
        path = /home/shared
        read only = No


```


Obviously, edit share names and comments as appropriate.

---

### Post by grs on 2008-09-11
You've given me a lot to read through and try. I'll get back to you when I try a few things, in a couple of days.

Below is the sample smb.conf file that comes with Ubuntu Server. Do I need the following section or can they be deleted?
I'm not useing this as a print server, don't own a printer!!

Networking
Debugging/Accounting
Printing
Misc
Domains

I guess I need Authentication if I want users to have to login.


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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom



```

---

### Post by grs on 2008-09-12
Krupski

I stuck in the code you suggested with nothing else in the smb.conf file and it made no difference.

bab1

I followed The No-Frills Samba Servers guide from the link, again no difference

When I tried the below code, it just came back that it didn't know the command

```

root#  chkconfig smb on
root#  /etc/rc.d/init.d/smb restart

```

And when I tried to verify I got

```
 
# smbclient -L ubuntu -U%
# Error connecting to 192.168.1.106 (Connection refused)
# Connection to ubuntu failed (Error NT_STATUS_CONNECTION_REFUSED)

```

Anyone got ideas? Is it possable there is some security setting somewhere else that could be causing it not to connect?

---

### Post by bab1 on 2008-09-12
My bad.  I'm sorry.  I forgot that the installation was for RedHat.  I assumed (again my fault) that you had Samba and smbfs installed.  The guide should be used [COLOR="Red"]**only**[/COLOR] for the configuration of Samba.

```
root#  chkconfig smb on [COLOR="Magenta"]<-- RH09 command[/COLOR]
root#  /etc/rc.d/init.d/smb restart<--  [COLOR="Blue"]/etc/init.d/samba restart[/COLOR]
```

The restart command is in blue.

At this point lets see if you have anything shared.  Try this command ```
smbtree
```  Post the results here.

---

### Post by kamaji792 on 2008-09-15
I had a quick look at the sample smb.conf file.  I'd try uncomenting the following line:
```
;   security = user
```
i.e. delete the ';' at the start of the line.

I use the sample file and just add my share at the end.

All the best

---

### Post by grs on 2008-09-15
i'm extremely busy at the moment and have not being able to get near my PC. I will look at it again as soon as I can and let you know how I get on.

---

### Post by promodus on 2008-09-15
An easy tool if you're relatively new to samba

[gsambad]("http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=16&Itemid=30") 

Can be installed directly via apt-get install gsambad or part of the gui admin tools package gadmintools

---

### Post by grs on 2008-09-16
gsambad looks as though it needs to run from a desktop gui - Ubuntu Server is terminal based

---

### Post by grs on 2008-09-16
> **kamaji792 said:**
> I had a quick look at the sample smb.conf file.  I'd try uncomenting the following line:
```
;   security = user
```
i.e. delete the ';' at the start of the line.

I use the sample file and just add my share at the end.

All the best

I just tried what you suggested and now Windows Explorer will not let me see the PC's on MSHOME!!

---

### Post by promodus on 2008-09-16
> **grs said:**
> gsambad looks as though it needs to run from a desktop gui - Ubuntu Server is terminal based

Desktop & Server share the same repositories.
You don't need to run it from a desktop gui. (and by run, I mean execute)
You can X Forward the app somewhere else.
Ubuntu server is not restricted as a "server" nor is the desktop version restricted to a "desktop." They're the same base just different roles, you can mix and match softwares and do whatever you want with it.

---

### Post by kamaji792 on 2008-09-16
> **grs said:**
> I just tried what you suggested and now Windows Explorer will not let me see the PC's on MSHOME!!

Is the client PC in the same Workgroup as the server?

---

### Post by grs on 2008-09-16
yes

---

### Post by kamaji792 on 2008-09-17
I assume that client and server are on the same sub-net?

Is there any chance there is a Firewall getting in the way?

Can you ping from client to sever and back?

Lastly for the moment.  Below is the output of **testparm** on a server that is working fine:
```

[global]
	workgroup = WORKGROUP
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[Data]
	path = /srv/Samba/Data
	invalid users = root, admin
	valid users = user1, user2
	read only = No
	create mask = 0775
	directory mask = 0775

```
If it is any consolation I have had lost of fun the past getting samba to run.  These days it seem to be easier :P

---

### Post by grs on 2008-09-18
Yes, client and server are on the same subnet.

Since I installed Ubuntu Server I have never touched the firewall settings, how do I edit them? Should I just turn it off althogether?

The server can ping the client and the client can ping the server.

I will try and transfer some of those testperm results into my smb.conf file in the next few days.


I'm still getting my head around Linux/Samba, I've used linux storage server packages before but they had a gui and therefore there was a lot going on in the background that I never saw!

---

### Post by kamaji792 on 2008-09-19
> **grs said:**
> Since I installed Ubuntu Server I have never touched the firewall settings, how do I edit them? Should I just turn it off althogether?

Unless you told ubuntu to start a firewall it will not have started one.  You can confirm this with the command:

sudo iptables -L

With no firewall up I get:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

All the best for now.

---

### Post by grs on 2008-09-19
I got the same reply as you from my server. The firewall is off.

---

### Post by grs on 2008-09-19
> **kamaji792 said:**
> I assume that client and server are on the same sub-net?

Is there any chance there is a Firewall getting in the way?

Can you ping from client to sever and back?

Lastly for the moment.  Below is the output of **testparm** on a server that is working fine:
```

[global]
	workgroup = WORKGROUP
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[Data]
	path = /srv/Samba/Data
	invalid users = root, admin
	valid users = user1, user2
	read only = No
	create mask = 0775
	directory mask = 0775

```
If it is any consolation I have had lost of fun the past getting samba to run.  These days it seem to be easier :P

I've just tried to use the same settings you have but I still get invalid permissions error when I try to access with Windows Explorer. I though I was supposed to be asked for a password?

---

### Post by kamaji792 on 2008-09-19
> **grs said:**
> I've just tried to use the same settings you have but I still get invalid permissions error when I try to access with Windows Explorer. I though I was supposed to be asked for a password?

I was going to try and replicate your problem and I have just created a share on my home server.  Interestingly the server and client (winXP) are in different workgroups but I can still use the server (they are on the same network subnet though) :P

In windows explorer I open:
> 'My Network Places'
> 'Microsoft Windows Network
> 'TheWorkgroup'
> 'SambaServer'

When I click on the 'SambaServer' I get a little log-on window.  You will not get a log on window if the samba and windows users are the same.  i.e. the **user name** and **password** are the same.

Once I have logged into the server I can see all the shares.

The test I wanted to carry out was I set the directory used for the sare so only 'root' could access it.  Now when I use windows explorer to enter the new share I get a message that starts:
"\\SambaServer\ShareName is not accessible. You might..."

So you need to make sure that the user (under Linux) has at least read permissions.

Note what the permissions are on the directory under Linux and then set them to allow anyone to read or write the directory:

sudo chmod 0777 /path/to/share

Good luck

PS - Though I could access the share when the Linux box had the wrong workgroup name it did not seem to be reliable.  Setting it to the same workgroup as the winXP box made life a lot more stable. :/

---

### Post by kamaji792 on 2008-09-19
While you are at it just try the following:

**ps aux | grep nbd**

This will show us if the samba deamons are running, I expect the are.  This is what it looked like on my setup:
```
ps aux | grep mbd
root      4582  0.0  0.2   7508  1264 ?        Ss   20:43   0:00 /usr/sbin/nmbd -D
root      4584  0.0  0.4  11172  2336 ?        Ss   20:43   0:00 /usr/sbin/smbd -D
root      4587  0.0  0.1  11172  1004 ?        S    20:43   0:00 /usr/sbin/smbd -D
root      4588  0.0  0.7  11480  3668 ?        S    20:44   0:00 /usr/sbin/smbd -D
gavin     4613  0.0  0.1   3004   756 pts/0    R+   21:12   0:00 grep mbd
```

Now try the following:

**netstat -al**

Again on my system the first lot of lines are (I don't understand the active Unix domain sockets):

```
$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp        0      0 server.local:netbios-ssn 192.168.0.4:1568        ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 server.localhost:ssh     192.168.0.4%8191:1511   ESTABLISHED
udp        0      0 server.localh:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 server.local:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*

```

netbios-sn  - Port 137 - Netbios Name service.
netbios-ds  - Port 445 - Microsoft Naked CIFS.
netbios-ssn - Port 139 - Netbios session service
netbios-dgm - Port 138 - Netbios Datagram Service

Those are all the ports that samba uses.

If these are OK it will be looking at the logs and I have never done that.

Good luck

---

### Post by bab1 on 2008-09-19
@kamaji792,

> I don't understand the active Unix domain sockets

Unix domain sockets are internal to the host.  It's how the host communicates to itself.

To see only the TCP/UDP ports try ```
>sudo netstat -plntu
```

This will get the following:```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:901             0.0.0.0:*               LISTEN     4531/inetd          
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4564/smbd           
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4480/cupsd          
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4564/smbd           
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          4436/avahi-daemon:  
udp        0      0 192.168.1.12:137        0.0.0.0:*                          4562/nmbd           
udp        0      0 0.0.0.0:137             0.0.0.0:*                          4562/nmbd           
udp        0      0 192.168.1.12:138        0.0.0.0:*                          4562/nmbd           
udp        0      0 0.0.0.0:138             0.0.0.0:*                          4562/nmbd           
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          4436/avahi-daemon: 

```

---

### Post by grs on 2008-09-20
ps aux | grep nbd gives:

```

grs  4947  0.0  0.0   5164   836 pts/0    S+   09:26   0:00 grep nbd

```

netstat -al gives:

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0    132 ubuntu:ssh              192.168.1.103%3717:2645 ESTABLISHED
udp        0      0 ubuntu:netbios-ns       *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 ubuntu:netbios-dgm      *:*
udp        0      0 *:netbios-dgm           *:*
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     11708    /tmp/.winbindd/pipe
unix  5      [ ]         DGRAM                    11560    /dev/log
unix  2      [ ]         DGRAM                    6195     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    6343     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     11710    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     11489    /var/run/acpid.socket
unix  2      [ ]         DGRAM                    12181
unix  2      [ ]         DGRAM                    11778
unix  3      [ ]         STREAM     CONNECTED     11775
unix  3      [ ]         STREAM     CONNECTED     11774
unix  3      [ ]         STREAM     CONNECTED     11713
unix  3      [ ]         STREAM     CONNECTED     11712
unix  2      [ ]         DGRAM                    11602


```

The share now has the following details, I have tried a number of variations with no luck, should the masks be set to 0777 I did try that:

```

[TV]
comment = TV Shows
path = /mnt/TV
invalid users = root, admin
valid users = grs
read only = No
create mask = 0775
directory mask = 0775


```

I'm still not getting asked for a password in Win Explorer, my Windows and Ubuntu users are the same. I( can see the Server but not its shares. I have had other storage servers on the network before in the form of FreeNAS and Clarkconnect, they both asked my for a password when I first tried to connect.

---

### Post by kamaji792 on 2008-09-22
Your shares look fine to me.

If your Windows and ubuntu accounts are the same (user name and password) then Samba should let you in without asking for a password.

The output of the grep command makes it look like samba is not runnig.

What output do you get from:

**sudo /etc/init.d/samba restart**

There should be 2 lines with "[OK]" at the end of them.  The first line telling you it is turning the samba off and the second telling you it has turned it back on.

I'm hoping that you don't get an OK on the first line and then an OK on the second line, meaning that it has now turned samba on.

I'm sure there is a log file to see if Samba is getting turned on, at boot time, but I don't know which one it would be.

All the best.

PS - Thanks **bab1** I knew there must be a way of stopping the Unix socket output on netstat, but could not work it out for myself - you have been thanked :)

---

### Post by HermanAB on 2008-09-22
Here is a Samba debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

It sounds to me like your file permissions are wrong - nothing to do with Samba.  If you share files amongst multiple users, then you need to create a group and manage the permissions that way, or make everything wide open with "chmod -R 777 /wherever/samba/data/is".

Cheers,

Herman

---

### Post by grs on 2008-09-22
> **HermanAB said:**
> Here is a Samba debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

It sounds to me like your file permissions are wrong - nothing to do with Samba.  If you share files amongst multiple users, then you need to create a group and manage the permissions that way, or make everything wide open with "chmod -R 777 /wherever/samba/data/is".

Cheers,

Herman


That is what I suspected alright. I'll have a read through the guide and see what I can come up with. I have tried a few things with chmod but have not tried using -R part of the command.

---

### Post by grs on 2008-09-23
How do I make a samba group and then place a user into that group? After reading the debug guide that is the only thing I have try.
If that does not work I'm going back the pervious storage server I was using.

---

### Post by kamaji792 on 2008-09-23
Keep me happy and post the output of:

**sudo /etc/init.d/samba restart**

I still suspect the samba deamons are not running.

In the mean time I will look in to what I did with groups.

---

### Post by kamaji792 on 2008-09-23
***WARNING***
What I am writing is what I belive I did to get my system to work.  The paritcular problem I had was several users using the share but I wanted everyone to be able to access each others files.  I believe this could also have been achieved with **force user** option in the smb.conf file.
Additionally check the man entries for the commands.

To create a "samba" group (you can chose any name you like so lone as it does not exist):

**sudo groupadd samba**

Append the group to user "jim":

**sudo usermod -a -G samba jim**

Set the "samba" group as the default:

**sudo usermod -g samba jim**

Now we need to change the shares so they all allow full access to the group **samba**.

**sudo chown -R :samba /path/to/samba/share**

Finally we need to set all the files and directories to be editable by the samba group:

**sudo chmod g+rwx**

Hope that works for you.

---

### Post by grs on 2008-09-24
**sudo /etc/init.d/samba restart** gave the following:

```


 * Stopping Samba daemons                                                                                                                                                                            start-stop-daemon: warning: failed to kill 4668: No such process
                                                                                                                                                                                              [ OK ]
 * Starting Samba daemons             


```

With the groups, I thinkI tried adding force user to smb.conf with no effect, it went fine till I got to
**sudo chmod g+rwx** it said 
[B]chmod: missing operand after `g+rwx'
Try `chmod --help' for more information.
[/B]
Did I leave out something?

---

### Post by kamaji792 on 2008-09-24
> **grs said:**
> 
With the groups, I thinkI tried adding force user to smb.conf with no effect, it went fine till I got to
**sudo chmod g+rwx** it said 
[B]chmod: missing operand after `g+rwx'
Try `chmod --help' for more information.
[/B]
Did I leave out something?
Oops...

My error, missing the **-R** to go through subdirectories and the path to the share.  It should have been:

**sudo chmod -R g+rwx /path/to/samba/share**

Looking at the output of the re-start command something is not happy if it fails to stop the samba deamons.

I notice I also got another command wrong.  To check if the samba deamons are running it should be:

**ps aux | grep mbd**

You should get one line of output for **nmbd** and then a **smbd** for each connection to the server. Like:
```

$ ps aux | grep mbd
root      4526  0.0  0.2   6528  1356 ?        Ss   09:06   0:00 /usr/sbin/**nmbd** -D
root      4528  0.0  0.4  10104  2520 ?        Ss   09:06   0:00 /usr/sbin/**smbd** -D
root      4542  0.0  0.2  10104  1032 ?        S    09:06   0:00 /usr/sbin/**smbd** -D

```

All the best

---

### Post by grs on 2008-09-24
ps aux | grep mbd

Gave the following output:


```

root      4985  0.0  0.0  54972  1400 ?        Ss   08:39   0:00 /usr/sbin/nmbd -D
grs  5057  0.0  0.0   5164   832 pts/0    S+   21:22   0:00 grep mbd

```

I still had no luck. I think I should try to reinstall Ubuntu, I've always had some trouble getting to install. That is sometime it will get half way others three quater way through then stops, other time it get the whole way through then the PC won't boot up. I had similar problems with Ubuntu Studio when I tried to install it at first.

---

### Post by kamaji792 on 2008-09-24
OK.

Well at least looking at your last post the **nmbd** (NetBios daemon is running).

Hope you have better luck next time.

---

### Post by plonka2000 on 2008-09-24
Just my 0.02c...

Try webmin:

```
[COLOR="DeepSkyBlue"]**edit /etc/apt/sources.list**[/COLOR]
#nano /etc/apt/sources.list

[COLOR="DeepSkyBlue"]**add the following line:**[/COLOR]
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib

[COLOR="DeepSkyBlue"]**INSTALL Webmin**[/COLOR]
#apt-get install webmin
```

After faffing with samba for days myself, I installed Webmin (For other Administration reasons) and it works a treat to configure samba.

The only other thing I had to do was:
```
sudo smbpasswd -a <user_name>
```

AND THEN AFTER THAT, I could access webmin from a browser using:
http://<server_ip>:10000 (Remote)
[http://localhost:10000](http://localhost:10000) (Local)

Webmin works a charm for SMB config, among *_**hundreds**_* of other things.

---

### Post by kamaji792 on 2008-09-25
> **grs said:**
> 
I still had no luck. I think I should try to reinstall Ubuntu, I've always had some trouble getting to install. That is sometime it will get half way others three quater way through then stops, other time it get the whole way through then the PC won't boot up. I had similar problems with Ubuntu Studio when I tried to install it at first.

Commiseration on the install problems.  I have found Ubuntu to be one of the easier systems to install, with the exception of the disk partitioning but I am getting there.

I just checked my system this morning (back to **ps ax | grep mbd** this was the output with no windows boxes connected:

```
$ ps ax | grep mbd
 4359 ?        Ss     0:00 /usr/sbin/nmbd -D
 4361 ?        Ss     0:00 /usr/sbin/smbd -D
 4375 ?        S      0:00 /usr/sbin/smbd -D
 4511 pts/0    R+     0:00 grep mbd

```

The upshot of which is it looks like you should have 2 **smbd** daemons running even if there are no windows boxes connected to the server.

It might be worth trying to launch them from the command line to see if you can see any errors being reported.

I turned my samba daemons off (**sudo /etc/init.d/samba stop**) and then did it manually as below, firstly starting the NetBIOS daemon:
```
**$ ps ax | grep mbd**
 4550 ?        Ss     0:00 /usr/sbin/nmbd -D
 4552 pts/0    R+     0:00 grep mbd

```
At this point I tried to connect to the server with my WinXP box but I could not browse the workgroup.  So I started a Samba daemon:
```

**$ sudo /usr/sbin/smbd -D**
**$ ps ax | grep mbd**
 4550 ?        Ss     0:00 /usr/sbin/nmbd -D
 4554 ?        Ss     0:00 /usr/sbin/smbd -D
 4555 ?        S      0:00 /usr/sbin/smbd -D
 4557 pts/0    S+     0:00 grep mbd

```
You can see the way that calling one Samba daemon from the command line starts 2.  Now I could browse the workgroup and connect to the server to use the sares:
```

**$ ps ax | grep mbd**
 4550 ?        Ss     0:00 /usr/sbin/nmbd -D
 4554 ?        Ss     0:00 /usr/sbin/smbd -D
 4555 ?        S      0:00 /usr/sbin/smbd -D
 4560 ?        S      0:00 /usr/sbin/smbd -D
 4562 pts/0    R+     0:00 grep mbd

```
See how, now I am connected, there is another Samba daemon running.

Any way all the best

---

### Post by borlosky on 2008-09-30
i'm having a different issue with samba, first needs some back story, i have 4 pc's, 2 that run strictly Win Xp, 1 that runs ubuntu, and the last running dual boot ubuntu 64bit/win xp 32 bit. the issue is with the dual boot pc, in windows, i can share folders with all other 3pc's, both linux and win just fine, but when i boot to ubuntu on the dual boot, none of the other pc's can access those shared folders, but the pc's can see the folders there. and at the same time, when the dual boot pc is booted into linux, all pc's are then unable to view shares on the stand alone linux box. but if i reboot back into win on the dual boot, i can access the shares on the linux only box just fine. sounds like something in the samba config, is preventing access to BOTH linux pc's somehow. (both linux pc's can still access the other 2 pc's windows shares fine however.)

---

### Post by kamaji792 on 2008-10-02
That sounds like a pretty weir problem borlosky.  I would start by checking **workgroups**, **ip addresses** but I am at a loos really to understand the problem.  Obvously check you can ping to and from all the relevant boxes and check any firewalls.

All the best.

---

### Post by borlosky on 2008-10-02
> **kamaji792 said:**
> That sounds like a pretty weir problem borlosky.  I would start by checking **workgroups**, **ip addresses** but I am at a loos really to understand the problem.  Obvously check you can ping to and from all the relevant boxes and check any firewalls.

All the best.

yea, i can still ping all pcs from any of the pc's fine, it's only an issue with accessing file shares. For instance, if both linux pc's are running, non of the other pc's can access any file shares on the only linux boxes, but the linux boxes can access the windows pc's fine, but if i shut down either of the linux pc's, all the other pc's can access the shared folders on all pc's (except for the pc thats shut down obviously). ....very weird issue, i'll check ip's though, but as far as i know there's no conflicts, since i can ping all pc's individually, and all pc's can still browse net, and can browse the windows pc's shares as well. also none of the pc's run any firewalls, i use a hardware firewall thru my router.

---

### Post by Llewxam on 2008-10-29
greets to all. i was about to post about my issue with no longer being able to view my windows shares. everything is set up as it was and after about 2 or 3 days ago stopped working. i can connect to the server but none of the shared folders show up. 
following some of the pointers in this thread i went to the samba debug howto and ran ```
smbclient -L //hal/ -N 
``` to which i got this in return ```
 smbclient -L //hal/ -N
Domain=[HAL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_OK
Domain=[HAL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

if that's of any help i would like to know how to fix this issue since i rely a lot on samba for transferring college projects and many other files.

---

