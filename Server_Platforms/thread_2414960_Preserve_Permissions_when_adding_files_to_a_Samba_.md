---
title: "Preserve Permissions when adding files to a Samba share"
date: 2019-03-18
forum: Server Platforms
---

### Post by leetbacoon on 2019-03-18
I have a Mac (El Capitan 10.11.6) client that is connected to an Ubuntu server (18.04.1 LTS) running Samba, sharing a ZFS pool. Everything works great, except that whenever I add a file to the server, the permissions are changed.

 For example, here's foo.txt on the mac:
 
```
$ ls -l foo.txt
-rw-r--r--  1 leetbacoon  staff  160 Feb 21 15:37 foo.txt
```

When it is clicked and dragged to the server, the server copy changes the attributes:

 ```
$ ls -l /Volumes/SMB\ Share/foo.txt
-rwx------  1 leetbacoon  staff  160 Feb 21 15:37 /Volumes/SMB\ Share/foo.txt*
```

Copying the file from the server back to my Mac retains those permissions:
 ```
$ ls -l ./Copied\ From\ Server/foo.txt
-rwx------  1 leetbacoon  staff  160 Feb 21 15:37 ./Copied\ From\ Server/foo.txt*
```

I want to have the file permissions retained when copying to the server, i.e.:
 
```
$ ls -l /Volumes/SMB\ Share/foo.txt
-rw-r--r--  1 leetbacoon  staff  160 Feb 21 15:37 /Volumes/SMB\ Share/foo.txt
```

All the ls -l commands were executed on the Mac client.
 
Here is my /etc/samba/smb.conf file:

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

mangled names = no
unix charset = UTF-8
dos charset = CP850
access based share enum = yes

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

#[printers]
#   comment = All Printers
#   browseable = no
#   path = /var/spool/samba
#   printable = yes
#   guest ok = no
#   read only = yes
#   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
#[print$]
#   comment = Printer Drivers
#   path = /var/lib/samba/printers
#   browseable = yes
#   read only = yes
#   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

## Shared folders

[SMB Share]
 comment = SMB Share
 path = /smbshare
 browseable = yes
 read only = no
 guest ok = no
```
 
Thanks friends ):P

---

### Post by TheFu on 2019-03-18
Samba handles file permissions without regard to any native permissions.

If you want native permissions for shared storage, use NFS. NFS is the native file sharing protocol for all Unix-like systems, including OSX and Linux.  NFS mounted storage honors users, groups, permissions, umasks, hardlinks, symbolic links, pipes, pretty much anything that a locally connected disk uses.

But there is 1 difference.  By default, root on a remote system has no special access on NFS storage.  Only the local 'root' user actually has root authority. There is an override for this, but it is seldom used or needed.

[https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/](https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/) - an OSX NFS client guide.
There are many Ubuntu NFS server guides.

Let me know if you'd like a little more info. There is 1 or 2 important things that will impact your OSX setup to make NFS work nicely, but it isn't worth my time to explain if you aren't going to use it.

---

### Post by Morbius1 on 2019-03-18
I know you said this didn't work but I think I know why because I've been able to reproduce it myself.

If you access the private share then go to the server and add these lines to the [SMB Share] share:
```
ea support = yes
vfs objects = catia fruit streams_xattr

```
Then do an ls -l /Volumes/SMB\ Share/foo.txt nothing has changed. It still shows rwx------.

You need to disconnect from the share in Finder then reconnect. You should now see rwxr--r--.

---

### Post by leetbacoon on 2019-03-18
I tried your suggestion Morbius and copying a -rw-r--r-- file to the server does keep it -rw-r--r-- (i forgot to actually *disconnect* through Finder, sorry) however if i copy a -rwxrwxrwx file to the server it changes the permissions to -rw-rwxrwx. If there's a way to get that to work too then I'm set

TheFu,  I apprerciate your answer as well, however I also need to use Time  Machine over this, and afaik Time Machine only allows SMB & AFP.

---

### Post by Morbius1 on 2019-03-19
Add another option to your [SMB Share] share definition:
```
map archive = No
```

Restart smbd:
```
sudo service smbd restart
```

And remember to disconnect from the server in Finder then reconnect.

[COLOR=#0000cd][I]Side note: You may be a bit too early to try to use Samba as a Time Machine repository. I have seen it done in HowTo's but all of the bells, whistles, and constraints required for TM really isn't in Samba until I think Samba Version 4.8 - and I've already seen bug reports about it .....

In any event I have never done it and despite what some folks might say behind my back I only post what I know and that only comes from doing it myself.[/I][/COLOR]

---

### Post by leetbacoon on 2019-03-21
Ah, yes, thank you Morbius! Works like a dream. I'll link this post as the answer over on ask ubuntu.

Regarding Time Machine, if i recall correctly, SMB is recommended nowadays to be used instead of AFP, even with Time Machine. My plan was to use both AFP (netatalk+avahi) and SMB on the same computer and share the same drive, also using Time Machine with Macs from Leopard, 10.5 to Mojave, 10.14. Maybe things have changed in recent years?

Really if I can use just SMB with Leopard through Mojave with Time Machine then I'm set.

Additionally, would you happen to know a few bugs people have reported? For the record I plan on storing files with names most people wouldn't all at once, like names with arabic characters, russian characters, chinese, korean, greek, et cetera. I hope this won't be an issue.


=============================================================================


One last thing. I was reading [this article on samba's website]("https://www.samba.org/samba/docs/current/man-html/vfs_fruit.8.html") about vfs_fruit and was curious about this note:

"Be careful when mixing shares with and without     vfs_fruit. OS X clients negotiate SMB2 AAPL protocol     extensions on the first tcon, so mixing shares with and     without fruit will globally disable AAPL if the first tcon is     without fruit."

I did create a second share for testing, both with and without the options you suggested using, Morbius. So to answer, yes, I did mix shares both with and without fruit at one point in time but i don't anymore. All is using fruit. Is AAPL would still enabled or do I need to enable something manually?

---

### Post by Morbius1 on 2019-03-21
> "Be careful when mixing shares with and without     vfs_fruit. OS X  clients negotiate SMB2 AAPL protocol     extensions on the first tcon,  so mixing shares with and     without fruit will globally disable AAPL  if the first tcon is     without fruit."
That is a fact I'm afraid. Upon initial connection to a share Finder remembers the state and environment of that connection. If you create a share w/o fruit and connect to that share first you are in a non-fruit state when you connect to the share w/fruit.

If all your share are configured w/fruit this is not an issue.
> My plan was to use both AFP (netatalk+avahi) and SMB on the same  computer and share the same drive, also using Time Machine with Macs  from Leopard, 10.5 to Mojave, 10.14.

Um ... Wow .... I was assuming you would use SMB w/Time Machine since Apple really wants to use its own native smb implementation these days. That's an interesting question. I don't know what happens if AFP is used together with SMB on the same directory. Sorry, this is one of those "I've never done it" situations I mentioned above.

[COLOR=#0000cd]Please note:[/COLOR] [COLOR=#0000cd]This is going to sound counter intuitive but if you plan on accessing this share with previous versions of MacOS you may ( *note: may* ) need to add another option. This time in the [global] section of smb.conf: [/COLOR]
```
unix extensions = no
```

---

### Post by leetbacoon on 2019-03-22
All of my shares now include fruit. I assume, since this is the case, I have nothing to worry about?

> Um ... Wow .... I was assuming you would use SMB w/Time Machine since  Apple really wants to use its own native smb implementation these days.  That's an interesting question. I don't know what happens if AFP is used  together with SMB on the same directory. Sorry, this is one of those  "I've never done it" situations I mentioned above.

No worries. I really would prefer to use only SMB anyway (simpler to set up/manage and seems more bullet-proof than using netatalk). And, to clarify, yes I have used both AFP and SMB before on the same source on the same computer, and it does work, but I haven't tried them both at the same time and not with Time Machine.

My thoughts were to use AFP (maybe Leopard through Mavericks) on the older Mac clients and SMB on the newer ones (Yosemite to present).

And, I haven't tried it yet, but what does "unix extensions = no" do? Some research online didn't explain well about this. For the record, the oldest OS I will use with this is Leopard. This won't touch =<OS9 territories. And also, not sure if it's related, but a lot of my files contain "/" in them. Hopefully that flag won't mess up that.

One last thing to note, reading more into the vfs_fruit documentation, I see **fruit:time machine = [ yes | no ]** and **fruit:time machine max size = SIZE [K|M|G|T|P]**. I assume I need to use these under each share, too?


Sorry mods if this is getting off topic :-\
And sorry for the amount of questions, I am a noob haha

---

### Post by Morbius1 on 2019-03-22
> For the record, the oldest OS I will use with this is Leopard.
In reference to the "unix extensions" I mentioned I'm talking about something around the El Capitan era. You may find that It will not work unless you set unix extensions to no.

The reason and explanation are complicated and I admit that I don't understand it fully myself but there is a very subtle interaction between permission on a non-Windows client and a Linux samba server. I can only pass along what I was told by someone who dumbed it down for me: From a Linux perspective the permissions on MacOS are ... um ... weird. It's sorta kinda a hybrid between normal Linux permissions and access control lists. As MacOS has evolved and as the native Apple SMB implementation has evolved it's become closer to how a Linux client operates. 
>  One last thing to note, reading more into the vfs_fruit documentation, I see **fruit:time machine = [ yes | no ]** and **fruit:time machine max size = SIZE [K|M|G|T|P]**. I assume I need to use these under each share, too?
This is what I was talking about above. I'm not sure that will work in Ubuntu 18.04 because the version of samba there hasn't fully implemented it yet so the short answer is: I don't know.

A quick search  finds something like this: [https://kirb.me/2018/03/24/using-samba-as-a-time-machine-network-server.html](https://kirb.me/2018/03/24/using-samba-as-a-time-machine-network-server.html)

Note:
[1] I wouldn't try to install samba 4.8 on Ubuntu 18.04 on a drunken bet.
[2] I looks like he has some of the parameters in the wrong place ( fruit:aapl = yes for example is a [global] parameter not a share parameter )
[3] I may try it on a Ubuntu 18.10 test box one of these days but ......

---

### Post by leetbacoon on 2019-03-27
Hi, sorry for the late reply. So I tried that but still Time Machine is not working. I went the long way and just installed Netatalk and it seems to be working fine over AFP, however, I am now running into other issues I don't remember having before. :(

If I copy a file to my server through finder, then delete it on the server (ssh), it disappears like normal. But if I try copying a file to there again with the same name, finder says **The operation can&#8217;t be completed because an item with the name &#8220;foo.7z&#8221; already exists. **I haven't tried deleting the file, disconnecting, reconnecting, and trying again because I feel that that will solve it, but I will still have to do that for every file which I really don't want to have to do.

Since your post, I have done the following:

- $ sudo zfs set xattr=sa tmrepo # I read somewhere that for OSX's file attributes, running this should speed up ZFS and not create appledouble files.

- Change my smb.conf file, attached below:
```
[global]
mangled names = no
dos charset = CP850
access based share enum = yes
unix extensions = no
fruit:aapl = yes
fruit:model = MacPro
unix charset = UTF-8
fruit:resource = xattr
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
server role = standalone server
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
usershare allow guests = yes

[SMB Share]
 comment = SMB Share
 path = /smbshare
 browseable = yes
 read only = no
 guest ok = no
 ea support = yes
 vfs objects = catia fruit streams_xattr
 map archive = no
 spotlight = yes
 readdir_attr:aapl_rsize = yes
 readdir_attr:aapl_finder_info = yes
 readdir_attr:aapl_max_access = yes
```

And by the way, my version of Samba is 4.7.6.

Would you happen to know if there's anything I need to do to get this all good?

---

### Post by leetbacoon-alt on 2019-05-11
Hi Morbius, would like to know if you have any solution to this. Apologies for bumping. The thread is still relevant, as this issue persists. I feel like it is related to a vfs fruit mis-configuration. Any help is appreciated.

And yes, I had to create another acct. I forgot original account pass word. :-/

---

