---
title: "Ubuntu Home Server not Allowing connections"
date: 2017-03-23
forum: Server Platforms
---

### Post by vrubel68 on 2017-03-23
I set this server up a couple years ago with a raid on it and, until I updated to 14.04, it connected and shared just fine.  Now, for w/e reason, it's not allowing a connection.  I've tried purging the IPtables, disabling the firewall, reconfiguring Samba, resetting Nautilus, etc.  At this point, I've exhausted all the searches I've found.

Any tips?

smb.conf:
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

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

    security = share

    workgroup = WORKGROUP

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

    usershare owner only = false

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
;    passdb backend = tdbsam

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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Shares]
    comment = Shared Files
    path = /home/Shares
;    browsable = yes
    read only = no

[evocati]
    comment = Raid Array
    path = /media/evocati
;    browseable = yes
    guest ok = yes
;    writeable = No
    create mask = 775
;    directory maks = 0775





[Bulk Files]
    comment = Overflow
    path = /media/evocati/Bulk Files
    writeable = yes
;    browseable = yes
    guest ok = yes

[Network]
    comment = Server Files
    path = /media/evocati/279229b0-d042-40f7-b765-998d5f9647cb
    writeable = yes
;    browseable = yes
    guest ok = yes


```


IPtables:

```
evocati@evocati-desktop:~$ sudo iptables -L
[sudo] password for evocati: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere             ctstate INVALID
UDP        udp  --  anywhere             anywhere             ctstate NEW
TCP        tcp  --  anywhere             anywhere             tcp flags:FIN,SYN,RST,ACK/SYN ctstate NEW
ICMP       icmp --  anywhere             anywhere             ctstate NEW
REJECT     udp  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere             reject-with tcp-reset
REJECT     all  --  anywhere             anywhere             reject-with icmp-proto-unreachable

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ICMP (1 references)
target     prot opt source               destination         

Chain TCP (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh

Chain UDP (1 references)
target     prot opt source               destination 

 
```

/sigh.

---

### Post by wildmanne39 on 2017-03-23
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-03-23
What kind of connections exactly? Samba? SSH?

---

### Post by Morbius1 on 2017-03-23
Edit smb.conf and "comment out" the security line like this:
> # Change this to the workgroup/NT-domain name your Samba server will part of     [COLOR=#0000cd][B]
#[/B][/COLOR]security = share
Then restart smbd:
```
sudo service smbd restart
```
Share-level security no longer exists. It hasn't existed for years but in earlier versions of samba it would be ignored and replaced with "user". Today it prevents the smbd service from running.

If you comment out your existing line it will default to "auto" and samba itself will decide the appropriate security level on it's own.

[COLOR=#0000cd]*Side note: I can't help but think that the shares pointing to /media/evocati/XXX like this one will be a problem: *[/COLOR]
> [Bulk Files]
    comment = Overflow
    path = /media/evocati/Bulk Files
    read only = No
    guest ok = Yes
Unless your client is running Windows as the "evocati" user he will never get access to that share. It's not a Samba issue it's a Linux issue. You might consider changing the share definition to this:
> [Bulk Files]
    comment = Overflow
    path = /media/evocati/Bulk Files
    read only = No
    guest ok = Yes
    [COLOR=#0000cd]**force user = evocati**[/COLOR]
Then restart smbd again.

/media/$USER is a folder created by the system that allows only $USER from gaining access to what's under it. "force user" will fix that for those shares.

---

### Post by vrubel68 on 2017-03-23
> **darkod said:**
> What kind of connections exactly? Samba? SSH?
wierd..it won't allow any spaces in this window.

I'm using Samba.  It's a home LAN that was working just fine prior to the update.

---

### Post by vrubel68 on 2017-03-23
> **Morbius1 said:**
> Edit smb.conf and "comment out" the security line like this:

Then restart smbd:
```
sudo service smbd restart
```
Share-level security no longer exists. It hasn't existed for years but in earlier versions of samba it would be ignored and replaced with "user". Today it prevents the smbd service from running.

If you comment out your existing line it will default to "auto" and samba itself will decide the appropriate security level on it's own.

[COLOR=#0000cd]*Side note: I can't help but think that the shares pointing to /media/evocati/XXX like this one will be a problem: *[/COLOR]

Unless your client is running Windows as the "evocati" user he will never get access to that share. It's not a Samba issue it's a Linux issue. You might consider changing the share definition to this:

Then restart smbd again.

/media/$USER is a folder created by the system that allows only $USER from gaining access to what's under it. "force user" will fix that for those shares.

I'll change up my smb.conf when I get home.

Hrm, I didn't put that in there like that; that was the Samba GUI.  Additionally, I just logged in to the account from my windows computer (\\192.168.1.75\Bulk Files) and never had any issues prior.  The logic was to keep the kids from fooling with the server, so it would require credentials.  I don't have sufficient experience with Linux to be able to set the network up as I would prefer, so this may be very well be a haphazard arrangement with a far better (and cleaner) solution.


Edit:  I just re-read your post and realized what you meant.  It very well could be that the Samba GUI isn't posting the *[COLOR=#0000ff]force user = evocati[/COLOR] *to smb.conf and that's all that's required*.  *I didn't save the old configuration (like an idiot) prior to the update, so I am unable to verify prior syntax used.  I really hope that's it, though, as I spent 5 hours lastnight trying to get the network back up ](*,).

---

### Post by vrubel68 on 2017-03-23
```
evocati@evocati-desktop:~$ gksudo gedit /etc/samba/smb.conf

(gedit:3131): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
evocati@evocati-desktop:~$ sudo smbd stop
[sudo] password for evocati: 
evocati@evocati-desktop:~$ sudo smbd start
evocati@evocati-desktop:~$ sudo service smdb restart
smdb: unrecognized service
evocati@evocati-desktop:~$ sudo service smbd restart
stop: Unknown instance: 
smbd start/running, process 3262
evocati@evocati-desktop:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Shares]"
Processing section "[evocati]"
Processing section "[Bulk Files]"
Processing section "[Network]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Shares]
    comment = Shared Files
    path = /home/Shares
    read only = No


[evocati]
    comment = Raid Array
    path = /media/evocati
    create mask = 0775
    guest ok = Yes


[Bulk Files]
    comment = Overflow
    path = /media/evocati/Bulk Files
    force user = evocati
    read only = No
    guest ok = Yes


[Network]
    comment = Server Files
    path = /media/evocati/279229b0-d042-40f7-b765-998d5f9647cb
    force user = evocati
    read only = No
    guest ok = Yes
evocati@evocati-desktop:~$ 
```

Alright, I commented out the security item, and then inserted the force user line however, that didn't seem to address the issue.

Should the computer be seen on the network if I've made them visible via Nautilus and Samba?

---

### Post by Morbius1 on 2017-03-24
>  Should the computer be seen on the network if I've made them visible via Nautilus and Samba?                 
Yes but ......

It looks like you are also using Nautilus to share folders. Please post the output of the following command:
```
net usershare info --long
```
In the mean time edit smb.conf and right below the "workgroup = WORKGROUP" line add another one:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba in this exact order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
Then wait a few minutes. Restarting nmbd caused Windows to get confused for a few moments but it settles out in time.

By any chance are the Windows machines running Win10? Win10 can use a different method to resolve names.

And finally can your clients access the samba server by it's ip address?

---

### Post by vrubel68 on 2017-03-24
Wierd, I didn't get an email saying this had been responded too even though I'm subscribed :-/

> **Morbius1 said:**
> Yes but ......

It looks like you are also using Nautilus to share folders. Please post the output of the following command:
```
net usershare info --long
```

```


evocati@evocati-desktop:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/bulk files is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Pictures]
path=/home/evocati/Pictures
comment=
usershare_acl=Everyone:R,EVOCATI-DESKTOP\evocati:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/{3d553fbf-3e3d-4820-ba65-0570c25a7704} is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/network is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Linux]
path=/
comment=
usershare_acl=Everyone:R,EVOCATI-DESKTOP\evocati:F,
guest_ok=n


```



In the mean time edit smb.conf and right below the "workgroup = WORKGROUP" line add another one:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba in this exact order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
Then wait a few minutes. Restarting nmbd caused Windows to get confused for a few moments but it settles out in time.

By any chance are the Windows machines running Win10? Win10 can use a different method to resolve names.

And finally can your clients access the samba server by it's ip address?

Alright, I posted the code for the net usershare info --long posting.   It didn't like a bunch of the shares, but that's no surprise.

To answer your last question, no, all of the comps are using windows 7 and thus far I've been unable to actually connect to the server at all.  Most assuredly, the issue is entirely the linux configuration and not the windows systems; this issue came up AFTER I updated my server box to 14.04 after 5 years of having access to the drives over the network from any of the computers in the house via login (I didn't want the kids deleting/moving/altering files-folders).

I currently have it setup with a static internal IP address, but I don't recall what the add. search domain should be.  Does Home.lan sound accurate?

---

### Post by darkod on 2017-03-25
It might not be related, but similar strange thing happened with my samba shares when upgrading my home server from 12.04 to 14.04 few years ago. During the upgrade when it asked me about the smb.conf I told it to keep my version, which is what usually everyone does and I consider it the correct answer when doing OS upgrades.

But my shares didn't work after that even though it all looked good and correct. However I have much simpler configuration than yours, I have only few public shares and no pasword protection, so I simply kept a copy of my smb.conf, purged samba and reinstalled it (to create new default smb.conf for the new samba version coming with 14.04) and then simply pasted my share definitions in the new smb.conf without changing anything else (because the default smb.conf allows anonymous access if I'm not mistaken).

If you kept your smb.conf during the upgrade too, you might be facing something similar. But for you it will be more complicated to purge samba and start working with new default smb.conf only adding the parts you need from your old smb.conf. Because the point is not to replace it all, the point is to use the 14.04 smb.conf and add only necessary parts.

This issue during upgrade might be related with the fact that 12.04 was coming with samba v3 and 14.04 with v4 (unless I remember it wrong).

---

### Post by Morbius1 on 2017-03-25
More questions I'm afraid.

** Can the Windows machines ping the Linux machine by it's ip address:
```
ping some-ip-address
```
If it cannot disable the firewall on Linux:
```
sudo ufw disable
```
Then try to ping it again.

** What is the make and model of your router?

** Run testparm -s again and make sure there is no reference to "security = share" and that the "name resolve order" line shows up.

---

### Post by vrubel68 on 2017-03-25
Darko, I think you're entirely correct with regards to the Samba issue.  That's exactly what I did and that's what I started trying to adjust at first as I did exactly what you did in preserving my smb.conf though, I think I ended up purging the old one following one of the guides.  At this point, though, I copy the file (smb.conf.old) and leave it in the samba folder just as a reminder to myself.  as far as version go, I have no idea.  I didn't keep up on changes, but you're probably right considering the issues.

---

### Post by vrubel68 on 2017-03-25
> **Morbius1 said:**
> More questions I'm afraid.

** Can the Windows machines ping the Linux machine by it's ip address:
```
ping some-ip-address
```
If it cannot disable the firewall on Linux:
```
sudo ufw disable
```
Then try to ping it again.

** What is the make and model of your router?

** Run testparm -s again and make sure there is no reference to "security = share" and that the "name resolve order" line shows up.

```

C:\Windows\System32>ping 192.168.1.75


Pinging 192.168.1.75 with 32 bytes of data:
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.


Ping statistics for 192.168.1.75:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Windows\System32> 
```

After the firewall disable in terminal (I had disabled the firewall through the GUI just after the update but just in case I went ahead and did the terminal, as well), windows is still unable to ping the computer:

```
 [...]C:\Windows\System32>ping 192.168.1.121


Pinging 192.168.1.121 with 32 bytes of data:
Reply from 192.168.1.121: bytes=32 time<1ms TTL=128
Reply from 192.168.1.121: bytes=32 time<1ms TTL=128
Reply from 192.168.1.121: bytes=32 time<1ms TTL=128
Reply from 192.168.1.121: bytes=32 time<1ms TTL=128


Ping statistics for 192.168.1.121:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms


C:\Windows\System32> 
```

My router is a Linksys e3000 (which has neither been reset nor powered off since the update)

Testparm -s doesn't show the *[COLOR=#0000cd]security = share  [/COLOR][COLOR=#0000cd][/COLOR][COLOR=#0000cd][/COLOR]*, however the resolve line didn't show up.  It may be that I placed it in the wrong spot or placed too many much space below it (the syntax isn't clear)

```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

#    security = share

    workgroup = workgroup

    name resolve order = bcast host lmhosts wins

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

```

---

### Post by Morbius1 on 2017-03-25
I don't know about any of the other posters in this thread but I'm getting more and more confused.

You said you assigned a static ip address to  this box:
> I currently have it setup with a static internal IP address
When you try to ping it there is a problem:
> Reply from 192.168.1.75: Destination protocol unreachable.
When you turn off the firewall you can ping it - or at least you can ping something - but with another ip address:
> Reply from 192.168.1.121: bytes=32 time<1ms TTL=128

I know what I would do at this point:

** However you assigned the static ip address on the Linux box I would undo it so that network-manager is set to **Automatic ( DHCP )** again.

** Page 16 of the users manual for this router talks about **DHCP Reservation**. That allows the router to assign the exact same ip address to that Linux box every time that box boots without you having to do anything within Ubuntu itself

---

### Post by vrubel68 on 2017-03-25
my apologies for the confusion; the 192.168.1.121 is the windows box and shoudn't have been added to the code (I was pinging to check the connection to the router).

> 
I know what I would do at this point:

** However you assigned the static ip address on the Linux box I would undo it so that network-manager is set to **Automatic ( DHCP )** again.

** Page 16 of the users manual for this router talks about **DHCP Reservation**.  That allows the router to assign the exact same ip address to that  Linux box every time that box boots without you having to do anything  within Ubuntu itself



I did this lastnight, as well, and the connection issue persisted (though, I didn't think to ping on a floating IP, so I'll try that in a moment).  I'll address the DHCP reservation on the router shortly.

---

### Post by vrubel68 on 2017-03-25
I did a traceroute from the ubuntu box to the windows box (192,168.1.132 is the new automatic IP address and 192.168.1.121 is the windows box) and received the following:

```

evocati@evocati-desktop:~$ traceroute 192.168.1.121
traceroute to 192.168.1.121 (192.168.1.121), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
evocati@evocati-desktop:~$ 

```

And here's the traceroute to the Router:
```

evocati@evocati-desktop:~$ traceroute 192.168.1.1
traceroute to 192.168.1.1 (192.168.1.1), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.421 ms  0.492 ms  0.605 ms
evocati@evocati-desktop:~$ ^C

```

so, even with an automatic DHCP in IPv4 (set via wired connection in the GUI), it's still not making a connection.  Altering the router may not even make any difference as the connection is made through a Powerconnect 3324 24 port switcher.

---

### Post by Morbius1 on 2017-03-25
> Altering the router may not even make any difference as the connection is made through a Powerconnect 3324 24 port switcher. 				
That's it for me folks.

---

### Post by vrubel68 on 2017-03-25
Well, I appreciate your help anyways.

/sigh

This just goes to reinforce the idea:  If's it's not broken, don't fix it.  Updates only seem to break things.

---

### Post by darkod on 2017-03-25
Hold on, lets take a deep breath, and focus on networking now. Honestly I never thought about it so far because ping is really the first thing you should try... :)

I would forget about IP reservations and use plain old static IP on the server, the way it should be. Another clarification, you are running Desktop version in fact, right? But even if you are, Network Manager has option in the GUI for static IP. In such case you forget about /etc/network/interfaces (did you change something in it manually?) and use only NM to set the static IP.

After you set it and reboot (I have found that restarting the networking service doesn't work sometimes) check ping to the router first, and then to any other machine in the LAN. Report back...

---

### Post by vrubel68 on 2017-03-25
Darko,
  Aye, after your comment, I went and grabbed my other e3000 router to simplify things.  AND you're completely correct in thinking that there's issues on both boxes (both are coming back with "Destination Protocol Unreacheable" for any IP address on the network outside of the router (192.168.1.1).  I'll worry about the windows box seperately as I have 4 other computers I can use.

Yes, I'm using desktop 14.04 and I had originally used Network Manager to assign the static IP at 192.168.1.75.  I'll reset that again, reboot and then check /etc/network/interfaces to see if they align.

---

### Post by vrubel68 on 2017-03-25
after resetting the IP to static I compared to /etc/network/interfaces and found this:

```

auto lo
iface lo inet loopback

```

It's not clear to me what this means, though.  I haven't altered this previously so w/e this is, Ubu did it. ;-)

Also:

[i.imgur.com/3v8238c.png]("http://i.imgur.com/3v8238c.png")

---

### Post by darkod on 2017-03-25
The lo interface is the built-in loopback interface. That is normal...

So right now can you ping 192.168.1.1 from the ubuntu server/desktop?

---

### Post by vrubel68 on 2017-03-25
Yes.

```

evocati@evocati-desktop:~$ traceroute 192.168.1.1
traceroute to 192.168.1.1 (192.168.1.1), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.441 ms  0.512 ms  0.864 ms
evocati@evocati-desktop:~$ 



```

I just did a reset, as well.

---

### Post by darkod on 2017-03-25
Test ping to outside and dns lookup from the ubuntu desktop:
```
ping -c 4 8.8.8.8
nslookup google.com
```

From other machines in the LAN can you ping 192.168.1.75?

---

### Post by vrubel68 on 2017-03-25
```

evocati@evocati-desktop:~$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=45 time=20.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=45 time=22.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=45 time=22.2 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=45 time=20.9 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 20.540/21.631/22.752/0.910 ms
evocati@evocati-desktop:~$ nslookup google.com
Server:        127.0.1.1
Address:    127.0.1.1#53

Non-authoritative answer:
Name:    google.com
Address: 172.217.3.174

evocati@evocati-desktop:~$ 

```

The ping from windows come back as Detination protocol unreacheable:

```

C:\Windows\System32>ping 192.168.1.75


Pinging 192.168.1.75 with 32 bytes of data:
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.


Ping statistics for 192.168.1.75:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),


C:\Windows\System32>

```

---

### Post by darkod on 2017-03-25
From the same windows do you have ping to the router 192.168.1.1? You have to establish if the failure is from windows to LAN or from LAN to ubuntu desktop.

PS. Your ubuntu desktop connectivity looks good, you have ping to outside and dns is working fine. To check iptables status run:
```
sudo iptables -L -n -v
```
Post the output.

---

### Post by vrubel68 on 2017-03-25
```

evocati@evocati-desktop:~$ sudo iptables -L -n -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
16165 8170K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
 1406 89427 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
   18   720 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
 9537 3044K UDP        udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
 1665 84360 TCP        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp flags:0x17/0x02 ctstate NEW
  130  4776 ICMP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
 9537 3044K REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable
 1665 84360 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with tcp-reset
  248  8316 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-proto-unreachable

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 19740 packets, 3463K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ICMP (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain TCP (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22

Chain UDP (1 references)
 pkts bytes target     prot opt in     out     source               destination         
evocati@evocati-desktop:~$ 


```

It's not clear to me what that all means, but the last three stand out in the upper section (REJECT; proto unreacheable).

---

### Post by darkod on 2017-03-25
You have a firewall on it. Look at the chain titles: INPUT (policy DROP...), FORWARD (policy DROP...)

By default no firewall is active. Some application you installed or tutorial you followed set this up. I think you can temporarily test by turning it off, but long term you will need to investigate what set this up and if it's safe to turn it off. If the server is on a local LAN why would you need a firewall at all? Your router usually has integrated firewall and no other firewalls are needed. Because you have issues like this one when even local LAN machines can't connect and use applications correctly.

If I'm not mistaken to temporarily test you will need to set ACCEPT policy and then flush the current rules. After that run the list again and check results:
```
sudo iptables -P INPUT ACCEPT
sudo iptables -F INPUT
sudo iptables -L -n -v
```

Then check ping to 192.168.1.75 again.

---

### Post by vrubel68 on 2017-03-25
> **darkod said:**
> You have a firewall on it. Look at the chain titles: INPUT (policy DROP...), FORWARD (policy DROP...)

By default no firewall is active. Some application you installed or tutorial you followed set this up. I think you can temporarily test by turning it off, but long term you will need to investigate what set this up and if it's safe to turn it off. If the server is on a local LAN why would you need a firewall at all? Your router usually has integrated firewall and no other firewalls are needed. Because you have issues like this one when even local LAN machines can't connect and use applications correctly.

If I'm not mistaken to temporarily test you will need to set ACCEPT policy and then flush the current rules. After that run the list again and check results:
```
sudo iptables -P INPUT ACCEPT
sudo iptables -F INPUT
sudo iptables -L -n -v
```

Then check ping to 192.168.1.75 again.

What the deuce?!?  

[http://i.imgur.com/jJzELNv.png](http://i.imgur.com/jJzELNv.png)

```

evocati@evocati-desktop:~$ sudo iptables -L -n -v
Chain INPUT (policy ACCEPT 52 packets, 10254 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 29 packets, 2560 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ICMP (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain TCP (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22

Chain UDP (0 references)
 pkts bytes target     prot opt in     out     source               destination         
evocati@evocati-desktop:~$ 


```

and here's the ping from the windows box:

```
C:\Windows\System32>ping 192.168.1.75


Pinging 192.168.1.75 with 32 bytes of data:
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.
Reply from 192.168.1.75: Destination protocol unreachable.


Ping statistics for 192.168.1.75:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
C:\Windows\System32>


```

It would appear that Gufw Firewall doesn't inherently alter the iptables even when specified to do so.  That's annoying.

As a bonus though!  

[http://i.imgur.com/Qqd7HZy.png](http://i.imgur.com/Qqd7HZy.png)

```

evocati@evocati-desktop:~$ traceroute 192.168.1.122
traceroute to 192.168.1.122 (192.168.1.122), 30 hops max, 60 byte packets
 1  evocati-desktop.local (192.168.1.75)  2998.367 ms !H  2998.328 ms !H  2998.319 ms !H
evocati@evocati-desktop:~$

```

---

### Post by vrubel68 on 2017-03-26
YAY!!!!

[http://i.imgur.com/MHQ7Crn.png](http://i.imgur.com/MHQ7Crn.png)

Fantastic!  Thank you for your help everyone, and special kudo-props go to Darkod for helping sort out the IP/Firewall issue.  I'll have to keep the GuFw issue in the back of my mind when I deal with again.


I guess the last issue I really have is more of an inconvenience, really.  I'll have to post that in a new thread... cause this is solved!

---

### Post by vrubel68 on 2017-03-26
For any that are following up with iptables issues, the code from above (and copied here) will set the new rules to open the server up:

```

sudo iptables -P INPUT ACCEPT
sudo iptables -F INPUT
sudo iptables -L -n -v

```

Partially for my benefit:
The first command defines the protocol used (option -P) as INPUT (intraffic) and changes the rule to ACCEPT (allow all in traffic)
The second rule (-F) Flushes the INPUT Chain (sub rules, ports, size limitations, source, etc).  This, in effect, makes all in traffic set to what ever the Protocol was defined as.
The third command (-L -n -v) Lists all Protocols (-L) with the chains attached to each protocol (-n) and in totality (-v, verbose).


So, once this is all done, we have to save it since all terminal commands are ephermeral.  To do this, ensure that we have persistent iptables installed:

```

sudo apt-get install iptables-persistent


```

Once those are installed (or confirmed installed), we need to save our new rules.  We do this with the following command string:

```

sudo invoke-rc.d iptables-persistent save

```

At this point, our iptables are now set to w/e rule we installed above (accept/reject, special chains, w/e) thus ensuring that if we reboot, we won't have to reset the rules again.

---

