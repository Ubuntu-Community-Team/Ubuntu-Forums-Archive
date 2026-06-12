---
title: "Unable to ping Ubuntu IP or from all Windows PCs over home wireless LAN"
date: 2013-06-30
forum: Server Platforms
---

### Post by sasoki on 2013-06-30
Hello,

I have the following devices:

**Ubuntu 12.10**
hostname = ub
IP = 192.168.0.2

**Windows XP**
hostname = winxp
IP = 192.168.0.3

**Windows 7**
hostname = win7
IP = 192.168.0.5
________________

I use a Sky router (UK) to access broadband internet.
________________

I can access **winxp** and **win7** from **ub** (either through Connect to Server or Remote Desktop).

**[SIZE=5]My goal[/SIZE]**

I installed an Apache2 server on **ub** and want to access it from Windows devices over the WLAN. But this failed.

**[size=5]Some diagnostics[size=3]**

_In **ub**_

I can ping **winxp** and **win7** both by IPs and hostnames.

**While I'm connecting to [B]winxp** through Remote Desktop (rdesktop):[/B]

[INDENT]In **winxp**:

ping 192.168.0.2 [COLOR="#008000"]works [/COLOR]

ping ub [COLOR="#B22222"]fails[/COLOR] 
[/INDENT]

[B]However, when the remote desktop is disconnected, the Ubuntu device is inaccessible even with pinging IP:
[/B]
[INDENT]ping 192.168.0.2 [COLOR="#B22222"]fials[/COLOR][/INDENT]

**/etc/host**
[INDENT]
127.0.0.1       localhost                        
192.168.0.2    ub  
[/INDENT]

**I have samba installed and running**.

Also, the firewall is disabled.

[INDENT]sudo ufw status verbose
Status: inactive
[/INDENT]
**[SIZE=5]The questions are[/SIZE]**

Why I'm unable to access Ubunutu from Windows machines?

And how to make Apache accessible from any device attached to the network (even iPhone)?

Many thanks in advance!

---

### Post by chrisguk on 2013-06-30
I believe something fundamental could be wrong with your setup.  The way networking works is that if your machines are on the same subnet and network, then you should be able to ping them, regardless of OS as the use of ping is not OS specific.  You said that you have Samba running, did you create a workgroup in sambe too?  then also make sure the windows machines are part of the workgroup?

You say that you want all machines to access apache.  I believe what you are saying is you want all machines to access the content held under the webserver.  Again all machines should be able to access the IP 192.168.0.2 and you should get a web page stating that it works.  Do0es this happen for you?
[COLOR=#000000]

[/COLOR]

---

### Post by sasoki on 2013-06-30
Thank you for the prompt reply!

In my /etc/samba/smb.conf

# Change this to the workgroup/NT-domain name your Samba server will part of
        workgroup = MyWorkgroup

And this is the same used in Windows machines.

Apache is running ("It works") according to [http://localhost/](http://localhost/) in Ubuntu. But of course not accessible neither by IP nor hostname from other devices (but only with IP when rdesktop from Ubuntu to winxp is active).

---

### Post by chrisguk on 2013-06-30
Can you post your samba config?

Also can you do the following:

[FONT=Ubuntu Mono]sudo ufw enable 80
[/FONT][FONT=Ubuntu Mono]sudo ufw enable 443
[/FONT][FONT=Ubuntu Mono]sudo ufw enable 53

The try the ping again.  If that doesnt work.  Try:

[/FONT][FONT=Ubuntu Mono]sudo ufw disable

then ping again[/FONT]

---

### Post by sasoki on 2013-06-30
Thank you chrisguk

**ufw**

$ service ufw status
ufw stop/waiting

**iptables**

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


**My /etc/samba/smb.conf is**

============================BEGINNING OF FILE

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP
        force user = myusername

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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

	server role = domain controller
	username map = /etc/samba/smbusers
	security = user
	guest ok = yes
	guest account = myusername
[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

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

[sysvol]
	path = /var/lib/samba/sysvol
	read only = no

[netlogon]
	path = /var/lib/samba/sysvol/localdomain/scripts
	read only = no

;	local master = yes
	preferred master = yes

[Downloads]
	path = /home/myusername/Downloads
;	writeable = no
;	browseable = yes
	guest ok = yes

============================END OF FILE

---

### Post by darkod on 2013-07-01
Do you have the server on a static IP? Are you sure it didn't change from .2?

You have no firewall enabled, which is the one thing that could block the ping. But according to the ufw status and iptables -L there is no firewall enabled. Keep it like that while troubleshooting.

On the ubuntu server check the current IP and network config:
```
ifconfig
cat 7etc/network/interfaces
```

Accessing by hostname might depend on how DNS is set up on the home network. But pinging and accessing by IP should always work, unless you have the IP wrong.

---

### Post by sasoki on 2013-07-01
Thank you darkod.

The IP address is dynamic (i.e. set by the router), but I told the router to reserve this IP (and hostname) for Ubunut (using MAC address).

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:88:e3:cc:73:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 68:94:23:20:88:b5  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe20:88b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:745552 errors:129 dropped:0 overruns:0 frame:1109178
          TX packets:644774 errors:119 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:584428893 (584.4 MB)  TX bytes:120806916 (120.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15170810 (15.1 MB)  TX bytes:15170810 (15.1 MB)
```

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by darkod on 2013-07-01
Is that the whole content of /etc/network/interfaces? There should be more, the parts that control eth0 and eth1.

Can you post this from the ubuntu machine:
ping 192.168.0.3
ping 192.168.0.5
ping 192.168.0.1 (I assume this is your router)

Don't do any remote desktops, just try that. Also try from the windows machines:
ping 192.168.0.2

I don't understand the point connection by remote desktop from a machine your trying to make a server (ubuntu) into windows workstations/desktops. If you do use remote desktop, usually you would want to enter the other way around. But in any case, the remote desktop is a different topic, lets see what networking says first.

---

### Post by sasoki on 2013-07-01
Thank you very much for you support!
--
Yes, that's the whole content of  /etc/network/interfaces

**Ping from Ubuntu 192.168.0.2**
```

# Windows XP
~$ ping 192.168.0.3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.
64 bytes from 192.168.0.3: icmp_req=1 ttl=128 time=4.32 ms
64 bytes from 192.168.0.3: icmp_req=2 ttl=128 time=2.85 ms
64 bytes from 192.168.0.3: icmp_req=3 ttl=128 time=3.47 ms
64 bytes from 192.168.0.3: icmp_req=4 ttl=128 time=2.19 ms
64 bytes from 192.168.0.3: icmp_req=5 ttl=128 time=2.85 ms
^C
--- 192.168.0.3 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 2.195/3.140/4.328/0.721 ms

# Windows 7
~$ ping 192.168.0.5
PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_req=1 ttl=128 time=4.37 ms
64 bytes from 192.168.0.5: icmp_req=2 ttl=128 time=2.09 ms
64 bytes from 192.168.0.5: icmp_req=3 ttl=128 time=2.14 ms
64 bytes from 192.168.0.5: icmp_req=4 ttl=128 time=4.77 ms
64 bytes from 192.168.0.5: icmp_req=5 ttl=128 time=2.16 ms
64 bytes from 192.168.0.5: icmp_req=6 ttl=128 time=2.45 ms
64 bytes from 192.168.0.5: icmp_req=7 ttl=128 time=2.62 ms
^C
--- 192.168.0.5 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6008ms
rtt min/avg/max/mdev = 2.094/2.946/4.774/1.052 ms

# ruoter
~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.77 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.74 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.23 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=64 time=1.84 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=64 time=1.91 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=64 time=2.10 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=64 time=1.78 ms
^C
--- 192.168.0.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6010ms
rtt min/avg/max/mdev = 1.748/1.913/2.239/0.175 ms


```

**Ping from Windows XP 192.168.0.3**

(Note: I added Ubuntu hostname to Windows XP \etc\hosts)

```

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

:: to Router
C:\Documents and Settings\MyUserNameXP>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:

Reply from 192.168.0.1: bytes=32 time=33ms TTL=64
Reply from 192.168.0.1: bytes=32 time=55ms TTL=64
Reply from 192.168.0.1: bytes=32 time=78ms TTL=64
Reply from 192.168.0.1: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 78ms, Average = 41ms

:: to Ubuntu
C:\Documents and Settings\MyUserNameXP>ping 192.168.0.2

Pinging 192.168.0.2 with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 192.168.0.2:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

:: to Windows 7
C:\Documents and Settings\MyUserNameXP>ping 192.168.0.5

Pinging 192.168.0.5 with 32 bytes of data:

Reply from 192.168.0.5: bytes=32 time=7ms TTL=128
Reply from 192.168.0.5: bytes=32 time=1ms TTL=128
Reply from 192.168.0.5: bytes=32 time=1ms TTL=128
Reply from 192.168.0.5: bytes=32 time=2ms TTL=128

Ping statistics for 192.168.0.5:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 7ms, Average = 2ms


```

**Pinging from Windows 7 192.168.0.5**

```

Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

:: to router
C:\Users\Win7user>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:
Reply from 192.168.0.1: bytes=32 time=1ms TTL=64
Reply from 192.168.0.1: bytes=32 time=13ms TTL=64
Reply from 192.168.0.1: bytes=32 time=2ms TTL=64
Reply from 192.168.0.1: bytes=32 time=4ms TTL=64

Ping statistics for 192.168.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 13ms, Average = 5ms

:: to Ubuntu
C:\Users\Win7user>ping 192.168.0.2

Pinging 192.168.0.2 with 32 bytes of data:
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.
Reply from 192.168.0.5: Destination host unreachable.

Ping statistics for 192.168.0.2:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

:: to Windows XP
C:\Users\Win7user>ping 192.168.0.3

Pinging 192.168.0.3 with 32 bytes of data:
Reply from 192.168.0.3: bytes=32 time=6ms TTL=128
Reply from 192.168.0.3: bytes=32 time=1ms TTL=128
Reply from 192.168.0.3: bytes=32 time=2ms TTL=128
Reply from 192.168.0.3: bytes=32 time=1ms TTL=128

Ping statistics for 192.168.0.3:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 6ms, Average = 2ms

```

I'm not an expert, but I used remote desktop (rdesktop) from Ubuntu to WinXP just to test ping Ubuntu from WinXP while working from Ubuntu!

** **The strange thing is that my ubuntu is only pingable from a (Windows) device that is actively connecting to (either via rdesktop, or even with ping).** During such temporary 'connection', I can:
- ping Ubuntu from WinXP using IP
- ping Ubuntu from WinXP using hostname if I manually added Ubuntu IP to WinXP etc/hosts
- access Apache welcome page of Ubuntu from WinXP

When I ping my iPhone (192.168.0.4) from Ubuntu, I can access Apache on Ubuntu from iPhone.

[Telephone analogy: W can only talk to U when U initiates the call. Otherwise, W cannot reach U!].

---

### Post by sasoki on 2013-07-01
Also, in Ubuntu (not sure if useful):

```
$ nmcli dev list iface eth0 | grep IP4
$ nmcli dev list iface eth1 | grep IP4
IP4.ADDRESS[1]:                         ip = 192.168.0.2/24, gw = 192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          Home
```

Is it something related to domain?

---

### Post by darkod on 2013-07-01
That content of /etc/network/interfaces looks very wrong. Try to add this at the end:
```
auto eth1
iface eth1 inet dhcp
```

Don't forget to use eth0 instead of eth1 if you have the cable in the first network port.

After that restart networking on the server:
```
sudo /etc/init.d/networking restart
```

Also don't forget you need to edit the network file with sudo rights, it's a system file. See if that somehow helps. I'm confused since with that network config file, eth1 shouldn't even be up and running.

---

### Post by sasoki on 2013-07-01
Done

etc/networks/interface/
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

but Ubunutu won't boot :( Still saying "Booting system without full network configuration" for more than 5 minutes.

---

### Post by chrisguk on 2013-07-01
Have you resolved this issue because I just noticed something here:

```



eth0      Link encap:Ethernet  HWaddr b8:88:e3:cc:73:b7            UP BROADCAST MULTICAST  MTU:1500  Metric:1          RX packets:0 errors:0 dropped:0 overruns:0 frame:0          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)          Interrupt:16 eth1      Link encap:Ethernet  HWaddr 68:94:23:20:88:b5            inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0          inet6 addr: fe80::6a94:23ff:fe20:88b5/64 Scope:Link          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          RX packets:745552 errors:129 dropped:0 overruns:0 frame:1109178          TX packets:644774 errors:119 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:584428893 (584.4 MB)  TX bytes:120806916 (120.8 MB)          Interrupt:17 

```

The line on eth0 is missing IP information.  Do you actually have two network cards in the machine?

If you have two then place this code in your /etc/network/interfaces

```


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
	address [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.2[/FONT][/COLOR]
	broadcast [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.255[/FONT][/COLOR]
	netmask 255.255.255.0
	network [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.0[/FONT][/COLOR]
	gateway [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.1[/FONT][/COLOR]


auto eth1
iface eth1 inet static
	address [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.6[/FONT][/COLOR]
	broadcast [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.255[/FONT][/COLOR]
	netmask 255.255.255.0
	network [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.0[/FONT][/COLOR]
	gateway [COLOR=#000000][FONT=Ubuntu Mono]192.168.0.1[/FONT][/COLOR]




```

Reboot the machine or if a server installation issue the following:

```


sudo service networking restart


```

---

### Post by sasoki on 2013-07-02
Thanks chrisguk. Unfortunately this didn't help and cause no networking at all. It is an Acer Aspire laptop with wireless and wired cards, both are enabled, but I only use the wireless to connect.

Can you please explain the 'strange' behavior mentioned at the end of this previous comment?

[http://ubuntuforums.org/showthread.php?t=2158731&p=12713569#post12713569](http://ubuntuforums.org/showthread.php?t=2158731&p=12713569#post12713569)

---

### Post by darkod on 2013-07-02
For wireless I think you need additional parameters in /etc/network/interfaces related to the wi-fi setup (SSID, password, etc). But I haven't looked into the details since I have never tried to connect a server on a wireless.

Try connecting it by cable at least temporarily, to see if it works. Of course, don't forget to either set a static IP on the wired interface, or if you are doing it by router resevation use the correct wired MAC (now you are probably using the wi-fi MAC for the reservation).

In general, I would avoid connecting a server by wi-fi. If you can stuck the laptop somewhere close to the router and have it connected by cable, much better.

---

### Post by chrisguk on 2013-07-02
Replace eth1 with wlan and see what that does.  Also give the wlan the IP address you want.  You can change eth0 to dhcp if you are using wifi.  But as dark said cable is better.

---

