---
title: "SAMBA HELP i don't have &quot;enable windows networking&quot;"
date: 2005-03-29
forum: Server Platforms
---

### Post by dekae on 2005-03-29
Hello I have installed samba and tried to follow many tutorials. One of the tutorials was in [http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba), however the interface i have for the network settings is different. I don't have the option to "enable windows networking" under the general tab. Is there some way I can do this manually?
Thank you

Alvaro

---

### Post by Myles3 on 2005-03-29
edit the /etc/samba/smb.conf file

or 

make sure you install smbfs

For more instructions [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

---

### Post by dekae on 2005-03-29
I followed the instructions in [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver) too. But only linux is able to recognize windows, although i can't see it automatically if i write write smb://ip/share everything works. However when i use the windows computer. It can't access to linux share folder.
If i try in smb.conf where do I make the changes? is it here?:
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

thank you
Alvaro

---

### Post by Myles3 on 2005-03-29
[QUOTE=dekae]# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes[/QUOTE]

Don't touch this.

What is your workgroup MSHOME or WORKGROUP.

Have you tried to enter the IP in windows \\*YOURIP*\*ShareName*

---

### Post by allknowing469 on 2005-03-29
This may sound stupid, but have you tried enabling the network in XP. I was having the same problems with sharing files between my XP machine and Ubuntu. After I set up the network in XP I was able to share my files. Never hurts to try.

---

### Post by dekae on 2005-03-30
[QUOTE=Myles3]Don't touch this.

What is your workgroup MSHOME or WORKGROUP.

Have you tried to enter the IP in windows \\*YOURIP*\*ShareName*[/QUOTE]


it was MSHOME but i changed it to CASA which is the workgroup where the rest of the computers are.
Ok I just tried \\ip\share in windows but it says it couldn't find it. Then i used the search tool in windows start -> search and it found the linux computer but when i tried to open it told me i didn't have access to it. And when i tried to see properties it told me it couldn't find the server.

[QUOTE=allknowing469]This may sound stupid, but have you tried enabling the network in XP. I was having the same problems with sharing files between my XP machine and Ubuntu. After I set up the network in XP I was able to share my files. Never hurts to try.[/QUOTE]


I have it enabled because i can see the other windows machines the only one i can't see is the linux computer.

---

### Post by Myles3 on 2005-03-30
Have you setup any users in samba itself?

---

### Post by dekae on 2005-03-30
I don't know i think i did. After installing samba I did what the guide says:
sudo smbpasswd -a your_system_username
sudo gedit /etc/samba/smbusers 
and added my user. I'm the only one using the linux computer. After that i tried the "How to share public folder with read/write permissions (Authentication=No)?".

---

### Post by clb137 on 2005-03-30
HI,
Have you installed 'webmin' ?   it is a great tool that makes setting up 'samba' easy. 

Have installed 'smbfs' ? you need this as well as 'samba'

In your samba.conf file you must have user listed or it will not work for file sharing, 

have a look and if you need more help give me a shout

good luck

clinton

---

### Post by dekae on 2005-03-30
Hello,  yes I installed smbfs and samba. Where do I write the user list in samba.conf?. 
I'm going to try webmin thank you.

---

### Post by dekae on 2005-03-31
Ok, I have webmin now, but I don't know what to change in order for the network to work.
In the network neighborhood in the windows computer i can see the ubuntu computer but I still can't access.

---

### Post by clb137 on 2005-04-02
try this thread and set yourself up as a user

[http://ubuntuguide.org/#addeditdeletenetworkusers](http://ubuntuguide.org/#addeditdeletenetworkusers)

have you managed to start Webmin? If so you can go to the user section and add yourself as a user. 

Once your on as a samba user make sure that you have at least one folder shared, then go to your windows box and try to log on, you should have to input your log name (the samba one) and youe password (the one you set up for samba)

good luck

clinton

---

### Post by stoneguy on 2005-04-02
For me, Warty's been a bit flaky connecting to my Win drives. After I convert to Hoary Released, I'm going to hammer on this until I get somewhere or understand why I didn't. If I'm successful, I'll put together a HowTo or pass some notes to jiyuu.

My testing shows Linspire and Xandros can deal with peer workgroups - no reason that (K)Ubuntu shouldn't be able to as well.

---

### Post by dekae on 2005-04-02
[QUOTE=clb137]try this thread and set yourself up as a user

[http://ubuntuguide.org/#addeditdeletenetworkusers](http://ubuntuguide.org/#addeditdeletenetworkusers)

have you managed to start Webmin? If so you can go to the user section and add yourself as a user. 

Once your on as a samba user make sure that you have at least one folder shared, then go to your windows box and try to log on, you should have to input your log name (the samba one) and youe password (the one you set up for samba)

good luck

clinton[/QUOTE]
 Hi, i added my user and logged on in the windows box with the same user and password I have in samba and linux. When I tried to access the ubuntu shared files it again told me I didn't have permission.
This is the folder im sharing taken from my smb.conf:
[red]
   comment = Public Stuff
   path = /home/red
   public = yes
   writable = yes
   printable = no

---

### Post by dekae on 2005-04-05
anyone?

---

### Post by clb137 on 2005-04-06
Hi,

Hi if your are sure tha that you have set a user for samba with a password then I am not sure why it is not working.  Can you post your samba.conf file?

I will be aware for the nest 2 weeks so please bear with me 

thanks


clinton

---

### Post by dekae on 2005-04-06
Hi,  here it is:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = CASA

# server string is the equivalent of the NT Description field
   server string = %h (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

  security = share



# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

# AGREGUE ESTO DE ubuntuguide "compartir publico con passwd"
; username map = /etc/samba/smbusers


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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

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
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

#mi folder
[red]
   comment = Public Stuff
   path = /home/red
   public = yes
   writable = yes
   printable = no
available = yes
browseable = yes

```

thank you

---

### Post by SweetFancyMoses on 2005-04-11
I'm having quite a bit of a problem setting up print sharing.  I've searched this forum and others, I've set up cups and samba, made sure it prints locally, but when I search for the printer on other computers on the LAN, it appears not to show up at all.  What is everyone else doing to get print sharing working?

---

### Post by clb137 on 2005-04-21
[QUOTE=SweetFancyMoses]I'm having quite a bit of a problem setting up print sharing.  I've searched this forum and others, I've set up cups and samba, made sure it prints locally, but when I search for the printer on other computers on the LAN, it appears not to show up at all.  What is everyone else doing to get print sharing working?[/QUOTE]


Are you trying to print on a windows machine from a linux box???

please supply more details on your setup configeration and what you have done so far 

thanks

clinton

---

### Post by dpod on 2005-06-08
[QUOTE=dekae]Hello I have installed samba and tried to follow many tutorials. One of the tutorials was in [http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba), however the interface i have for the network settings is different. I don't have the option to "enable windows networking" under the general tab. Is there some way I can do this manually?
Thank you

Alvaro[/QUOTE]
 The problem is probably that you haven't started the samba daemons. you need to do the following (see [http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2532400):](http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2532400):)

nmbd
smbd

(don't need sudo permission, apparently).

I did the same as you and had the same problem until I discovered this.

---

### Post by LordHunter317 on 2005-06-08
> **Myles3]make sure you install smbfs[/quote]The smbfs package is only needed for the client, not the server.  I'll say that again:**smbfs is only needed for a client, not a server**. 

It's not even needed for all clients said:**
> For me, Warty's been a bit flaky connecting to my Win drives. After I convert to Hoary Released, I'm going to hammer on this until I get somewhere or understand why I didn't.I suspect it's normal browsing issues when you don't have WINS setup, or are on a domain.  Browsing is one of those black-art things that doesn't work right without the proper infrastructure.

**To the OP:**
The immediate problem is you disabled the guest account.  The guest account must be enabled.  Uncomment that line.
 
The fact you have 'security=share' is also part of your problem.  With modern Windows, it just ends up complicating authentication issues.

Reset it to 'security=user'.  This will behave like Windows does, and more like you're expecting.  Then, assuming you have permissions on the files you want to access and use the password you added, everything should work.  If it doesn't, then you have other issues.

---

### Post by garyng on 2005-06-09
Windows' browsing feature SUCKS, big time. I don't know which genius in MS come up with this solution.

Make sure there is one WINS server(and only one) running on your subnet and configure every computer(be it samba or windows) to use it. This solves most of the "now you have it, now you don't" problems.

---

