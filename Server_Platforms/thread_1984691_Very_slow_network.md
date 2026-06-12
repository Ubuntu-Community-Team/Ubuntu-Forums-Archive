---
title: "Very slow network"
date: 2012-05-22
forum: Server Platforms
---

### Post by Ghost_Mazal on 2012-05-22
My Server (running Ubuntu server 11.10) is dreadfully slow over the network.
It runs on fairly new hardware (Intel I7 , 4gig ram)

It takes very long to open samba shares , it takes very long to copy files , it takes very long to log-in with ssh. It seems to be the network overall.

I have searched but couldn't find any real help or solution.

What can I check to find the problem ?

Thanx

---

### Post by roelforg on 2012-05-22
Are you sure it isn't a slow hdd or some other app eating bandwidth at either end?

---

### Post by Ghost_Mazal on 2012-05-22
I did use 2 seperate HDD's , so it's not the HDD.

I don't know how to check the possibility of other apps eating bandwidth on the server.

Also , it has no access to the internet. It's only accessible on the LAN so it's not something running on the Internet the whole time.

---

### Post by rubylaser on 2012-05-22
The first thing to do when troubleshooting is to simplify the setup as much as you can.  I'd run a crossover cable from your server to a client computer and run iperf on each end.  The server side will look like this.

```
iperf -s
```

and the client can be as simple as this.
```
iperf -c 10.1.1.80
```

To install iperf you just need to do this
```
sudo apt-get intsall iperf -y
```

The output will look like this.
```
Rubylasers-Mac-Pro ~ $ iperf -c 10.1.1.80
------------------------------------------------------------
Client connecting to 10.1.1.80, TCP port 5001
TCP window size: 65.0 KByte (default)
------------------------------------------------------------
[  3] local 10.1.1.75 port 52914 connected with 10.1.1.80 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.09 GBytes   **933 Mbits/sec**

```

If you have two gigabit NICs involved, you should see between 825-900+ Mbits/sec here.  If you don't, you either have a bad NIC or a bad crossover cable.

If this test is a success, you can try to repeat it with a switch between the client and server.  If you suddenly see a dropoff, it's likely your switch isn't keeping up.

That's how I'd start to diagnosis this, rather than just looking at the file transfer protocols that are currently slow. Also, what is "dreadfully slow" in MB/s? And, is this a gigabit network?

---

### Post by Ghost_Mazal on 2012-05-22
And that's exactly where things goes south. As always nothing is installed in linux and you have to apt-get.

No internet connection so can't do that.

On the description of slow , it took me about 8 minutes to copy a 110mb file and it takes about 90seconds just to log in with SSH (putty). Which is no where near what the speed should be. I'll see if I can do a copy with a tool that will display mb/s

---

### Post by Ghost_Mazal on 2012-05-22
Eeeeeeeeeeek it's even worse than I thought !!!! I copied with a tool that shows transfer speed and it jumps between 380kb , YES kb/s ,  and 2800 kb/s !!!! Horrible.

---

### Post by kmyram on 2012-05-22
> **Ghost_Mazal said:**
> it takes about 90seconds just to log in with SSH (putty).

Two things...
a) what does /var/log/syslog say?
b) I vaguely recall slow login being caused by nameserver-lookup-error - is client machine ipadress in servers hosts-file?

/Kasper

---

### Post by Ghost_Mazal on 2012-05-22
> **kmyram said:**
> Two things...
a) what does /var/log/syslog say?
b) I vaguely recall slow login being caused by nameserver-lookup-error - is client machine ipadress in servers hosts-file?

/Kasper

a) A whole heap of stuff not understandable. Can you be more specific ?

b) Nope , added it and the SSH (putty) login is solved now. Logs in at normal speed.

Copying to the samba share is still at 200kb/s to 2500 kb/s

---

### Post by rubylaser on 2012-05-22
> **Ghost_Mazal said:**
> And that's exactly where things goes south. As always nothing is installed in linux and you have to apt-get.

No internet connection so can't do that.

On the description of slow , it took me about 8 minutes to copy a 110mb file and it takes about 90seconds just to log in with SSH (putty). Which is no where near what the speed should be. I'll see if I can do a copy with a tool that will display mb/s

I'd either temporarily connect it to the internet, or grab the package on a different machine and burn it to a disk or transfer to a thumb drive to bring it over.  You're not going to be able to troubleshoot this without the proper tools.

Also, if I may ask, why does this box have no internet access? If it's just for security, you can use iptables to deny all inbound and outbound traffic except what you need.

---

### Post by Ghost_Mazal on 2012-05-22
> **rubylaser said:**
> I'd either temporarily connect it to the internet, or grab the package on a different machine and burn it to a disk or transfer to a thumb drive to bring it over.  You're not going to be able to troubleshoot this without the proper tools.

Also, if I may ask, why does this box have no internet access? If it's just for security, you can use iptables to deny all inbound and outbound traffic except what you need.

I will never understand why tools that is so important are not included. Why must we always get a half OS.

Well the server is sitting behind a proxy. There is no direct access to Internet for it. And I did try to go the "enter the proxy" route for it and it was a complete mess that never worked and every tutorial on it that I could get my hands on winded up in a FAIL. So not even going to try that again.

---

### Post by rubylaser on 2012-05-22
> **Ghost_Mazal said:**
> I will never understand why tools that is so important are not included. Why must we always get a half OS.

Well the server is sitting behind a proxy. There is no direct access to Internet for it. And I did try to go the "enter the proxy" route for it and it was a complete mess that never worked and every tutorial on it that I could get my hands on winded up in a FAIL. So not even going to try that again.

iperf isn't a core tool and that's why it's not installed by default.  All Linux distros are designed so that you can add the packages you need.  

You're asking for help, but you seem unwilling to try anything and you have a rather derogatory undertone, so I'm not really sure what we can do to help you at this point?

---

### Post by Ghost_Mazal on 2012-05-22
> **rubylaser said:**
> iperf isn't a core tool and that's why it's not installed by default.  All Linux distros are designed so that you can add the packages you need.  

You're asking for help, but you seem unwilling to try anything and you have a rather derogatory undertone, so I'm not really sure what we can do to help you at this point?

I already tried everything suggested that didn't involve Internet (and even that I tried to get working and put a lot of time into it on a previous occasion) So please don't lie.

I guess I just hoped that the OS would have been decent enough to have tools to at least do some troubleshooting. Never thought that was too much too ask and that 3rd party software would have been necessary for troubleshooting.

You are right , there doesn't seem to be anything you guys would be able to do as it seems Internet is needed for troubleshooting.

Sorry for asking , have a nice day.
Gonna right this off as bad software

---

### Post by rubylaser on 2012-05-22
> **Ghost_Mazal said:**
> I already tried everything suggested that didn't involve Internet (and even that I tried to get working and put a lot of time into it on a previous occasion) So please don't lie.

I guess I just hoped that the OS would have been decent enough to have tools to at least do some troubleshooting. Never thought that was too much too ask and that 3rd party software would have been necessary for troubleshooting.

You are right , there doesn't seem to be anything you guys would be able to do as it seems Internet is needed for troubleshooting.

Sorry for asking , have a nice day.
Gonna right this off as bad software

I'm not sure what lying about?!?! I think you're obviously in over your head, and frustrated.  I'm going to move on because this is not constructive, and you've just looking for a way to vent, and I'm not your dumping ground.

---

### Post by kmyram on 2012-06-02
> **Ghost_Mazal said:**
> 
Sorry for asking , have a nice day.
Gonna right this off as bad software

Easy, partner :)
Can you ftp? Test that.

Then, what does your /etc/samba/smb.conf say - especially under the "########### MISC ###########" section header.
TCP_NODELAY should be set on IMHO and then there's some other tweaking possibilities...

/Kasper

---

### Post by Ghost_Mazal on 2012-06-02
> **kmyram said:**
> Easy, partner :)
Can you ftp? Test that.

Then, what does your /etc/samba/smb.conf say - especially under the "########### MISC ###########" section header.
TCP_NODELAY should be set on IMHO and then there's some other tweaking possibilities...

/Kasper

I tried all of that already. All the performance settings in smb.conf made no difference.
Even the buffers settings makes no difference.

Even tried different network card , flyleed , switch.

Tried the hosts file with ip and host names on both client and server side.

I found that this is a very common problem with ubuntu and samba. I tried many things found on the web , but nothing really helps.

edit: No , ftp is not set up.
The only other service I use is apache , and that is very quick.

---

### Post by Gyokuro on 2012-06-02
Why can the OP not post his/her smb.conf? If it is problem with samba and ubuntu more people will post - that's not the case so I think it is more problem of OP's network configuration (DNS resolving issue).

---

### Post by Ghost_Mazal on 2012-06-02
> **Gyokuro said:**
> Why can the OP not post his/her smb.conf? If it is problem with samba and ubuntu more people will post - that's not the case so I think it is more problem of OP's network configuration (DNS resolving issue).

If I remember on Monday I will post the smb.conf file. Don't have access on weekends to the server.

It's not my network. In the same office there is an old little P4 with 512mb ram on the same network and it's samba performance is fast as it should be. It has an almost exactly same configuration in samba , except for the shares have different names and it runs ubuntu server 10.10 not 11.10. And this little old machine has no speed issues over the network.

It's also not the client , as the same clients copy fast to the old 10.10 machine and slow to the 11.10  machine.
Problem is definitely with the 11.10 server. And there are various clients , not just one. And they differ between Xp and Win 7. But all are slow to the 11.10 but fast to the old 10.10 , on the same network

---

### Post by Ghost_Mazal on 2012-06-02
Oh and I forgot to mention , clients make mapped drives to the server using

```
//ipadres/sharename
```

I don't use

```
//servername/sharename/
```

So DNS shouldn't be an issue anyway

---

### Post by cariboo on 2012-06-03
You can always download the version of iperf you need from [packages.ubuntu.com]("http://packages.ubuntu.com/"), and upload it using sftp to the server, and install it manually.

It would also help if you told us how you are connecting to the server, what type of network, are there any switches, whether managed or unmanaged, and any other details you can think of.

---

### Post by Ghost_Mazal on 2012-06-03
> **cariboo907 said:**
> You can always download the version of iperf you need from [packages.ubuntu.com]("http://packages.ubuntu.com/"), and upload it using sftp to the server, and install it manually.

It would also help if you told us how you are connecting to the server, what type of network, are there any switches, whether managed or unmanaged, and any other details you can think of.

Wired network , 3com 3300 managed switches, 100mb/s network

I connect like I said with ip and not with servername.
I make mapped drives in windows. So there are permanent connections with drive letters to the shares.
Clients are mixed , Win XP and Win 7 , both are slow to the server.
Other services that are used is php front end's to mysql databases. (those services are very fast without issue)
Static ip's on server and all clients

Anything else that is relevant ?

---

### Post by Ghost_Mazal on 2012-06-04
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
# - When such options are commented with ";", the proposed setting
# differs from the default Samba behaviour
# - When commented with "#", the proposed setting is the default
# behaviour of Samba but the option is considered important
# enough to be mentioned here
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
log file = /var/log/samba/log.%m
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
obey pam restrictions = yes
interfaces = 127.0.0.0/8 eth2
map to guest = bad user
encrypt passwords = yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
dns proxy = no
netbios name = zdwit
server string = %h server (Samba, Ubuntu)
path = /home/software
unix password sync = yes
workgroup = chq
os level = 20
security = user
syslog = 0
usershare allow guests = yes
panic action = /usr/share/samba/panic-action %d
max log size = 1000
pam password change = yes
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
# server string is the equivalent of the NT Description field
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
# wins support = no
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z
# This will prevent nmbd to search for NetBIOS names through DNS.
# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast
#### Networking ####
# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = yes
&#12288;
&#12288;
#### Debugging/Accounting ####
# This tells Samba to use a separate log file for each machine
# that connects
# Cap the size of the individual log files (in KiB).
# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
# syslog only = no
# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
# Do something sensible when Samba crashes: mail the admin a backtrace
&#12288;
####### Authentication #######
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
# You may wish to use password encryption. See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using. 
&#12288;
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
########## Domains ###########
# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
; domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
# logon path = \\%N\%U\profile
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
; logon drive = H:
# logon home = \\%N\%U
# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd
# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe. 
# The following assumes a "machines" group exists on the system
; add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe. 
; add group script = /usr/sbin/addgroup --force-badname %g
########## Printing ##########
# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
# load printers = yes
# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap
# CUPS printing. See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups
############ Misc ############
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=65536 SO_SNDBUF=65536
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
# domain master = auto
# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash
# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
; winbind enum groups = yes
; winbind enum users = yes
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
; usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
#======================= Share Definitions =======================
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
comment = Home Directories
browseable = no
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
read only = no
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
create mask = 0700
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
directory mask = 0700
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
valid users = %S
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; read only = yes
# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700
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
; write list = root, @lpadmin
# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; read only = yes
; locking = no
; path = /cdrom
; guest ok = yes
# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom
&#12288;
&#12288;
&#12288;
&#12288;
&#12288;
&#12288;
&#12288;
[finance]
revalidate = yes
writeable = yes
valid users = sarahmah,siphoba,wendyn,@finance
write list = @finance
only user = yes
path = /home/finance
[software]
valid users = albiedp,barrydk,daniesm,wikusv
create mask = 770
write list = barrydk,wikusv,albiedp,daniesm,@itusers
path = /home/software
directory mask = 770
[www]
valid users = barrydk,wikusv
create mask = 775
write list = barrydk,wikusv
path = /var/www
directory mask = 775
&#12288;

```

---

### Post by R. M. Frank on 2012-06-04
Hmm, I didn't see anything about network configurations themselves, just a lot about samba.

Are the network interfaces correctly configured? (ifconfig, /etc/network/interfaces), is the gateway correct (netstat -r), are the dns servers correctly specified, etc.

In my case (two network interfaces, both using dhcp), network access nealry stopped because the system picked the wrong network interface as gateway after the upgrade to 12.04 and a reboot. I simply entered the correct gateway and now things are back to normal.

-Robert

---

### Post by Ghost_Mazal on 2012-06-04
> **R. M. Frank said:**
> Hmm, I didn't see anything about network configurations themselves, just a lot about samba.
 
Are the network interfaces correctly configured? (ifconfig, /etc/network/interfaces), is the gateway correct (netstat -r), are the dns servers correctly specified, etc.
 
In my case (two network interfaces, both using dhcp), network access nealry stopped because the system picked the wrong network interface as gateway after the upgrade to 12.04 and a reboot. I simply entered the correct gateway and now things are back to normal.
 
-Robert
 
It's because the other network services are fine and only Samba that has an issue that I didn't post interfaces. But here it is:
 
 ```
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth2
#auto eth1
#iface eth0 inet dhcp
#iface eth0 inet static
#           address 10.131.29.109
#           netmask 255.255.255.0
#           gateway 10.131.29.1
#iface eth1 inet static
#           address 10.131.29.109
#           netmask 255.255.255.0
#           gateway 10.131.29.1
iface eth2 inet static
            address 10.131.29.109
            netmask 255.255.255.0
            gateway 10.131.29.1

```

---

### Post by Ghost_Mazal on 2012-06-04
/etc/resolv.conf
 
```
 
#nameserver 10.0.0.2
nameserver 10.131.64.38
nameserver 10.135.220.11


```
 
And yes I am sure all the ip's in both the interface file and the resolv file is correct.

---

### Post by Ghost_Mazal on 2012-06-04
Good news is I got iperf on the server , bad news is I get this when I try and test to one of my pc's :
 

```
sudo iperf -c 10.131.29.40
connect failed: Connection refused
```

---

### Post by Ghost_Mazal on 2012-06-04
Ok I quickly saw I need 2 Linux machines to use iperf.
Fortunately I have the 2nd server.
 
Here is the test results and it is clear that my network is fine , and my network configs is fine. It defnitely looks to be Samba related as iperf didn't show speed issues:
 
```
 
 
10.10 server to the 11.10 problem server:
 
iperf -c 10.131.29.109
------------------------------------------------------------
Client connecting to 10.131.29.109, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 10.131.29.40 port 57058 connected with 10.131.29.109 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  12.2 MBytes  10.2 Mbits/sec
 
No speed issues
 
11.10 problem server to 10.10 fast server:
 
iperf -c 10.131.29.40
------------------------------------------------------------
Client connecting to 10.131.29.40, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 10.131.29.109 port 33402 connected with 10.131.29.40 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.2 sec  11.5 MBytes  9.50 Mbits/sec
 
Also no speed issues

```

---

### Post by Ghost_Mazal on 2012-06-04
Iperf results from XP client machine :
 
```
------------------------------------------------------------
Client connecting to 10.131.29.109, TCP port 5001
TCP window size: 64.0 KByte (default)
------------------------------------------------------------
[  3] local 10.131.29.85 port 1874 connected with 10.131.29.109 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-18.0 sec  20.0 MBytes  9.32 Mbits/sec

```
 
Also no speed issues , yet samba copies at only 300 - 800kb/s :confused:

---

### Post by kmyram on 2012-06-04
> **Ghost_Mazal said:**
> ```
 
# You may want to add the following on a Linux system:
# SO_RCVBUF=65536 SO_SNDBUF=65536
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

```

Seems ok...
Sorry to ask, but you did restart Samba?
Have you done anything to tweak the network settings on the Win-clients, ie. tcp window size? Yeah, I know they work fine on everything else, but just to rule out...

/Kasper

---

### Post by Ghost_Mazal on 2012-06-04
> **kmyram said:**
> Seems ok...
Sorry to ask, but you did restart Samba?
Have you done anything to tweak the network settings on the Win-clients, ie. tcp window size? Yeah, I know they work fine on everything else, but just to rule out...

/Kasper

Yup I did restart samba , and the whole server is restarted every day when it's cloned.

No , I haven't done any tweaking at the windows side.
I don't know what is that tcp window size you are referring to.

---

