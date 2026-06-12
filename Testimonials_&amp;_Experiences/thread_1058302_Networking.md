---
title: "Networking"
date: 2009-02-02
forum: Testimonials &amp; Experiences
---

### Post by BLTicklemonster on 2009-02-02
I have just determined that the only reliable way to network this computer with other computers on the local area network is to reinstall ubuntu every time the network on this computer fails. I won't but I can tell you that each time I install ubuntu for one reason or another, since I have found out how to get it to work and since Ubuntu has gotten things working better, this computer will share nicely with the windows computers. Then for no apparent reason, it stops. It will remain stopped until the next time I install Ubuntu again for whatever reason. I would imagine it's the updates that is causing this, though I'm not certain.

I'm just ranting, please do not offer assistance, as I would rather pull my teeth than to try to troubleshoot this only to loose it again. Yes, I'm sure many of you have no problem whatsoever, yay you. I'm ecstatic for you. 

Again, no assistance is necessary, just let an old man who thinks networking in Windows is a breeze (contrary to what I've read on here, it's so simple it's a joke) have his rant and be done with it.

Now to go upstairs to the windows computer and email my daughter's essay to this computer so I can print it, then carry it back upstairs so she can glue it to her poster board. Which stinks, because they're up there right now laughing at Dad and his cockeyed operating system he swears by. (me being the aforementioned Dad entity)

Thank you, Ubuntu. There's three people upstairs who refuse to give Ubuntu a chance, though I'm sure someone will say I'm to blame in this. Read on, if that's your opinion.

I can't wait to see the replies, but before you do, answer me this: Why does networking constantly break in Ubuntu? Why should I troubleshoot anything at all? The windows machines network in no time flat, and have never failed at all. Not once. Not a single update has caused a problem for any of them, yet this machine geeks like clockwork every time. Every single time.

Free :popcorn: while supplies last, lol.

---

### Post by Kebabman on 2009-02-02
Define 'network this computer with other computers on the local area network'; If by this you mean using windows networking to share files etc. Then that would be the first problem. You are attempting to use a Microsoft way of doing things through 3rd party hacks to get it all working. Obviously this will work a lot better through Windows than it will through Ubuntu, in the same way that using Linux specific file sharing methods will work a lot better between a bunch of Linux machines than if you then shove a windows box in the mix.

Just my 2 pence worth.

---

### Post by BLTicklemonster on 2009-02-02
Networking in Ubuntu: Right clicking a folder and sharing it. Worked fine, stopped working. Lather rinse repeat ad infinitum.

If it doesn't work, why is it an option?

---

### Post by Kebabman on 2009-02-02
In which case you are using Samba to share files with a windows network. As you have said it has worked before, it is quite possible that there is a bug somewhere down the line that is stopping it working, possibly due to an update that has been installed.

If you are expecting Ubuntu to be quite as stable as Windows for a desktop user then unfortunately you are obviously mistaken. Windows is a product developed by a large number of paid developers, not a bunch of volunteers who do it all out of their passion for the OSS community. Finding what is wrong and trouble shooting it is how these bugs get fixed and passed on to other users in the same situation. This is one of the benefits of OSS in the first place. I have had numerous troubles over the years with the windows way of networking but unfortunately there are few places where I can go and rant about it to people that might actually listen to my comments, take it on board and use my trouble shooting efforts to try and fix the problem.

Hopefully some good will come out of your rant if you can give as much information as possible and even if you don't trouble shoot the problem yourself it might give others the oppurtunity to recreate the problem and go about finding a fix that can be rolled out int he next bunch of updates. Hence benefiting the community at large.

---

### Post by BLTicklemonster on 2009-02-02
Well, there's really hardly anything to say other than I installed Hardy two weeks ago, and have done every update since.

---

### Post by Kebabman on 2009-02-02
I would love to be able to help you with this but unfortunately I don't have a windows machine available at the moment to test with. I might be able to cobble one together tomorrow in order to do a few tests and see if I can get it working. I'm sorry it has stopped working for you and truly hope you get it working. I definately agree that it is an extremely desirable feature that a lot of users would like and from what I can tell it is far from simple in a lot of cases.

If I have any luck I will post back to you to let you know what I did. Hopefully with a bit of time this feature will be a lot simpler to set up.

In the mean time have you looked into other ways of sharing files? I know it's not quite as simple as using sambe a lot of the time (when it works obviously) but there are other ways out there. There are options such as sshfs which i use quite a bit, this mounts remote directories over ssh which is quite good. There is obviously FTP. And others, might be worth taking a look.

---

### Post by BLTicklemonster on 2009-02-02
No no no no no, you don't understand, I am beyond even caring at this point. For me, Ubuntu = no networking for some twilight zone reason that is beyond comprehension. Well, okay, comprehend this:

1. I refuse to edit anything in order to network. Why? Because it's the freaking 21st century, and I'm not in DOS.

2. It appears as though there's more talent wasted putting compiz and pulse audio in new releases of Ubuntu than there is in seeing all threads in this forum and on other linux forums where someone has a problem with networking, and the thread dies out. Why does it die out? Certainly there are people who get their networking going, but don't have the courtesy to thank anyone. I feel though, that a large number of these people took a hard long look at 'nix and decided that it was not worth the hassle, wiped their drives, installed Windows and never looked back.

3. For some insane reason people have to make things difficult. To network in Windows, use the stinking wizard. Done. Guess what? It will keep working til the cows come home! It's simple. Ubuntu on the other hand... Well, I made this thread, right?

Now I'd love to try to be helpful by posting anything helpful, but honestly I don't have the patience to. It's like ... say you install Vista or maybe the new Mac os, and you can't use it unless you open a file and edit something, then if you update it, it stops working. No, nobody gets paid to do all this stuff, and I appreciate the hard work that goes into Ubuntu, but it's just this one stinking little nightmare: NETWORKING that kills it for me. Why does it keep breaking? What is being done that stops it working? Why hasn't anyone noticed this? Well, because the people who don't want to edit files just to network have already left the building. I, on the other hand, being the whore for abuse that I am, stay. 

Anybody else out there having problems like mine, by all means, chime in. I can't be the only one.

---

### Post by mikecanada on 2009-02-02
My vista box and my Ubuntu 8.10 work perfect together,just drop down frm Places to network and there is the Windows box.My only issue is I can,t have the vista ubuntu network AND the internet together seems the system excepts the web to come from a source other than the modem or air card.Cheers Mike and don,t get down things will get better.

---

### Post by Kebabman on 2009-02-03
Well, presumably you were making that post from your ubuntu box so the networking is actually working fine. It's not the networking that's broken it's your ability to share files over a hack of a piece of software created to share files using a MICROSOFT sharing method. This isn't windows so interoperability could be a problem. Do you expect to run Microsoft software on Linux flawlessly?

As I previously stated, if you want to share files then look at methods that will work between the two operating systems rather than expecting to be able to use the microsoft method without any troubles. Either that or just go back to windows if using that specific file sharing method is that important to you. The tools for the job and all that...

---

### Post by callan79 on 2009-02-03
> **mikecanada said:**
> My vista box and my Ubuntu 8.10 work perfect together.

I thought I'd pipe up and offer my two cents aswell. Here's some interesting trivia :

1. My wife likes to whinge about -everything- and -anything-
2. If there's some way she can blame Ubuntu, she will
3. She's usually wrong - the system 'usually' does as expected

Now, we (she) have an X-Box in the lounge. We use it to stream video files and photos for display on the TV. The videos and photos come from her Ubuntu box.

In the past, I've edited SAMBA configuration files, to learn the ropes. In Intrepid though, I just right clicked the folder, chose SHARING, and it all set up by itself.

I made sure the username/password on the X-Box matched the username/password on the Ubuntu box.

I'm happy to report that since Oct 2008 it hasn't broken a single time. Even with regular updates, it keeps working. Hey, she's using it right now as we speak.

You ask - what is the point of this post?

Only to illustrate that my system is plain, boring and 'normal' - and everything 'just works'. So there -must- be some little thing that's happening that causes BLTicklemonster's network sharing to keep falling over.

BLTicklemonster - have you got any firewalls installed or set up? Any weird non-standard networking applications like network scanners etc?

Good luck with finding the solution, I bet it's something really simple!

By the way ... the shared files, are they on YOUR machine, or a WINDOWS machine?

Cheers
Callan
(apologies for the long, useless post)

---

### Post by BLTicklemonster on 2009-02-08
> **Kebabman said:**
> Well, presumably you were making that post from your ubuntu box so the networking is actually working fine. It's not the networking that's broken it's your ability to share files over a hack of a piece of software created to share files using a MICROSOFT sharing method. This isn't windows so interoperability could be a problem. Do you expect to run Microsoft software on Linux flawlessly?

As I previously stated, if you want to share files then look at methods that will work between the two operating systems rather than expecting to be able to use the microsoft method without any troubles. Either that or just go back to windows if using that specific file sharing method is that important to you. The tools for the job and all that...

It always works. Like clockwork since feisty. Every time I do a fresh install. Then it breaks. No rhyme nor reason, it just breaks. Every time in each version I've used. 

It works for other people. Why them, not me? And why can I search the forums for answers and find more unanswered or dropped thread that have no resolution on networking than on any other thing? 

I'd do another fresh install if I knew it wouldn't break for no reason. Not sure if it's updates doing it, or what, but it always breaks. Yes, I always do updates, too. Could it be the updates causing the problem? I don't know. But I have changed my attitude. I do want direction if at all possible, so if anyone has anything constructive, that would be nice.

My smb.conf is probably a mess. If it would be helpful, we could start with it.

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
   workgroup = MSHOME
#interfaces = lo eth0
interfaces = lo 
bind interfaces only = true
security = share
guest account = nobody
load printers = yes
printing = cups
printcap name = cups 

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes # I changed that from a semicolon.

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
;   interfaces = 127.0.0.0/8 lo

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

   guest account = nobody
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
; map to guest = bad user

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
   guest ok = yes
   public = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
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

The edits have been done since it broke, so they aren't what broke it if anyone is wondering...

When I go to System>Administration>Networking Tools, and change network device from loopback to eth0, and try to configure it, I get this message:

The interface does not exist

Check that it is correctly typed and that it is correctly supported by your system.

I don't get it, is loopback enough?

---

### Post by BLTicklemonster on 2009-02-08
And to make matters worse, I can ping the XP machine across the room, and can ping this machine from there, yet neither shows up in either's networking. 

Or does that make matters better?

---

### Post by callan79 on 2009-02-09
> **BLTicklemonster said:**
> And to make matters worse, I can ping the XP machine across the room, and can ping this machine from there, yet neither shows up in either's networking.


Hi BLTicklemonster,

Okay, the fact that your machines can ping is GREAT - it indicates they can at least talk.

Now, from reading the above I have a sneaking suspicion that you might be trying to browse the network each time you want to do something. I mean you go to PLACES >> NETWORK and browse to find the other machine (or on the Windows machine, Start >> My Network Places).

Am I correct?

If so, I will admit that even on Windows, I found network 'browsing' to be quite hit and miss.

I recommend you formally map your network drives, this is how it's "supposed" to be done.

(1) Am I correct that you are browsing the network each time, and this is where the problem is?

(2) Do you know how to map/mount the remote shares, or do you need a hand (if so, please post your /etc/fstab here)

Cheers
Callan

---

### Post by stalkingwolf on 2009-02-09
there are several things to point out here.

First, it is not necessary to install each and every update.   You
can choose not to install any, or just the ones you want. I believe you can
even turn them off if you want.

Second, try booting into your oldest kernal.  It should be the last generis boot choice.  If Ubuntu is the only OS on that machine you will need to hit ESC when grub starts to get the boot menu.

Third, if that doesnt fix your problem, reboot , hit ESC, and boot the first
recovery choice.  Should be the second choice.  Let it do its thing.
A window will open with several choices, the second being FIX BROKEN PACKAGES.  select that, hit enter and let it do its thing.  then the window
will come back with resume normal boot highlighted.  Hit enter and off you go.

Fourth, if none of the above works reinstall and do no updates.

---

### Post by wolfen69 on 2009-02-09
> **BLTicklemonster said:**
> I'm sure many of you have no problem whatsoever, yay you. I'm ecstatic for you. 


i have no problem with it! :lolflag:

---

### Post by SteveHillier on 2009-02-09
Oh boy!!
What I find surprising is the BLTickleMonster blames Ubuntu for the failure to network.
Windows networking is not faultless by any means.  I have just had to reinstall Windows XP because the networking was screwed up.  I could ping, I could see servers, I could connect by remote desktop but it would not connect via DNS.  I ultimately concluded a registry problem.
Vista networking is difficult.  You can do all sorts of things but if you have not switched on network discovery forget about doing anything useful.  Tried copying across shares via Vista?  be prepared for long waits particularly if you just downloaded to a temporary folder!!
This machine I am using is Hardy, on a Windows domain, mixed with Fedora, Vista and XP workstations.  We have no problems nor have had any that are directly attributable to Ubuntu since this machine was built with Feisty some time ago and through the upgrades to Hardy.  In fact when Windows stutters I can often kick start things with Ubuntu.
We all of need a rant sometimes, I have even been guilty of it myself, but most of the time it is not because things are not working properly, it is because we don't understand how they work, reality does not always meet our expectations.
BFN

---

### Post by cariboo on 2009-02-09
Using Ubuntu's way of sharing files, just doesn't make sense to me. I know it is supposed to make it easier for less experienced users to setup networking, but it is poorly documented. There are a lot of howtos, but no real explanation of how it is supposed to work. If you need to setup up a network that just works, have a look at this [howto]("http://ubuntuforums.org/showthread.php?t=202605"). It may look a little complicated to an inexperienced user, but if you take your time and follow the howto step by step you will create a network that needs very little maintainence and it just works.

Jim

---

### Post by za.zen on 2009-02-09
> **wolfen69 said:**
> i have no problem with it! :lolflag:

Neither do I, but @OP:  best of luck resolving your issues.  :biggrin:

---

### Post by steveneddy on 2009-02-10
I will only add that I use my Ubuntu Hardy laptop on many different Windows networks in business and at friend's homes for work and play and I have never had any issues sharing or viewing shared folders with Windows machines.

I use Samba and it prints to shared printers, views shared folders across networks and attaches to remote drives when necessary.

Are you holding your mouth right when you do that?

---

### Post by Old *ix Geek on 2009-02-10
> **BLTicklemonster said:**
> answer me this: Why does networking constantly break in Ubuntu?It doesn't.  At least not for me--or any of the MANY people I've converted to Ubuntu from windoze.  Set it up once and you're done--at least that's how it's been for me in the four years since I started using Ubuntu.

---

### Post by lancest on 2009-02-11
For your network problem I would suggest using static addressing rather than DHCP. DHCP is sometimes not trustworthy. Also there are some hardware issues [here]("http://www.samba.org/samba/docs/man/Samba-Guide/HA.html"): Included in the problems are the poor network reliability of low cost hardware.

---

### Post by BLTicklemonster on 2009-02-11
Good points. I think I'll check out trying static IP addresses within the next couple of days and see how that turns out. I am stuck with the on board lan because my other pci slots (2) have a sound card and an ata 133 controller so I can increase my disk space. Sucks having 40 2 gig hard drives laying around ya know. j/k

---

### Post by solwic on 2009-02-12
> **BLTicklemonster said:**
> Good points. I think I'll check out trying static IP addresses within the next couple of days and see how that turns out. I am stuck with the on board lan because my other pci slots (2) have a sound card and an ata 133 controller so I can increase my disk space. Sucks having 40 2 gig hard drives laying around ya know. j/k

I just bought an external 640GB HDD at BestBuy for $85.  USB connectivity, so...it's a little slower than IDE/ATA, but if you want to free up a slot....  :)

I now have 1.14 TB of disk space.  I don't know how I'll ever fill it all up, but I'm going to have fun trying.  :)

Good luck!

---

### Post by BLTicklemonster on 2009-02-12
> **jrock612 said:**
> I just bought an external 640GB HDD at BestBuy for $85.  USB connectivity, so...it's a little slower than IDE/ATA, but if you want to free up a slot....  :)

I now have 1.14 TB of disk space.  I don't know how I'll ever fill it all up, but I'm going to have fun trying.  :)

Good luck!

Funny you should mention that... I pored over several sata hard drives last night, from 750 m  to 1 t.

---

### Post by solwic on 2009-02-12
> **BLTicklemonster said:**
> Funny you should mention that... I pored over several sata hard drives last night, from 750 m  to 1 t.

It's the easiest thing to do, I think.  I have a 500GB internal SATA and the 640GB external USB, and I don't think I'll ever fill either of them up.  

Still nice to have the space, though.  I also found that once I ditched the ATA drive that came with this PC and installed Ubuntu on my SATA that my PC runs a lot cooler.  The hard drive temp alone on the SATA dropped 20 degrees (Fahrenheit) without that old ATA smoldering next to it.  

But transfers are slower with USB.  It's a trade off, really:  more space and cooler drives but with slower transfers.  

Pick your poison.  :)

---

### Post by orochibayot on 2009-02-12
> **Kebabman said:**
> I would love to be able to help you with this but unfortunately I don't have a windows machine available at the moment to test with. I might be able to cobble one together tomorrow in order to do a few tests and see if I can get it working. I'm sorry it has stopped working for you and truly hope you get it working. I definately agree that it is an extremely desirable feature that a lot of users would like and from what I can tell it is far from simple in a lot of cases.

If I have any luck I will post back to you to let you know what I did. Hopefully with a bit of time this feature will be a lot simpler to set up.

In the mean time have you looked into other ways of sharing files? I know it's not quite as simple as using sambe a lot of the time (when it works obviously) but there are other ways out there. There are options such as sshfs which i use quite a bit, this mounts remote directories over ssh which is quite good. There is obviously FTP. And others, might be worth taking a look.

Thats Good!

---

