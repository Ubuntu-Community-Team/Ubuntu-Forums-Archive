---
title: "(possible) conflict with SAMBA and gigabit network"
date: 2011-08-20
forum: Server Platforms
---

### Post by Smi-Ling on 2011-08-20
Hi!

I have a problem with home network. After upgrading my the server form 9.10 to 10.04.3 LTS I also renewed all cables and installed a gigabit network card in the server and installed a new gigabit switch.

Resulting setup: full CAT-5E network & gigabit switch, UBUNTU 10.4.3 LTS server with Realtec RTL-8169 gigabit PCI network card; 2 WinXP SP3 workstations; server running SAMBA in PDM setup with roaming profiles.

This all resulted in very drastic speed DECLINE: old setup (100mb network), a 700mb file from server (Samba share) to WipXP clients: c.a. 2:30 min. New setup: over 180 minutes!!!
To narrow down te cause I did some experimenting. I found out that: when running everything with my old 100mb switch - speed are normal. Simply replacing the switch resulted in speeds compatible with a gigabit network. (700 mb test file transfer c.a. 25 seconds)

Conclusion (1): all hardware, the WinXP setups AND the new UBUNTU server are capable of running at gigabit speeds.

When I log-out my WinXP client and log back in: speeds declined to a dramatic crawl. BUT: transfering the same 700 mb file from the local drive of one workstation to the local drive of another: still c.a. 20 sec.

Conclusion: (2) Both WinXP workstations still run at gigabit speed; switch also. Problem is narrowed down to SAMBA  c.q. SAMBA shares.

This leads to the assumtion that SAMBA does something very wierd in the process of logging off and abck on of my workstations

I found numerous posts on speed problems with SAMBA and did the much discussed tinkering with the "socket options" line. All to no avail.

This is driving me mad! Who can help?????

---

### Post by CharlesA on 2011-08-20
Running 10.04.3 on gigabit with no reduction in speeds here. Can you post your smb.conf?

---

### Post by Smi-Ling on 2011-08-20
OK - here it is. Hope youcan find the problem here.

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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

# for symlinks in shares
   follow symlinks = yes
   wide links = yes
   unix extensions = no


## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = SMILING
   netbios name = PARIJS

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

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = bcast lmhosts host wins

#members of teh ntadmin group should be able to aad drivers and set
# printer properties. root is implicitly always a 'printer adin'
printer admin = @ntadmin


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
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

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

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
   domain logons = yes
   domain master = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
   logon drive = H:
   logon home = \\%N\%U\home

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
add machine script = sudo /usr/sbin/useradd -N -g machines -c Machine -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

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
#   socket options = TCP_NODELAY
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
   domain master = auto

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
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /srv/samba/netlogon
   guest ok = yes
   browsable = no
   read only = yes
   share modes = no
   write list = menno

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700

[base]
   comment = Test share for experimenting
   path = /shares/
   guest ok = no
   browsable = no
   read only = no
   admin users = @smi-ling

[extern]
   comment = External Share
   path = /shares/extern
   guest ok = no
   browseable = no
   read only = no
   admin users = @smi-ling
   hide unreadable = yes

[smiling]
   comment = Voor leden groep smi-ling ONLY
   path = /home/smi-ling
   guest ok = no
   browseable = no
   read only = no
   read list = @smi-ling
   write list = @smi-ling
   admin users = @smi-ling

[>films_A<]
   comment = Base share for PlayOn
   path = /shares/films_A
   guest ok = yes
   browseable = yes
   read only = yes
   write list = menno
   admin users = menno

[>films_B<]
   comment = Base share for PlayOn
   path = /shares/films_B
   guest ok = yes
   browseable = yes
   read only = yes
   write list = menno
   admin users = menno


[media]
   comment = Mount folder external devices
   path = /media
   guest ok = yes
   browseable = no
   read only = no
   hosts deny = 10.0.2.

[common]
   comment = Common Share
   path = /shares/common
   guest ok = yes
   browseable = no
   read only = no
   admin users = @smi-ling
   hosts deny = 10.0.2.

[remote]
   comment = remote FTP share (Rotterdam)
   path = /media/ftp_root/EXTERN
   guest ok = yes
   browseable = no
   read only = no
   hosts deny = 10.0.2.

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   use client driver = yes
   hosts deny = 10.0.2.

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
   hosts deny = 10.0.2.

# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
   write list = root, @ntadmin, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

### Post by CharlesA on 2011-08-20
Try using guest authentication instead of ldap and see what happens. Don't think it'll do anything different but it's worth a shot to help narrow the problem down.

---

### Post by Smi-Ling on 2011-08-20
I'm very sorry, but I don't know what you mean - or how to do this. Of course I'm quit willing to try - can you give some instructions?

---

### Post by CharlesA on 2011-08-20
Add guest = ok to a share and try copying to see what happens.

---

### Post by Smi-Ling on 2011-08-20
OK. Tried this. Here are the results.
1) made change in smb.conf
2) restart samba
3) switched network connection to full gigabit
4) did a test copy (700 MB; c.a. 30 sec)
5) logged off (too a long time to update profile)
6) logged on locally om winXP
7) connected to "guest share"
8) did the test copy; again high speed (c.a. 30 sec)
9) logged back on to server (whent quite snappy - but profile not changed)
10) did the test copy: crawling speed

Can you make anything out of this?

---

### Post by Entilza on 2011-08-20
You made a lot of hardware changes, it's time to test your network to make sure it's working first.  I'm sure Samba is fine.  You can try transfering through ftp to test the bandwidth without samba even in the picture.

install ethtool and report the stats of eth0 

$sudo ethtool eth0

$sudo ethtool -S eth0

Test file transfer through ftp by installing protfd and ftping from your windows box to ubuntu.

---

### Post by CharlesA on 2011-08-20
> **Entilza said:**
> You made a lot of hardware changes, it's time to test your network to make sure it's working first.  I'm sure Samba is fine.  You can try transfering through ftp to test the bandwidth without samba even in the picture.

install ethtool and report the stats of eth0 

$sudo ethtool eth0

$sudo ethtool -S eth0

Test file transfer through ftp by installing protfd and ftping from your windows box to ubuntu.

This would be the next step.

---

### Post by Smi-Ling on 2011-08-20
Let me start by saying that I am very glad with your help.

OK. I did as you both suggested. Installed proftpd. Ran a number of tests; each time transfering the same 700 MB file, from the same location on the server to the local drive of the workstation.

1) Original setup: 1:15 / ~10MB/sec (windows copy: ~ 2 min)
2) After "hot switch" to Gigabit setup: 0:39 sec / ~18 MB/sec. (windows copy: ~30 sec)

output of ethtool:

```

server@PARIJS:~$ sudo ethtool eth1
[sudo] password for server:
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
server@PARIJS:~$ sudo ethtool -S eth1
NIC statistics:
     tx_packets: 2567490
     rx_packets: 957861
     tx_errors: 0
     rx_errors: 0
     rx_missed: 0
     align_errors: 0
     tx_single_collisions: 0
     tx_multi_collisions: 0
     unicast: 957738
     broadcast: 114
     multicast: 9
     tx_aborted: 0
     tx_underrun: 0
server@PARIJS:~$

```3) "logged off", ftp to not-logged on workstation: c.a. 5 min / ~2MB/sec (max)
4) "logged back on": 1.8 MB/sec max speed; dwindling down to 0.9 MB/sec. (transfer aborted)

output of ethtool:

```

server@PARIJS:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
server@PARIJS:~$ sudo ethtool -S eth1
NIC statistics:
     tx_packets: 2808378
     rx_packets: 1109104
     tx_errors: 0
     rx_errors: 0
     rx_missed: 0
     align_errors: 0
     tx_single_collisions: 0
     tx_multi_collisions: 0
     unicast: 1108912
     broadcast: 177
     multicast: 15
     tx_aborted: 0
     tx_underrun: 0
server@PARIJS:~$


```
This all made me think that if not SAMBA, maybe "time" is the key here. So I restored everything back to the 100 MB setup. Now everything is back to normal. I then did the "hot switch": speed increase happens as always: ftp transfer ~ 40 sec. The I just waited 10 minutes. Did the FTP again. Amaizing: speed was reduced to 2.5 MB/sec!

So this is probabebly not caused bij SAMBA's log-off log-on handling (as I first suspected), but more a general network setting problem. Hopes this helps in narrowing down the cause.

Come to think of it: 18MB/sec is a bit slow for a gigabit setup. But that can also be caused by the server hardware itself beeing geared towards energy eficiency instead of performance.

---

### Post by Entilza on 2011-08-20
Ok Something is wrong because a 1gigabit network should be giving you at least 50+ mb/s.

Are you switching cables as well during your tests?  Try not to change more than one thing during each test so you can narrow it down.

Any chance of getting a third PC involved to help rule out where the slowdown is.  You also checked windows is connected at 1gig?

What about your router config.  Can you check your route from the ubuntu box to the windows pc?  Do a tracet from the windows to unix.

---

### Post by Smi-Ling on 2011-08-21
Yes I agree: it's something with the network. Now what I do is only swap ONE component in the cabling at a time. At first I changed the switch from a 10/100 to a gigabit switch, but since that is a lot of hassle, I now only change the connection of the server cable from the gigabit switch to the cable modem which has a 10/100 port. Results are the same. I also did these test with only changeing the network card beeing used in the server (eth0 is build-in 10/100 port; eth1 is new Realtec gigabit card): same result. 

As I described in my first post: this is a small network with WinXP SP3 workstations (in total 4; two with gigabit ports) and 10.04.3 LTS as server. When the whole system is "running" at gigabit speed, transferring data from server to workstations shows this dramatic speed decline, where as transfering data from workstation to workstations (both local disks) remains at a steady 20 MB/sec. 

Results are the same for both workstations. There is no router in this setup: it's a Sitecom "gigaswitch". IP adresses are dynamically using the DHCP function of the cable modem, that's also connected to the gigabit switch.

So im my opinion this problem is located somewhere in the server. At first I suspected SAMBA, but as you showed that's not the curlpit.  So I am quite at a loss here.

---

### Post by CharlesA on 2011-08-21
You can boot off a livecd and try copying a file back and forth to see if it does the same thing to rule out software misconfiguration.

20MB/sec seems a tad slow for gigabit, but it depends on what you are transferring - small files or big files.

---

### Post by PierreRobiquet on 2011-08-21
I've had a slightly similar experience to this, it was a bad ethernet cable that dropped around 10% of packets and did so in a sporadic fashion. Have you tried running a ping for a while, say 5 minutes on your network to see if any packets get dropped? When transferring the file between the two clients I would also check the checksum on both ends to ensure that the data isn't being corrupted. I would suggest you use something like the Ubuntu Live CD ISO and transfer it back and forth as it is large enough and should be available to you.

---

### Post by Smi-Ling on 2011-08-21
Hi! I had the server ping a workstation (and workstation the server at the same time) for 45 mins. server -> ws: 0 drops; ws->server 12 drops. Also I did the ws -> ws copy: I use a 700 mb movie (1 file). Copared the MD5 sums: no problems there. Also the file transferred from the server to te ws, althoug very slow, it came over with is't MD5 unchanged. So no problems there. Will try to boot from live CD tomorrow.

---

### Post by Smi-Ling on 2011-09-01
Hi everyone.

After beeing totally fed-up with this anoying problem, i bougt an INTEL PRO 10/100/1000 network card on E-bay for about $4.00 (the only one I could find that did NOT have the infamous realtec chip) and voila ... the nework runs at gigabit speed and is quite stable. 
So ... the problem is solved (sort of). 

Remains the question why this realtec-based card won't preform propperly. But than again: if I read the various fora right, I'm certainly not the only one struggeling with this card/chip. 

Everyone who has helped - thanks for the effort. It enabled me to pin-down the problem to the network card/driver and in that way contributed to solving it.

---

### Post by CharlesA on 2011-09-01
Glad you were able to get it working. Was the card a PCI card or PCIe card? I'm running realtek onboard and it's fine.

---

### Post by Smi-Ling on 2011-09-02
It is a PCI card. I am planning on putting this card in a WinXP system and see how it preforms. Maybe it's a simple hardware failure on this particular card. We'll see. I'll post the results.

---

### Post by CharlesA on 2011-09-02
> **Smi-Ling said:**
> It is a PCI card. I am planning on putting this card in a WinXP system and see how it preforms. Maybe it's a simple hardware failure on this particular card. We'll see. I'll post the results.

Good luck! I used Gigabit PCI cards before I had mobos with onboard gigabit, the performance is not that much difference from what I've seen, but it could very, like everything. :)

---

