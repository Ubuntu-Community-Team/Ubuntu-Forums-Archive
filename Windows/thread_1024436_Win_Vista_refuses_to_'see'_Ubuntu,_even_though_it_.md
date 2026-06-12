---
title: "Win Vista refuses to 'see' Ubuntu, even though it grants Ubuntu internet use"
date: 2008-12-29
forum: Windows
---

### Post by cabbiinc on 2008-12-29
Hello. Lets get too it. I have two computers networked via Lan to each other, with the Vista machine connected to DSL modem via USB. The Vista machine allows Ubuntu to use the internet through Vista but Vista just refuses to 'see' the Ubuntu machine in the Network Connections window. Ubuntu can see the Vista machine but not browse any folders.

I can ping Ubuntu rather successfully.
I think I have activated Samba (right clicked a file on the desktop in Ubuntu and shared, it did some stuff and said it was all good).
I have gone through the Vista wizards enough times I could probably write out what all the steps it takes you in a circle doing. Although I'm not opposed to doing them over again.
Zone Alarm has Ubuntu's IP set to Trusted.

Any advice?

---

### Post by Nessa on 2008-12-29
What filesystem did you use? Windows doesn't read ext3. You have to install an ext3 driver so it can "see" your Ubuntu installation.

---

### Post by tsali on 2008-12-29
This isn't a Vista issue.

I don't think Ubuntu installs with a Samba server by default. It will let you VIEW shares on a Windows network, but sharing your own files on that network is a different affair.

Try:

1) In Ubuntu, select the folder you want to share and right-click to select "Properties"

2) You will see the last tab to the right at the top - "Share"

3) Click "Share this folder". It will offer to install the sharing service for you. Follow the prompts from that point.

---

### Post by cabbiinc on 2008-12-29
> **tsali said:**
> This isn't a Vista issue.

I don't think Ubuntu installs with a Samba server by default. It will let you VIEW shares on a Windows network, but sharing your own files on that network is a different affair.

Try:

1) In Ubuntu, select the folder you want to share and right-click to select "Properties"

2) You will see the last tab to the right at the top - "Share"

3) Click "Share this folder". It will offer to install the sharing service for you. Follow the prompts from that point.

Yes I did that trying to get Vista to share the internet connection.

---

### Post by cabbiinc on 2008-12-29
> **Nessa said:**
> What filesystem did you use? Windows doesn't read ext3. You have to install an ext3 driver so it can "see" your Ubuntu installation.

Greetings. Would this [http://www.fs-driver.org/](http://www.fs-driver.org/) work?

---

### Post by rickyjones on 2008-12-29
> **cabbiinc said:**
> Greetings. Would this [http://www.fs-driver.org/](http://www.fs-driver.org/) work?

Remote file systems do not matter when you are viewing over the network - at that point SMB is used.

Have you tried to completely disable ZoneAlarm? Even if the Ubuntu IP is set to trusted I've seen ZoneAlarm cause issues.

Thanks,
Richard

---

### Post by jonandrews on 2008-12-29
RickyJones is absolutely correct - the file system in use by each machine is completely irrelevant to networking issues. I have a home network with Ubuntu (ext3), XP (NTFS), Solaris (XFS) and Mac (??) machines all networked together without reference to file systems. Have a look at my networking guide, which gives a step by step guide to setting up Ubuntu so it is fully accessible to windows pc's: 
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by albinootje on 2008-12-29
> **cabbiinc said:**
> 
I think I have activated Samba (right clicked a file on the desktop in Ubuntu and shared, it did some stuff and said it was all good).

Do you use the same WORKGROUP ?
See : /etc/samba/smb.conf

One other thing that can help is to make sure that all machine can reach the other machines by hostname.

---

### Post by cabbiinc on 2008-12-29
> **jonandrews said:**
> RickyJones is absolutely correct - the file system in use by each machine is completely irrelevant to networking issues. I have a home network with Ubuntu (ext3), XP (NTFS), Solaris (XFS) and Mac (??) machines all networked together without reference to file systems. Have a look at my networking guide, which gives a step by step guide to setting up Ubuntu so it is fully accessible to windows pc's: 
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

On step 4 of your guide [http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm](http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm) I can't even see the Ubuntu machine, even with ZoneAlarm turned off. I am using Vista, which from what I've seen on other forums, networks differently than XP.

---

### Post by rickyjones on 2008-12-29
> **cabbiinc said:**
> On step 4 of your guide [http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm](http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm) I can't even see the Ubuntu machine, even with ZoneAlarm turned off. I am using Vista, which from what I've seen on other forums, networks differently than XP.

Networking is networking is networking. 

1. Be sure that you are in the same subnet. Example, same IPs with the last number being different. Same subnet mask.

2. Verify that you can ping each machine via the IP. Worry about name resolution at another time.

3. Ensure that Folder and Printer Sharing is enabled on Vista. If I recall correctly it is disabled by default and this prevents Vista from seeing other computers.

4. Ensure that in Vista that your network is configured as a Home network so that you can discover other computers.

If all steps are successful then I'd be a little stumped as well. 

Thanks,
Richard

---

### Post by cabbiinc on 2008-12-29
> **rickyjones said:**
> Networking is networking is networking. 

1. Be sure that you are in the same subnet. Example, same IPs with the last number being different. Same subnet mask.

2. Verify that you can ping each machine via the IP. Worry about name resolution at another time.

3. Ensure that Folder and Printer Sharing is enabled on Vista. If I recall correctly it is disabled by default and this prevents Vista from seeing other computers.

4. Ensure that in Vista that your network is configured as a Home network so that you can discover other computers.

If all steps are successful then I'd be a little stumped as well. 

Thanks,
Richard

1. Yep, double checked that, but things change sometimes since I don't know how to make Vista a static IP.

2. Ping ping ping. They ping each other without a hitch.

3+4.
[IMG]http://farm4.static.flickr.com/3218/3148527424_d3966b46c9_o.jpg[/IMG]

---

### Post by cabbiinc on 2008-12-29
To add, on the Vista machine I did this in Command Prompt:

```
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Dan>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : pinkfloyd
   Primary Dns Suffix  . . . . . . . : Vista
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Vista
                                       domain.actdsltmp

Ethernet adapter Network Bridge:

   Connection-specific DNS Suffix  . : domain.actdsltmp
   Description . . . . . . . . . . . : MAC Bridge Miniport
   Physical Address. . . . . . . . . : 02-19-D1-40-10-74
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.6(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, December 29, 2008 8:45:42 AM
   Lease Expires . . . . . . . . . . : Tuesday, December 30, 2008 8:45:45 AM
   Default Gateway . . . . . . . . . : 192.168.0.2
   DHCP Server . . . . . . . . . . . : 192.168.0.2
   DNS Servers . . . . . . . . . . . : 192.168.0.2
                                       205.171.3.25
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 00-17-9A-2B-42-BC
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


```

Bluetooth adapter doesn't really go anywhere.

On the Ethernet adapter Network Bridge the IPv4 is the Vista computers address and I don't see the Ubuntu's address anywhere 192.168.0.43.

---

### Post by cabbiinc on 2008-12-29
> **albinootje said:**
> Do you use the same WORKGROUP ?
See : /etc/samba/smb.conf

One other thing that can help is to make sure that all machine can reach the other machines by hostname.

Do I put that in terminal? I only get
```
 /etc/samba/smb.conf: command not found
```

Don't know the hostname.

---

### Post by albinootje on 2008-12-29
> **cabbiinc said:**
> Do I put that in terminal? I only get
```
 /etc/samba/smb.conf: command not found
```

Don't know the hostname.

Yes, open a terminal, and do the following :
```

sudo gedit /etc/samba/smb.conf

```
Search for WORKGROUP in the beginning of that file.

Perhaps you have to install samba, because I'm not sure whether the package samba-common or the package samba supplies /etc/samba/smb.conf
```

sudo apt-get install samba

```

---

### Post by cabbiinc on 2008-12-29
> **albinootje said:**
> Yes, open a terminal, and do the following :
```

sudo gedit /etc/samba/smb.conf

```
Search for WORKGROUP in the beginning of that file.

Perhaps you have to install samba, because I'm not sure whether the package samba-common or the package samba supplies /etc/samba/smb.conf
```

sudo apt-get install samba

```

I've gone to some lengths to install Samba. When I was trying to get internet on the Ubuntu machine I tried installing it.

When I do your code [sudo gedit /etc/samba/smb.conf] I get a very long text file explaining what Samba is.

Should I go ahead with the second code you provided?

---

### Post by albinootje on 2008-12-29
> **cabbiinc said:**
> I've gone to some lengths to install Samba. When I was trying to get internet on the Ubuntu machine I tried installing it.

When I do your code [sudo gedit /etc/samba/smb.conf] I get a very long text file explaining what Samba is.

Should I go ahead with the second code you provided?

No, having that long text is fine.
You should search there for this text :

> 
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

And see whether the workgroup name is correct or not.

---

### Post by cabbiinc on 2008-12-29
> # Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP 

That is in that long text that came up. Am I missing something/supposed to do something? You can tell me if this is user error, I can take it.

---

### Post by albinootje on 2008-12-29
> **cabbiinc said:**
> That is in that long text that came up. Am I missing something/supposed to do something? You can tell me if this is user error, I can take it.

You should compare that with the "workgroup" you have on your Windows machine(s).

---

### Post by cabbiinc on 2008-12-29
> **albinootje said:**
> You should compare that with the "workgroup" you have on your Windows machine(s).

I'm sorry, I'm not making the connection here. My Vista machine's workgroup is set to workgroup, and I think the Ubuntu machine is set to workgroup as well.

---

### Post by albinootje on 2008-12-29
> **cabbiinc said:**
> I'm sorry, I'm not making the connection here. My Vista machine's workgroup is set to workgroup, and I think the Ubuntu machine is set to workgroup as well.

Okay, excellent, then we don't have to worry about that.

---

### Post by Battie on 2008-12-29
Sorry if this isn't helpful, but have we addressed HOW you're trying to see the samba share?  It's been a few years since I've used one, but do you still have to type smb:\\<name> in the explorer address bar?

---

### Post by rickyjones on 2008-12-29
> **Battie said:**
> Sorry if this isn't helpful, but have we addressed HOW you're trying to see the samba share?  It's been a few years since I've used one, but do you still have to type smb:\\<name> in the explorer address bar?

Please note that the above will NOT work in Windows. 

In Windows you can access SMB shares using the full UNC path in the explorer address bar, or from the Start > Run prompt.

Example: \\server\share

Thanks,
Richard

---

### Post by cabbiinc on 2008-12-29
Would running a Live CD (Ubuntu 8.04) temporarily on the Vista machine to diagnose the Ubuntu machine be pointless?

---

### Post by cabbiinc on 2008-12-30
> **cabbiinc said:**
> Would running a Live CD (Ubuntu 8.04) temporarily on the Vista machine to diagnose the Ubuntu machine be pointless?

bump

---

### Post by tsali on 2008-12-30
Some things I do know:

1) Trying to browse the Vista share from the Ubuntu machine is problematic with Nautilus. Try tksmb. This works for me for some reason.

2) Post your smb.conf file so we can see how you have your security structure and shares defined.

---

### Post by cabbiinc on 2008-12-30
> **tsali said:**
> Some things I do know:

1) Trying to browse the Vista share from the Ubuntu machine is problematic with Nautilus. Try tksmb. This works for me for some reason.

2) Post your smb.conf file so we can see how you have your security structure and shares defined.



I don't know how to try tksmb.

```
sudo gedit /etc/samba/smb.conf
``` opened a new window that displayed this



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
   workgroup = MSHOME

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



Thanks

---

### Post by tsali on 2008-12-30
Ok...nothing wrong with your smb.conf that I can see. It looks just like mine and I can see the folders I've shared on my Vista machine just fine.

When you created the share, did you you click the option to enable guest access?

Also, are you trying to share an entire user HOME folder? I think these have special rules.

Using tksmb...you install tksmb via synaptic. It's a network file browser.

---

### Post by cabbiinc on 2008-12-30
> **tsali said:**
> Ok...nothing wrong with your smb.conf that I can see. It looks just like mine and I can see the folders I've shared on my Vista machine just fine.

When you created the share, did you you click the option to enable guest access?

Also, are you trying to share an entire user HOME folder? I think these have special rules.

Using tksmb...you install tksmb via synaptic. It's a network file browser.

Alright, I started tksmb through synaptic without a hitch. I took the folder on the desktop of Ubuntu and reshared it just for good measure. I tried to go to places > Vista machine [by it's name] but no luck. I also tried to go to Places > Connect to Server > Windows Share but I'm feeling a little clueless as to what to put in all the fields.

I came back to the Vista machine and tried to find the Ubuntu machine, no luck.

I can still ping Ubuntu from Vista and vice versa.

In Vista I tried

```
Nbstat -c

    
Network Bridge:
Node IpAddress: [192.168.0.6] Scope Id: []



                  NetBIOS Remote Cache Name Table



        Name              Type       Host Address    Life [sec]

    ------------------------------------------------------------

    SABRYNASCOMPUTE<20>  UNIQUE          192.168.0.43        127

    
Bluetooth Network Connection:
Node IpAddress: [0.0.0.0] Scope Id: []



    No names in cache


```

But Vista still refuses to acknowledge that Ubuntu (SABRYNASCOMPUTE<20>) exists.

Thanks for all the help so far.

---

### Post by rickyjones on 2008-12-31
Have you tried a UNC path using the Ubuntu systems' IP address?

Start > Run > type in "\\IP" and then hit Enter?

Thanks,
Richard

---

### Post by cabbiinc on 2008-12-31
> **rickyjones said:**
> Have you tried a UNC path using the Ubuntu systems' IP address?

Start > Run > type in "\\IP" and then hit Enter?

Thanks,
Richard

I tried both \\192.168.0.43 and \\ 192.168.0.43 as well as both with //.
All give me the error "The filename, directory name, or volume label syntax is incorrect".
Heck I even tried putting " around it with no joy.

Thanks
Dan

---

### Post by rickyjones on 2008-12-31
> **cabbiinc said:**
> I tried both \\192.168.0.43 and \\ 192.168.0.43 as well as both with //.
All give me the error "The filename, directory name, or volume label syntax is incorrect".
Heck I even tried putting " around it with no joy.

Thanks
Dan

That is a very odd error message. It sounds like Vista isn't recognizing that as a UNC path.

Open up a command prompt and type the command (without quotes): "net view \\IP"

Thanks,
Richard

---

### Post by cabbiinc on 2008-12-31
> **rickyjones said:**
> That is a very odd error message. It sounds like Vista isn't recognizing that as a UNC path.

Open up a command prompt and type the command (without quotes): "net view \\IP"

Thanks,
Richard

```
net view \\IP
System error 53 has occurred

The network path was not found
```

Which just makes me think it's in the Vista machine.
FYI I've submitted a help request to M$. They sent back an email suggesting that I do exactly as I had told them I did with no luck. :lolflag: So I tried it again and sent them the error log, we'll see what they have to say :popcorn:

---

### Post by cabbiinc on 2009-01-01
> **tsali said:**
> 

...When you created the share, did you you click the option to enable guest access?



No, I forgot that. Went back and checked and nope, it wasn't enabled.

Still couldn't connect to Ubuntu from Vista though. So I started screwing around in the Command prompt. I did lots of things. I can now somewhat connect to Ubuntu from Vista, but not the other way around. I THINK what worked was
```
net use \\{IP address}
```
But I'm not sure. Now if I type in the IP address I can browse the shared folders of Ubuntu. But Vista still says there's nothing there if I look in the Network and Sharing Center > View computers and devices folder.

Seems pretty stupid to me.

---

### Post by cabbiinc on 2009-01-01
> **rickyjones said:**
> Networking is networking is networking. 


Well according to this page [http://www.home-network-help.com/vista-network-map.html](http://www.home-network-help.com/vista-network-map.html) no it's not when talking about Vista. LLTD play a roll in it. Apparently I'm not the only one who ran into this [http://ubuntuforums.org/showthread.php?t=959227&highlight=lltd](http://ubuntuforums.org/showthread.php?t=959227&highlight=lltd)

---

### Post by rickyjones on 2009-01-01
> **cabbiinc said:**
> ```
net view \\IP
System error 53 has occurred

The network path was not found
```

Which just makes me think it's in the Vista machine.
FYI I've submitted a help request to M$. They sent back an email suggesting that I do exactly as I had told them I did with no luck. :lolflag: So I tried it again and sent them the error log, we'll see what they have to say :popcorn:

In your command prompt did you literally type "new view \\IP"? I probably should have mentioned that you need to replace IP with the IP address of the machine you are trying to connect to. 

Example: new view \\192.168.1.1

This should get you some additional information.

Thanks,
Richard

---

### Post by cabbiinc on 2009-01-01
> **rickyjones said:**
> In your command prompt did you literally type "new view \\IP"? I probably should have mentioned that you need to replace IP with the IP address of the machine you are trying to connect to. 

Example: new view \\192.168.1.1

This should get you some additional information.

Thanks,
Richard

I did put the real IP address in place of "IP" with no joy. The command line "net use \\{the real IP address}" is what I think unlocked it. Vista hung for a good 60 seconds before saying "The command completed successfully". After that I could use the net view (possibly a coincidence, but that's what seemed to unlock things in my mind).

Now I can put the \\IP address into the address bar for windows expolorer, and it will accept it and show me the shared folders, but it still acts like its not there when you view the network computers.

[IMG]http://farm4.static.flickr.com/3097/3156749585_69bc5dcb54_o.jpg[/IMG]

You can see it in the tree but it doesn't have an icon in the Network folder, and if you navigate away from that it won't stay in the tree either.

Thanks
Dan

---

### Post by cabbiinc on 2009-01-02
So can someone tell me just what exactly to put in the fields when I try to connect to server in Ubuntu?

---

### Post by cabbiinc on 2009-01-05
So should I just concede that Windows Vista is a superior OS and I should just install that on the Ubuntu machine? 

At least I could get the file sharing to work.

---

### Post by cabbiinc on 2009-01-09
I have samba on, I have nautilus on, what else do I need to do to Ubuntu?

---

### Post by cabbiinc on 2009-02-02
How do I mark this as solved? Not that it is, I just give up. It can not be done, Ubuntu sucks just as bad as Vista apparently.

---

### Post by swoll1980 on 2009-02-02
restart your vista comp, also set up a samba password
```
sudo smbpasswd -a "user name"
```
also make sure guest account in vista is activated. If your using a firewall that's not windows firewall make sure the file sharing ports are open. Are you using a router, or a switch? if your using a switch make sure the 2 aren't using the same ip address. Networking is more complicating than most people think, and there are a hundred little things that could cause problems. If your using a router is the modem configured properly for the use of a router? If every networking issue could be addressed with point, and click we wouldn't have tens of thousands of network administrators.

---

