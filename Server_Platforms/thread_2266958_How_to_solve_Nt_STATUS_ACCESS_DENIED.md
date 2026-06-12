---
title: "How to solve Nt_STATUS_ACCESS_DENIED"
date: 2015-02-26
forum: Server Platforms
---

### Post by p.giann on 2015-02-26
I have a problem with my samba server and in my log.smbd file appears these errors.

```
 [2000/01/01 01:01:24, 0] rpc_client/cli_pipe.c:cli_nt_session_open(1202)
 cli_nt_session_open: cli_nt_create failed on pipe \spoolss to machine PC.  Error was NT_STATUS_ACCESS_DENIED [2000/01/01 01:01:24, 0] 
rpc_client/cli_spoolss_notify.c:spoolss_connect_to_client(145)
  connect_to_client: unable to open the domain client session to machine PC. Error was : NT_STATUS_ACCESS_DENIED.
[2000/01/01 01:01:25, 0] lib/smbrun.c:setup_out_fd(43)
  setup_out_fd: Failed to create file /tmp/smb.MzIKK7. (Read-only file system)
 
```

---

### Post by slickymaster on 2015-02-26
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by p.giann on 2015-02-26
I added in smbusr.conf  global configuration this command 

```
force user = admin
```

It seems partially solved because appears yet this error
 ```
 [2000/01/01 00:55:44, 0] lib/smbrun.c:setup_out_fd(43)  setup_out_fd: Failed to create file /tmp/smb.D548WZ. (Read-only file system)

```

I tried to force mounting file system with the command ```
 mount  -f -a -w 
``` but seems tmp folder is ever read-only.
Maybe is possible to change tmp folder?

---

### Post by volkswagner on 2015-02-26
What type of system is this? What kind of hardware, disks, etc.?

What's the output of:
```
cat /proc/mounts
```

and

```
ls -al /tmp
```

---

### Post by p.giann on 2015-02-27
This is the output :
```
# cat /proc/mountsrootfs / rootfs rw 0 0
/dev/root / squashfs ro 0 0
/proc /proc proc rw,nodiratime 0 0
tmpfs /var tmpfs rw 0 0
sysfs /var/sys sysfs rw 0 0
/var/udev/inodes/usbsda1 /var/udev/mount/NASusbsda1 vfat rw,nodiratime,fmask=002
2,dmask=0022 0 0

```

and this :

```
# ls -al /tmp
lrwxrwxrwx    1 34393507 34393507        4 Mar  8  2011 /tmp -> /mnt

```

---

### Post by volkswagner on 2015-02-27
I asked four questions. You answered two. Had you anwered all four you may have avoided my next two.

Did you notice / is squashfs and mounted read only? Why is /tmp symlinked to /mnt?

---

### Post by p.giann on 2015-02-27
Thanks for your time. It is true. Sorry... :oops::oops::oops::oops::oops:

What type of system is this? 
It is a router Telsey.
What kind of hardware, disks, etc.? 
CPU BCM96358 RAM 32MiB FLASH 8MiB
Did you notice / is squashfs and mounted read only? Yes, I tried to mount rw but didn't work. 
 Why is /tmp symlinked to /mnt? I don't know.. and I don't know why the tmp directory isn't writable..

---

### Post by volkswagner on 2015-02-27
Your samba server is running on the router?

I'm trying to help, but you are really holding back on information.

Your original post states your SAMBA server log file show's:
```
setup_out_fd: Failed to create file /tmp/smb.MzIKK7. (Read-only file system)
```

Please explain in detail, server and client setup. I'm really confused why you are asking
in Ubuntu forum about a router running SAMBA.

Your router is running Ubuntu?
Is your client running Ubuntu?
Is your router running SAMBA Server?
What operating system is your router running?
You may be better off asking the makers of the router or router firmware.

---

### Post by p.giann on 2015-02-27
I have a router and 2 notebook connected to this. On my router is running an O.S. Linux version 2.6.8.1. One of my notebook running Ubuntu 12.04 and another running Windows Vista. I also have a Samsung printer and an usb hd, both connected to router via usb. When I open usb hd from my two notebooks, all is ok. But I can't see the printer from my two notebooks. The log.smbd file is from router which has samba. I don't know if it is a bad configuration of my ubuntu notebook or is a problem of router

---

### Post by volkswagner on 2015-02-27
```
O.S. Linux version 2.6.8.1
```
The above really only tells us what kernel the router is running.

So now I know file sharing is working but printer sharing is not.

Again you should be asking at forums related to the router/router firmware.
I'm not familiar with Telsey. I'm not sure what version you are running but perhaps
you can install OpenWRT on it. [http://wiki.openwrt.org/toh/telsey/cpva502.w](http://wiki.openwrt.org/toh/telsey/cpva502.w)

I run OpenWRT on my router and use [p910nd]("http://wiki.openwrt.org/doc/howto/p910nd.server") print server daemon, not SAMBA to share the printer.

Post your smb.conf from the router.  I'll try to help, but again I'm not sure
I can offer advice on how to get the tmp file written to a writeable location (which may not be necessary if you can get the auth working properly).

---

### Post by p.giann on 2015-02-28
Thanks for your patience. This is smb.conf
```
# cat /etc/smb.conf
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
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


# check for user config file
config file = /var/samba/smbusr.conf

# workgroup = NT-Domain-Name or Workgroup-Name
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = Telsey Router Samba Server %v

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
;   hosts allow = 192.168.1. 192.168.2. 127.

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = no

# you may wish to override the location of the printcap file
;   printcap name = /etc/printcap

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
  guest account = nobody

# this tells Samba to use a separate log file for each machine
# that connects
;   log file = /usr/local/samba/var/log.%m

# Put a capping on the size of the log files (in Kb).
;   max log size = 50

# Security mode. Most people will want user level security. See
# security_level.txt for details.
   security = share
# Use password server option only with security = server
;   password server = <NT-Server-Name>

# Password Level allows matching of _n_ characters of the password for
# all combinations of upper and lower case.
;  password level = 8

# You may wish to use password encryption. Please read
# ENCRYPTION.txt, Win95.txt and WinNT.txt in the Samba documentation.
# Do not enable this option unless you have read those documents
  encrypt passwords = yes

# Unix users can map to different SMB User names
;  username map = /etc/samba/smbusers

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /etc/samba/smb.conf.%m

# Most people will find that this option gives better performance.
# See speed.txt and the manual pages for details
;   socket options = TCP_NODELAY

# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
;   interfaces = 192.168.12.2/24 192.168.13.2/24
   interfaces = br0

# Configure remote browse list synchronisation here
#  request announcement to, or browse list sync from:
#       a specific host or from / to a whole subnet (see below)
;   remote browse sync = 192.168.3.25 192.168.5.255
# Cause this host to announce itself to local subnets here
;   remote announce = 192.168.1.255 192.168.2.44

# Browser Control Options:
# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
;   local master = no

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
;   os level = 33

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
;   domain master = yes

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
;   preferred master = yes

# Use only if you have an NT server on your network that has been
# configured at install time to be a primary domain controller.
;   domain controller = <NT-Domain-Controller-SMBName>

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
#       Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one  WINS Server on the network. The default is NO.
;   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
   dns proxy = no

# Case Preservation can be handy - system default is _no_
# NOTE: These can be set on a per share basis
;  preserve case = no
;  short preserve case = no
# Default case is normally upper case for all DOS files
;  default case = lower
# Be very careful with case sensitivity - it can break things!
;  case sensitive = no

# Telsey
   netbios name = CPVA642_NAS
   bind interfaces only = True
   debug level = -1


#============================ Share Definitions ==============================
;[homes]
;   comment = Home Directories
;   browseable = no
;   writable = yes

# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /var/samba/lib/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /var/samba/profiles
;    browseable = no
;    guest ok = yes


# NOTE: If you have a BSD-style print system there is no need to
# specifically define each individual printer
;[printers]
;   comment = All Printers
;   path = /usr/spool/samba
;   browseable = no
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

[public]
   path = /mnt
   public = yes
   writable = yes
   printable = no
   guest ok =yes

```


etc directory isn't writable. If I want to change something I can do that only on my smbusr.conf file.
This is my smbusr.conf rewritten when I reboot the router:

```
# cat /var/samba/smbusr.conf
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
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

# workgroup = NT-Domain-Name or Workgroup-Name
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = TELSEY Router Samba Server


   smb passwd file = /var/samba/smbpasswd

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
;   hosts allow = 192.168.1. 192.168.2. 127.


# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
;  guest account = pcguest
  guest account = nobody



# Put a capping on the size of the log files (in Kb).
   max log size = 200

# Security mode. Most people will want user level security. See
# security_level.txt for details.
   security = share

# You may wish to use password encryption. Please read
# ENCRYPTION.txt, Win95.txt and WinNT.txt in the Samba documentation.
# Do not enable this option unless you have read those documents
  encrypt passwords = yes


# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
   interfaces = br0

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
  wins support = yes


# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
   dns proxy = no


# Telsey
   netbios name = CPVA642H_NAS
   bind interfaces only = True
   debug level = 1
   log level = 1
   socket options = TCP_NODELAY IPTOS_LOWDELAY
   read raw = yes
   write raw = yes
#   strict sync = yes
#   sync always = yes
   max xmit = 65535
   dead time = 15
   getwd cache = yes
    wide links = no



#============================ Share Definitions ==============================
[NASusbsda1]
comment = CPVA642H Disk Sharing
path = /var/udev/mount/NASusbsda1
public = yes
writable = yes
printable = no
guest ok = yes
browsable = yes


```

var directory can be modified.

smbpasswd is in etc directory and it is an empty file.

---

### Post by volkswagner on 2015-02-28
You are currently using security = share

Please read the [SAMBA docs on the different security mechanisms]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html") (particularly user and share).

With security = share, plus "load printers = no", and the fact you have no printers defined, I'd expect printer problems.

In fact, I'm not sure how you even see printers listed. Are you running CUPS on that router?

Please provide configs for the printer.

---

### Post by p.giann on 2015-02-28
I didn't found Cups. From the router printer setting menu I see a configuration string:
```
http://192.168.10.1:631/printers/Samsung
```
But I can't connect to printer when I put this string on Add printer.

On router is running an ippd demon on file /var/printers.ini 

```
> ps  PID  Uid     VmSize Stat Command
    1 admin       364 S   init
    2 admin           SW< [ksoftirqd/0]
    3 admin           SW< [events/0]
    4 admin           SW< [khelper]
    5 admin           SW< [kblockd/0]
    6 admin           SW  [khubd]
   20 admin           SW  [pdflush]
   21 admin           SW  [pdflush]
   22 admin           SW  [kswapd0]
   23 admin           SW< [aio/0]
   24 admin           SW  [pciehpd_event]
   25 admin           SW  [shpchpd_event]
   36 admin           SW  [mtdblockd]
   45 admin       412 S   -sh
   83 admin       208 S N udevd
  194 admin      2044 S   cfm
  340 admin           SW  [scsi_eh_0]
  345 admin           SW  [usb-storage]
  564 admin       204 S   pvc2684d
  706 admin           DW  [wl0]
  898 admin       388 S   syslogd -C -l 7
  901 admin       332 S   klogd
  904 admin      1912 S   telnetd
  908 admin       308 S   tftpd
  910 admin       224 S   ippd /var/printers.ini
  911 admin      1956 S   cfm
  916 admin      2172 S   httpd
  947 admin      1224 S N smbd
  950 admin      1100 S   nmbd
  951 admin       852 S   nmbd
  954 admin      2044 S   cfm
  955 admin      2044 S   cfm
  959 admin       208 S   restorebtnd
  985 admin       340 S   dhcpc -i br1
 1075 admin       344 S   upnp -L br0 -W waneth_1 -D
 1232 admin      1968 S   telnetd
 1241 admin       352 R   sh -c ps
 1242 admin       364 R   ps

``` 

this is the file /var/printers.ini

```
# cat /var/printers.ini[Samsung]
make=Samsung CLP-320 Series
device=/dev/printer0

```

---

### Post by volkswagner on 2015-02-28
CUPS runs on port 631. Can you post a screen shot of the main page ([http://192.168.10.1:631](http://192.168.10.1:631)).

Before diving into SAMBA, perhaps you can share printer directly with CUPS/ippd.

Do you have a screen similar to this when navigating to [http://192.168.10.1:631/admin](http://192.168.10.1:631/admin)

[IMG]http://volkswagner.com/gate/CUPSadmin.png[/IMG]

If you really want to get SAMBA to share the printer would start by adding line to your smbusr.conf file:
```
load printers = yes
```

With this, you should see printer listed as a share when navigating to \\CPVA642H_NAS\

---

### Post by p.giann on 2015-02-28
I tried to add load printers in smbusr.conf file but didn't work and when I go on [COLOR=#000000]the main page ([/COLOR][http://192.168.10.1:631]("http://192.168.10.1:631/")[COLOR=#000000]). or [/COLOR][COLOR=#000000]to [/COLOR][http://192.168.10.1:631/admin](http://192.168.10.1:631/admin) anything appears ( error 404) . It seems like the router don't open the port or don't have the admin panel.

I don't know if Cups is in another directory but in /etc/ I have only this:
```
# ls /etc/
CVS              fstab            modules_install  smb.conf
Wireless         gateway.conf     passwd           smbpasswd
adsl             group            ppp              smbusr.conf
certs            hosts            pppmsg           sysmsg
default1.cfg     hotplug          profile          tlsCerts
default2.cfg     hotplug.d        protocols        udev
default3.cfg     inetd.conf       psk.txt          udhcpd.conf
default4.cfg     init.d           racoon.conf      udhcpd.leases
dev.d            inittab          resolv.conf      wlan
dhcp             iproute2         services
ethertypes       ipsec.conf       siproxd



```

---

### Post by volkswagner on 2015-02-28
can you post a screen shot of

[http://192.168.10.1:631/printers/Samsung](http://192.168.10.1:631/printers/Samsung)

and

[http://192.168.10.1:631/printers](http://192.168.10.1:631/printers)

---

### Post by p.giann on 2015-02-28
Same problem ( error 404). If it is useful, this is the new log.nmbd
```
# cat log.nmbd[2000/01/01 00:00:27, 0] nmbd/nmbd.c:main(795)
  Netbios nameserver version 2.2.12 started.
  Copyright Andrew Tridgell and the Samba Team 1994-2002
[2000/01/01 00:00:27, 0] lib/debug.c:debug_parse_params(198)
  debug_parse_params: unrecognized debug class name or format [-1]
[2000/01/01 00:00:27, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 601 from pid 601)
[2000/01/01 00:00:27, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 601 from pid 601)
[2000/01/01 00:00:27, 0] lib/charset.c:load_client_codepage(213)
  load_client_codepage: filename /lib/codepages/codepage.850 does not exist.
[2000/01/01 00:00:27, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.850 does not exist.
[2000/01/01 00:00:27, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.ISO8859-1 does not exist.
[2000/01/01 00:00:27, 0] nmbd/nmbd.c:main(827)
  standard input is not a socket, assuming -D option
[2000/01/01 00:00:27, 0] nmbd/asyncdns.c:start_async_dns(148)
  started asyncdns process 626
[2000/01/01 00:00:46, 0] nmbd/nmbd.c:terminate(59)
  Got SIGTERM: going down...
[2000/01/01 00:00:46, 0] nmbd/nmbd.c:main(795)
  Netbios nameserver version 2.2.12 started.
  Copyright Andrew Tridgell and the Samba Team 1994-2002
[2000/01/01 00:00:46, 0] lib/debug.c:debug_parse_params(198)
  debug_parse_params: unrecognized debug class name or format [-1]
[2000/01/01 00:00:46, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 954 from pid 954)
[2000/01/01 00:00:46, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 954 from pid 954)
[2000/01/01 00:00:46, 0] lib/charset.c:load_client_codepage(213)
  load_client_codepage: filename /lib/codepages/codepage.850 does not exist.
[2000/01/01 00:00:46, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.850 does not exist.
[2000/01/01 00:00:46, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.ISO8859-1 does not exist.
[2000/01/01 00:00:46, 0] nmbd/nmbd.c:main(827)
  standard input is not a socket, assuming -D option
[2000/01/01 00:00:46, 0] nmbd/asyncdns.c:start_async_dns(148)
  started asyncdns process 956
[2000/01/01 00:01:26, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(404)
  *****


  Samba name server CPVA642H_NAS is now a local master browser for workgroup WORKGROUP on subnet 192.168.10.                                                 1


  *****
[2000/01/01 00:01:26, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(358)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
  Unable to sync browse lists in this workgroup.
[2000/01/01 00:04:07, 0] nmbd/nmbd.c:main(795)
  Netbios nameserver version 2.2.12 started.
  Copyright Andrew Tridgell and the Samba Team 1994-2002
[2000/01/01 00:04:07, 0] lib/debug.c:debug_parse_params(198)
  debug_parse_params: unrecognized debug class name or format [-1]
[2000/01/01 00:04:07, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 1229 from pid 1229)
[2000/01/01 00:04:07, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 1229 from pid 1229)
[2000/01/01 00:04:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:04:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:04:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:04:07, 0] lib/charset.c:load_client_codepage(213)
  load_client_codepage: filename /lib/codepages/codepage.850 does not exist.
[2000/01/01 00:04:07, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.850 does not exist.
[2000/01/01 00:04:07, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.ISO8859-1 does not exist.
[2000/01/01 00:04:07, 0] nmbd/asyncdns.c:start_async_dns(148)
  started asyncdns process 1231
[2000/01/01 00:04:07, 0] lib/pidfile.c:pidfile_create(86)
  ERROR: nmbd is already running. File /var/locks/nmbd.pid exists and process id 955 is running.
#

```

And this is the new log.smbd :
```
# cat log.smbd
  smbd version 2.2.12 started.
  smbd version 2.2.12 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2002
[2000/01/01 00:03:58, 0] lib/debug.c:debug_parse_params(198)
  debug_parse_params: unrecognized debug class name or format [-1]
[2000/01/01 00:03:58, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 1227 from pid 1227)
[2000/01/01 00:03:58, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 1227 from pid 1227)
[2000/01/01 00:03:58, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:03:58, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:03:58, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:03:58, 0] lib/charset.c:load_client_codepage(213)
  load_client_codepage: filename /lib/codepages/codepage.850 does not exist.
[2000/01/01 00:03:58, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.850 does not exist.
[2000/01/01 00:03:58, 0] lib/util_unistr.c:load_unicode_map(617)
  load_unicode_map: filename /lib/codepages/unicode_map.ISO8859-1 does not exist.
[2000/01/01 00:03:58, 0] lib/pidfile.c:pidfile_create(86)
  ERROR: smbd is already running. File /var/locks/smbd.pid exists and process id 952 is running.
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 1216 from pid 1216)
[2000/01/01 00:05:07, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 1216 from pid 1216)
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:07, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 952 from pid 952)
[2000/01/01 00:05:54, 1] lib/debug.c:debug_message(258)
  INFO: Debug class all level = 1   (pid 952 from pid 952)
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:05:54, 1] param/params.c:Parameter(382)
  params.c:Parameter() - Ignoring badly formed line in configuration file:
[2000/01/01 00:09:11, 1] smbd/service.c:close_cnum(677)



```

---

### Post by volkswagner on 2015-02-28
I don't understand. You said you configured printer at [http://192.168.10.1:631/printers/Samsung](http://192.168.10.1:631/printers/Samsung)
and now you get 404 error???

That's a very old version of samba

Again. I think you will need to ask firmware makers.

---

### Post by p.giann on 2015-03-01
I don't know... Can I change the default listen port 631 or can I change this default string[COLOR=#000000] [/COLOR][http://192.168.10.1:631/printers/Samsung](http://192.168.10.1:631/printers/Samsung)? Maybe is not correct.

---

### Post by volkswagner on 2015-03-01
I guess I have misread your post:

> **p.giann said:**
> I didn't found Cups. From the router printer setting menu I see a configuration string:
```
http://192.168.10.1:631/printers/Samsung
```
But I can't connect to printer when I put this string on Add printer.


I thought you were able to see the above configuration page in your browser.
This url does not get inserted in "add printers" wizard. 

Where did you find reference for this url  [http://192.168.10.1:631/printers/Samsung???](http://192.168.10.1:631/printers/Samsung???)

Take a look at this thread [http://ubuntuforums.org/archive/index.php/t-2211933.html](http://ubuntuforums.org/archive/index.php/t-2211933.html)

Again, you're running a very old version of SAMB, and I have no Idea what Linux distro you're running, plus
your ipp daemon is not the same as CUPS, but it should give you some ideas.

---

### Post by p.giann on 2015-03-02
Where did you find reference for this url  [http://192.168.10.1:631/printers/Samsung???](http://192.168.10.1:631/printers/Samsung???)
From this page. 
[[img]http://s1.postimg.org/z8y3zf1hn/image.jpg[/img]](http://postimg.org/image/z8y3zf1hn/)

---

