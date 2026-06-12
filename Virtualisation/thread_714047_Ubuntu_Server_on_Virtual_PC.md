---
title: "Ubuntu Server on Virtual PC"
date: 2008-03-03
forum: Virtualisation
---

### Post by jc1cell on 2008-03-03
I have installed Ubuntu Server 7.10 onto Virtual PC 2007 with success.  However, I created the Virtual Machine with only one drive for use with the OS.  In order to have it work as a Virtual File Server for testing purposes I created an additional virtual drive for this virtual machine......( I'm virtually going mad typing this .....virtually...lol).

The problem I'm encountering is that fdisk doesn't recognize the new drive...therefore I can't mount it so Ubuntu Server can recognize it.

Any ideas what I need to do for this?

jc

---

### Post by jc1cell on 2008-03-03
So I finally realized that Ubuntu is recognizing the drive...except that it is called sdb rather than the traditional hda as stated in [this]("http://howtoforge.com/ubuntu-home-fileserver-p3") site.  This is the tutorial I'm using to install ubuntu server...although his is a normal install rather than a virtual one.

I followed all his steps (except for having that second drive in before install)  when I do the fdisk -l it states that sdb does not have a valid partition table.

I tried continuing with the mounting anyway but it tells me I need to specify the filesystem...which I understand since it doesn't have a partition.

Any ideas on what to do or should I re-install the server with the drive in and hope that it recognizes it??

jc

---

### Post by jc1cell on 2008-03-03
So I used [this]("https://help.ubuntu.com/community/InstallingANewHardDrive#head-3b50f4548d735e5249f97885af56acc5dfb0fe14") tutorial from the Ubuntu documentation to partition the drive....it worked charms...however, its a linux partition and I need it as a ntfs.

Any ideas how i could do that??

jc

---

### Post by jc1cell on 2008-03-03
So I finally was able to complete the install as detailed in the before mentioned tutorial...(the change in hard drive names threw me for a loop for a while and being a total noob I have to search for the different commands needed for partinioning, formatting in NTFS, etc.)

I can see the server in my workgroup of which my windows system is a part of.  When I double click to acces I get my login window and it accepts my user name but even though I put in the proper password it just keeps loading the login screen.

One thing I noticed is that after I formated the partition as an ntfs filesystem it still reads the partition as linux and not ntfs.

Could this be an issue?

jc

---

### Post by jc1cell on 2008-03-03
So I changed the ntfs to linux and still have the same problem with logging in...it doesn't accept the password.  I can ping the server from the xp system without any issues.

I would copy my smb.conf but I have no clue how to do it since its in virtual pc and its ubuntu server with no gui....

Anyone have an idea about this....I have searched endlessly throught this forum and have found similar instances without any solutions.

jc

---

### Post by Eiríkr on 2008-03-03
Hey there --

I'm not familiar with Ubuntu Server, but the CLI I'm fine with.  :)  Log in to your Ubuntu machine, and first thing you should see is your prompt, something like this:
```
username@servername:~$
```
The bit after the ":" tells you your current directory, in this case "~" which is shorthand for your home directory (/home/username).  To get at your smb.conf file, type in
```
cat /etc/samba/smb.conf
```
"cat" is a command to just spit out the contents of the file to the terminal screen.  Then just copy it off the Virtual PC window and paste it into your browser's text box to post it here.  :)  Once we get sight of that, we can get cracking.  

Cheers,

Eiríkr

PS -- I'm up to my eyeballs in work, so my replies might be few and far between, but worry not -- I'll do what I can to get this worked out.  ;)

---

### Post by jc1cell on 2008-03-04
> **Eiríkr said:**
> 
...Then just copy it off the Virtual PC window and paste it into your browser's text box to post it here.  :)  Once we get sight of that, we can get cracking.  ...


Eiríkr

PS -- I'm up to my eyeballs in work, so my replies might be few and far between, but worry not -- I'll do what I can to get this worked out.  ;)

First off...thanks for taking the time to answer my "post" ;).  And don't worry about the replies....I know how it goes....I offer help on digital printing forums and state the same if necessary.

I hate to be such a noob (which I am) but I just can't seem to get Virtual PC to copy anything that's on the screen of the virtual machine ](*,)  . I was going to send screen shots of the different sections allowed on the screen but I gave up once I realized there were around seven and I still wasn't at the end of the document.

I may try installing somekind of window gui on it (although it may only give me more issues) just to be able to copy it via the gui terminal.  I tried using PUTTY since I have ssh installed, but it gives me a "Network Error: Connection Refused".

If you have any other ideas drop a line....

---

### Post by Eiríkr on 2008-03-04
If I recall, Ubuntu is odd in that it does not include sshd by default, so PuTTY won't work right off the bat.  You need to apt-get the openssh-server package first.

Another option is if you have mount.cifs installed anywhere on your Ubuntu Server machine (part of the smbfs package if you need to apt-get it), you could use the CLI to mount a folder shared from the Windows side and then just cp the smb.conf file over to the Windows box.  (There may well be easier ways of doing this, but I'm on a Samba jag right now and that's what I know best. :))

On the Windows side, choose a folder for sharing, right-click it, click Properties, Sharing tab, then select the "Share this folder" radio button.  Click the Permissions button and check that your current username has access, and make sure it has Change permissions too.  

On the Ubuntu side, pick or create an empty directory, then type (replacing capitalized text as appropriate):
```
sudo mount.cifs //WINBOX_NAME/SHARE_NAME /PATH/TO/DIR -o username=WINUSER,password=WINPASS,rw
```

Provided you've got no error messages, then type:
```
sudo cp /etc/samba/smb.conf /PATH/TO/DIR
```

Hop back to Windows and make sure the smb.conf file has indeed been copied to the shared folder, then go back into Ubuntu to unmount:
```
sudo umount /PATH/TO/DIR
```

You may then also want to un-share the Windows folder.  

HTH,

Eiríkr

---

### Post by jc1cell on 2008-03-04
I had installed the ssh during install....why it doesn't connect...i'm thinking it has to do with the fact that I can't connect to the server from win...am I right?  probably not.

I'm currently updating a virtual ubuntu desktop I have here on xp also in virtual pc..and then will install nfs to connect to the server from there.  I was thinking the same as you except using ubuntu all the way.  Open it either directly from the server directory or from a copy on Ubuntu Desktop.

I will however, while the updates install, follow the procedure you mentioned.

Hasta luego.....espero.

jc

Edit:  

This is what I did with samba:

apt-get install samba smbclient smbfs beep ntp ntpdate

I don't see what you mention there so I will try apt-get again

---

### Post by jc1cell on 2008-03-04
> **Eiríkr said:**
> 

On the Windows side, choose a folder for sharing, right-click it, click Properties, Sharing tab, then select the "Share this folder" radio button.  Click the Permissions button and check that your current username has access, and make sure it has Change permissions too. 


Done......Shared Folder = TempShare on the C drive root.
Only user is me: Administrator = designstation and has all permissions and no password set for it. 

> **Eiríkr said:**
> 
On the Ubuntu side, pick or create an empty directory,


Done:  /ubtempshare

> **Eiríkr said:**
> 

 then type (replacing capitalized text as appropriate):
```
sudo mount.cifs //WINBOX_NAME/SHARE_NAME /PATH/TO/DIR -o username=WINUSER,password=WINPASS,rw
```



Done...this is where the fun stuff happens

attempt 1

```
sudo mount.cifs //DESIGNSTATION/TEMPSHARE C:\TEMPSHARE -o username=DESIGNSTATION,rw
```

no ip address specified

attempt 2

```
sudo mount.cifs //192.168.0.100/TEMPSHARE C:\TEMPSHARE -o username=DESIGNSTATION,rw
```

mount error: cannot change directory into mount target C:\tempshare

attempt 1

```
sudo mount.cifs //DESIGNSTATION/TEMPSHARE /TEMPSHARE -o username=DESIGNSTATION,rw
```


mount error: cannot change directory into mount target C:\tempshare

This is where I stand with that command...how many errors i made....you will tell me :). I ran it from the home directory and the ubtempshare directory.

I have now Ubuntu desktop with both samba and nfs but can't connect either to either machine.

Will keep trying...any suggestions bring them along...whenever you get the chance obviously....:guitar:

jc

---

### Post by jc1cell on 2008-03-04
So now I have Ubuntu desktop accessing the windows share I created.  However, I can't access the Ubuntu Desktop Share I created since the machine doesn't even show up in the Windows Workgroup.

The Ubuntu Desktop also sees the Ubuntu Server...both via smb and ssh...it just doesn't allow me to connect.  I even tried using the desktop terminal to connect and it gives me the exact same error that putty gives me. I must have something setupt wrong.  I even port forwarded 22 as stated in putty and still no go...I remove the port forward but..man...what gives.  

And although I have created a shared folder in nfs...i have no clue how to mount it in the server command line.  Though I don't think that should be necessary since the Desktop see the server already...

I can ping to all of them...I'm almost positive it's on the server side..but what do I know about linux..:confused:..

Anyway...if you have any ideas let me know...I'm beat and will end todays linux server session...

Thanks for you help.

jc

---

### Post by Eiríkr on 2008-03-05
I noticed some errors in your mount attempts.  

> **jc1cell said:**
> attempt 1

```
sudo mount.cifs //DESIGNSTATION/TEMPSHARE C:\TEMPSHARE -o username=DESIGNSTATION,rw
```

no ip address specified

```
sudo mount.cifs //192.168.0.100/TEMPSHARE C:\TEMPSHARE -o username=DESIGNSTATION,rw
```

mount error: cannot change directory into mount target C:\tempshare


The argument to [font=courier]mount.cifs[/font] with the double-slash should be the Windows sharing computer name, followed by the name of the share.  The next argument is the location in the Ubuntu filesystem where you'd like to mount the share.  In your case, this should look like this:
```
sudo mount.cifs //WINMACHINENAME/tempshare /ubtempshare -o username=DESIGNSTATION,rw
```
Replace WINMACHINENAME with the name of your Windows box.  If for any reason that doesn't work, replace it with the IP address of your Windows box.  Whatever the case, there should not be any Windows-style slashes ( \ ) or colons included anywhere in the mount command.  

> **jc1cell said:**
> I have now Ubuntu desktop with both samba and nfs but can't connect either to either machine.

Ubuntu - Ubuntu sharing via NFS should be a bit easier.  :)  But NFS absolutely excludes any sharing with Windows machines, as far as I understand.  If that's fine with you, read [post=4387032]this post here[/post] (it's about Lin -> Mac NFS sharing but is plenty applicable to Lin -> Lin setups too), and let me know if you have any questions.  :D

Cheers,

Eiríkr

---

### Post by jc1cell on 2008-03-05
Now to the good stuff!!!!  (and thanks for getting me this far....you :guitar:)



Here's the SMB.CONF for the server
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
   workgroup = salnet 

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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

#  this was copied from the tutorial site

   [sdb public hard disk]
   comment = Public Folder
   path = media/store
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = no group


```

jc

---

### Post by Eiríkr on 2008-03-05
Looks fine but for one thing -- the [font=courier]path[/font] value for your public folder needs a / in front.  Fix that ([font=courier]sudo vim /etc/samba/smb.conf[/font], see [here]("http://www.tuxfiles.org/linuxhelp/vimcheat.html") for some help in getting used to the vim no-GUI text editor, or pick another one to use), restart samba ([font=courier]sudo /etc/init.d/samba restart[/font]) and you should be good to go.  

HTH,

Eiríkr

---

### Post by jc1cell on 2008-03-05
I think I'm already becoming an expert at vim...:lolflag:

I went ahead and changed what you mentioned....restarted the server and tried to access it via windows....](*,)

Here's something i read in a thread similar to my issues..

"[I][B]Here's how to troubleshoot your problem if you already have it and know what it is:

sudo -i
gedit /etc/samba/smb.conf

Scroll to the bottom and then find your share name. Make sure theres' a "users = yourusername

Then, save the file and go back to the terminal.
Type

"smbpass -a yourusername"

Then, enter a password. Finally, "/etc/init.d/samba restart"[/B][/I] "

I couldn't see what he stated "users=yourusername" in my smb.conf....could you??

jc

Update:

I went ahead and tried to add a username typing:

smbpasswd -a USERNAME

and what I received was an error stating:  failed to modify password entry for USERNAME

I tried this with the usernames I originally put in and with three new ones and it gave me the same error....Any ideas?

---

### Post by Eiríkr on 2008-03-06
**For smbpasswd** -- you probably need to add a "sudo" before it.  

**Adding "user = " to your share definitions in smb.conf** -- not needed, and not really a good idea if you can use a different setup.  Besides, the added option is used to figure out how to narrow access, not increase it.  From [the smb.conf man page]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAME"):

> **user**
This parameter is a synonym for username.

**users**
This parameter is a synonym for username.

**username (S)**
Multiple users may be specified in a comma-delimited list, in which case the supplied password will be tested against each username in turn (left to right).

The *username* line is needed only when the PC is unable to supply its own username. This is the case for the COREPLUS protocol or where your users have different WfWg usernames to UNIX usernames. In both these cases you may also be better using the \\server\share%user syntax instead.

The *username* line is not a great solution in many cases as it means Samba will try to validate the supplied password against each of the usernames in the *username* line in turn. This is slow and a bad idea for lots of users in case of duplicate passwords. You may get timeouts or security breaches using this parameter unwisely.

Samba relies on the underlying UNIX security. This parameter does not restrict who can login, it just offers hints to the Samba server as to what usernames might correspond to the supplied password. Users can login as whoever they please and they will be able to do no more damage than if they started a telnet session. The daemon runs as the user that they log in as, so they cannot do anything that user cannot do.

To restrict a service to a particular set of users you can use the valid users parameter.

The post you quote is unfortunately neither very clear, nor accurate, I'm afraid.  :shock:  

At any rate, try running [font=courier]sudo smbpasswd -a USERNAME[/font] and see if that works any better.  Once you've added a username (or modified if the username was added previously) and assigned its Samba password, restart Samba and try to log in again from Windows using the username / password combo you just defined.  

----- ***Actually:***

I just followed my own advice and read through parts of the smb.conf man page again.  You should have a look [at this section on the security settings]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY"), as I note you have your sole share defined as "public = yes" (synonym for "guest ok = yes") and this section applies to that with regard to how usernames and passwords are handled.  From the man page:
> **guest ok (S)**
If this parameter is yes for a service [i.e. for a share], then no password is required to connect to the service. Privileges will be those of the guest account.

This paramater nullifies the benifits of setting restrict anonymous = 2

See the section below on security for more information about this option. [i.e. the link I added above]

Default: guest ok = no

So it sounds like if you have [font=courier]security = user[/font] (which you have commented out, but it's also the default, so that's what you're using), then you need to specify which Ubuntu-side username guest logins should map to, [as noted here](http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITYEQUALSUSER):

> *SECURITY = USER*

This is the default security setting in Samba 3.0. With user-level security a client must first "log-on" with a valid username and password (which can be mapped using the username map parameter). Encrypted passwords (see the encrypted passwords parameter) can also be used in this security mode. Parameters such as user and guest only if set are then applied and may change the UNIX user to use on this connection, but only after the user has been successfully authenticated.

*Note* that the name of the resource being requested is not sent to the server until after the server has successfully authenticated the client. **This is why guest shares don't work in user level security without allowing the server to automatically map unknown users into the guest account.** See the map to guest parameter for details on doing this.

In fact, if you're not setting up your Samba file server to be used by lots of people you don't know, you're probably best off to either:
[list=a][*]use the same username (and if possible password) on both the Windows and Ubuntu sides, thereby allowing user-based login security without needing to do any username mapping; or
[*]specify a username mapping file that defines which remote (Windows or other Samba client) usernames equate to which local (Ubuntu Samba-server-side) usernames.  [/list]

Here's a sample of the relevant sections from my smb.conf file:
```
[global]
   ...
   security = user
   username map = /etc/samba/user.map
   ...
   
[shared]
        path = /data/shared
        valid users = @users # This limits access to only members of the group "users" 
        writeable = yes
        force group = users # Ensures that any files / directories created will be created with the groupname "users".  
                            # Possibly helpful for sharing access among different users that are members of the same group.
                            # It's actually better to set up proper filesystem permissions within Ubuntu; more on that below.
        force create mode = 0770    # Sets up the default mode on files created.  More below.
        force directory mode = 2770 # Ditto for new directories created.  More below.
        comment = Shared directory with forced group.

[UserA's Documents]
        path = /data/UserA's Documents
        valid users = usera     # This limits access to this share to only UserA
        writeable = yes

[UserB's Documents]
        path = /data/UserB's Documents
        valid users = @userb    # This limits access to this share to only members of UserB's group
        force create mode = 0770
        force directory mode = 2770
        writeable = yes
```
        
And here's a sample [font=courier]/etc/samba/user.map[/font] file.  The format is local Ubuntu username = remote client username:
```

usera=rutabaga
userb=pantalones
usera=broccoli_hater
userb=breakfastpants

```

In your situation, which sounds an awful lot like a single-user setup, your best and easiest bet is to use the same username on both the Win and Lin sides.  Then you can ignore all the troubles of username mapping, and leave out all the stuff having to do with "force ... mode" and "valid users" and all that.  ;)

As for setting up permissions on your Ubuntu filesystem, this can be a complicated endeavor, but it is certainly worth some thought and planning -- IF you have a multi-user setup.  Which it sounds like you don't, so there's really no need to get into it :D.  If you're curious, have a look at [post=4423357]this post[/post] where I go into some detail about how to manage permissions with modes and groups and all that.  

So here's probably far more than you were expecting :), but hope it helps.

Cheers,

Eiríkr

---

### Post by jc1cell on 2008-03-07
> **Eiríkr said:**
> **For smbpasswd** -- you probably need to add a "sudo" before it.  


Actually, I had first run ***sudo -i*** before running the ***smbpasswd -a***, at least that's how I remember applying it.  I will however retry as per your suggestion.


> **Eiríkr said:**
> 
**Adding "user = " to your share definitions in smb.conf** -- not needed, and not really a good idea if you can use a different setup.  Besides, the added option is used to figure out how to narrow access, not increase it.  From [the smb.conf man page]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAME"):



I'm asuming this previous information is  not valid going by the information that followed it

> **Eiríkr said:**
> 

----- ***Actually:***.....



I'm going to go ahead and follow the information and see where it leads me...it may be a couple of days until I post again since I just started working on a paying project...you know how that goes...bills before pleasure....\\:D/

I will however get to it and post my results...thanks for all your help up to this point.

jc

---

### Post by Eiríkr on 2008-03-07
As ever, better busy than bored.  ;)  Even better if the busy-ness is business, of the paying kind.  Good luck with your Samba setup, and let us know if you have any questions when you get back to it.  

Cheers,

Eiríkr

---

### Post by jc1cell on 2008-03-10
So I'm back....got to working on this again and decided to do a clean install.  Turns out I had not installed the open ssh originally and now am able to connect with putty...that's a plus.

I have also had better luck with connectivity from the client side (XP sp2).  As you know I have been using a [how to forge tutorial]("http://howtoforge.com/ubuntu-home-fileserver-p3") to get this done and as I re-did all this noticed some mistakes in his setup (spelling and missing instructions). So I kept at it with some of the info you gave me and others that i found in a search.

So now I can actually go into my server and see the shared disk from the XP client.  The problem I was having (for the sake of other readers) is that I never [created a user account on the server side]("http://www.brennan.id.au/18-Samba.html#useraccounts") (why it didn't accept the original account created during setup I don't know). So now I have an account (media) created.

The problem I'm encountering now is permission based.  I can access the server but can't open the shared drive. I have media set in my smb.conf as the force user


```
 [media]
comment = Public Folder
path = /media/store/sdb1
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = media
force group = no group
```

I tried mapping users as stated on the new site i found but couldn't get that to work.

It obviously has to do with permissions but to be quite honest...my brain is burnt down with all this reading (ain't it fun learning something new  \\:D/)

So here's my smb.conf...maybe you will see what I'm missing...i'm sure of it rather.

```
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

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

# added from the how to forge site

 [media]
comment = Public Folder
path = /media/store/sdb1
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = media
force group = no group


```

I don't know if the following as anything to do with what's going on but I noticed that we use "smbpasswd" to create the password for the user, however it states in the smb.conf that the password backend is tdbsam...what gives?  I tried this code:

```
 grep media /etc/samba/smbpasswd 
``` because the author requested it and it gave me a file doesn't exist error...??? and part of his smb.conf contains  

```
smb passwd file = /etc/samba/smbpasswd
```

Could that also be part of the issue...Sorry about the length....questions, questions question....although happy about the progress....

Thanks in advance...

---

### Post by Eiríkr on 2008-03-11
Hey there --

I see a few contradictory settings here; hopefully once we get these cleared up, you'll be able to access you Samba shares just fine.

If I understand you correctly, you have one (1) user (yourself), and you'd like to share files with a minimum of fuss.  

Provided this is correct, here's what to change.  (Some of this may well repeat what you've already done; I include it here for thoroughness, to provide some back-explanation, and in case anyone else reads this thread. :))


[size=3]**Within the Ubuntu OS environment:**[/size]

**Single-user:**
In the simplest setup, use your usual Ubuntu login username as your Samba username.  Ubuntu uses the /etc/passwd file to keep track of usernames, user IDs (UIDs), group memberships, and other related info.  Samba keeps a separate file /etc/samba/smbpasswd to keep track of usernames and passwords authorized to log into Samba shares.  Note that these usernames *do* need to match actual usernames on the system; it is possible to specify a different username in the Samba login dialog, so long as you provide a mapping between the Samba usernames and actual Ubuntu usernames, or things won't work (different passwords are no problem, and actually are a good idea).  

Anyway, make sure the Ubuntu username you want to use for Samba access exists in this /etc/samba/smbpasswd file by running the following command:
```
sudo smbpasswd -a USERNAME
```
... and then type in your desired Samba password at the prompt.  

Also make sure that the Ubuntu username that the Samba username matches (or will be mapped to) has permissions for reading / writing / executing within the directories you're sharing.  Samba itself does not enforce filesystem permissions, but rather relies on the underlying Ubuntu filesystem permissions as defined for the Ubuntu username.  In a single-user setup, just run this:
```
sudo chown -R USERNAME:USERNAME /PATH/TO/SHARE
```
... replacing the caps as appropriate.  This sets the owner username and owner group name to USERNAME.  Owner users almost always have all required access permissions, so we don't need to go into how to use  [font=courier]chmod[/font] unless you run into trouble.  :)

**Multi-user:**
In a multi-user setup, things get a bit more complicated.  Start by creating a group:
```
sudo addgroup GROUPNAME
```
... then make sure all usernames that the Samba usernames match (or will be mapped to) are members of this group, like this:
```
sudo usermod -aG GROUPNAME USERNAME
```
... repeating as necessary for all the intended members of the group.  Then make sure the directories shared have the right permissions for that group.  The group owner for the shared directory and its contents should be GROUPNAME:
```
sudo chgrp -R GROUPNAME /PATH/TO/SHARE
```
... then make sure that group members have permission to read / write / execute the shared directories.  We'll also use the [font=courier]setgid[/font] bit to make absolutely sure that any files or directories created within the shared directory or its sub-directories inherit the group owner -- otherwise, share users can access things to start, but then might not be able to access each other's files and directories within the share, which can cause problems.  The command here looks ugly, but the basic idea is we use [font=courier]find[/font] to grab *just* the directories (the "type -d" part; [font=courier]setgid[/font] on files is not what we want, as this means those files then execute with the group's permissions, which can cause security problems in some cases).  We then pipe that with the | to the [font=courier]xargs[/font] command to preprocess, and ultimately the output from that gets fed into [font=courier]chmod[/font] where we actually set the permissions mode.  
```
find /PATH/TO/SHARE -type d -print0 | sudo xargs -0 chmod 2775
```
This allows anyone logged into your Ubuntu machine who is *not* in the GROUPNAME group to read, but not write, the shared directories.  Turn that last "5" into a "0" to prevent this.  (Note that this read access for "other" users [i.e. non-GROUPNAME members] is *just* for users logged directly into your Ubuntu OS.  You'd have to also allow such users explicit access in your smb.conf file for them to access the share that way.)


[size=3]**In the [global] section:**[/size]

Actually, this all looks good.  The only possible thing to change is if you need Samba - Ubuntu username mapping.  There are two parts to this.  The first is the following line in the [global] section:
```
   username map = /etc/samba/user.map
```
The second part is the user.map file itself.  The basic format is [font=courier]UBUNTU_USERNAME=SAMBA_USERNAME[/font] with no spaces, and with one "=" statement per line.  Note that multiple SAMBA_USERNAMES can be mapped to the same UBUNTU_USERNAME.  A sample file:
```
rutabaga=tiresales
rutabaga=siegfried
broccoli=accounting
chayote=wibble
```
Create the file using vim or other editor of choice:
```
sudo vim /etc/samba/user.map
```
The two [font=courier]rutabaga[/font] matches in the sample file could be two different Samba users altogether, or even just the same user's two different usernames on two different machines.  Note that users [font=courier]rutabaga[/font], [font=courier]broccoli[/font], and [font=courier]chayote[/font] *must* all exist as Ubuntu usernames on the Samba server machine, and *must* have been added to the smbpasswd file via the [font=courier]sudo smbpasswd -a USERNAME[/font] command.  


[size=3]**In the [printers] section:**[/size]

If your printer is not hooked up to your Samba server machine, you can just delete these whole two sections.
```
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
   
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```


[size=3]**In the [media] section:**[/size]

Here we want to get rid of the [font=courier]public[/font] and [font=courier]force[/font] bits.  These are generally useful when folks cannot get Samba usernames sorted out, for whatever reason.  If you've followed the bit above about usernames and groups and permissions, we're good to go without having to allow potentially risky [font=courier]public[/font] access.  While we're at it, since we set up proper usernames and permissions (including possibly the [font=courier]setgid[/font] bit as needed), we can also dispense with the [font=courier]mask[/font] entries as well.  
```
[media]
   comment = Public Folder
   path = /media/store/sdb1
#   public = yes
   writable = yes
#   create mask = 0777
#   directory mask = 0777
#   force user = media
#   force group = no group
```

[size=3]**Edited smb.conf file:**[/size]

After removing all comments, this leaves us with:
```
[global]
   security = user
   username map = /etc/samba/user.map  # <--  As needed.
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY


# Leave these in or remove as needed:
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


[media]
   comment = Public Folder
   path = /media/store/sdb1
   writable = yes

```

Hope this helps.  Let me know if anything is unclear, or you have any questions.  

Cheers,

Eiríkr

---

### Post by jc1cell on 2008-03-12
> 

**Single-user:**
In the simplest setup, use your usual Ubuntu login username as your Samba username.  

```
Ubuntu Username = jose
```

> Anyway, make sure the Ubuntu username you want to use for Samba access exists in this /etc/samba/smbpasswd file by running the following command:
```
sudo smbpasswd -a USERNAME
```
... and then type in your desired Samba password at the prompt.  

```
root@uServer:/home/jose# smbpasswd -a jose
New SMB password: *****
Retype new SMB password:*****
```

> ```
sudo chown -R USERNAME:USERNAME /PATH/TO/SHARE
```
```

root@uServer:/home/jose# chown -R jose:jose /media/store
```


> **Multi-user:**
In a multi-user setup, things get a bit more complicated.  Start by creating a group:
```
sudo addgroup GROUPNAME
```
```

root@uServer:/home/jose# addgroup musicvideo
addgroup: The group `musicvideo' already exists.
```


> ... then make sure all usernames that the Samba usernames match (or will be mapped to) are members of this group, like this:
```
sudo usermod -aG GROUPNAME USERNAME
```

```
root@uServer:/home/jose# usermod -aG musicvideo jose
```

> 
```
sudo chgrp -R GROUPNAME /PATH/TO/SHARE
```

```
root@uServer:/home/jose# chgrp -R musicvideo /media/store
```


> ```
find /PATH/TO/SHARE -type d -print0 | sudo xargs -0 chmod 2775
```

```
root@uServer:/home/jose# find /media/store -type d -print0 | xargs -0 chmod 2775
```




> [size=3]**In the [global] section:**[/size]


```
   username map = /etc/samba/user.map
```

```
root@uServer:/home/jose# cat /etc/samba/user.map
jose=jose

```
> [size=3]**Edited smb.conf file:**[/size]


```
root@uServer:/home/jose# cat /etc/samba/smb.conf
[global]

   workgroup = salnet
   username map = /etc/samba/user.map
   server string = %h server (Samba, Ubuntu)
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
    security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY

 [media]
comment = Public Folder
path = /media/store
writable = yes






root@uServer:/home/jose#


```

So, I'm not totally confused with what we just did...actually I understand it quite a bit (although the command and such are somewhat foreign but the concept I'm grasping).

However that may be, I'm back to square one without access to the server completely.  It asks for authentication but doesn't give me access to the drive.  The weird thing is that from "My Network Places" I get authentication request but from "Workgroup Computers" I just get a denial( see attached images).



I reloaded Samba (start/stop daemons) and even restarted the server all together...so although I understand everything, I'm obviously doing something wrong...

Maybe I should start from scratch with a brand new smb.conf and and maybe re-install the server to begin from zero.  Removing all info from the original smb.conf and adding as needed.


jc

---

### Post by Eiríkr on 2008-03-12
Actually, what you've described here is most likely *not* an Ubuntu or Samba problem -- as I recently discovered in a couple other threads over in the Network forum, Windows is (:shock: >gasp!< :shock:) overly "convenient" and stores share authentication information -- permanently.  So say you've got Windows username Fred, and you access Samba via username Zipperhead.  Now, ***whenever*** you log into Windows username Fred, Windows will try to use Samba authentication for username Zipperhead -- **absolutely regardless of whatever changes have been made on the Samba side**.  Have a look at [thread=720889]a recent howto by KennedyM[/thread] with instructions on how to bitch-slap Windows into not doing this.  :twisted:  Then post back here and let us know if this helps.

---

### Post by jc1cell on 2008-03-12
Quick question...could it possibly be affecting the fact that I log into my XP system as administrator always... I don't have any other users on this machine so I constantly run it as the default install when it comes to users.

I went to the link and didn't have any info in step one so I didn't bother with step two.

jc

---

### Post by Eiríkr on 2008-03-12
One thought is to rename / move the two folders KennedyM mentions, specifically:
```
\Documents and Settings\<Username>\Application Data\Microsoft\Credentials\
\Documents and Settings\<Username>\Local Settings\Application Data\Microsoft\Credentials\
```

If all they contain is Samba data, then it's probably even safe to delete (or at least empty) these, but just in case, try just renaming them (maybe adding ".OLD" on the end of the names) so that you can name tham back again if it looks like you need them in place for things to function correctly.  Then I'd suggest rebooting, and trying again to log into your Samba shares -- you *should* be prompted for login username and password.  

Cheers,

Eiríkr

---

### Post by rodgul on 2008-05-21
> ... then make sure that group members have permission to read / write / execute the shared directories. We'll also use the setgid bit to make absolutely sure that any files or directories created within the shared directory or its sub-directories inherit the group owner -- otherwise, share users can access things to start, but then might not be able to access each other's files and directories within the share, which can cause problems. The command here looks ugly, but the basic idea is we use find to grab *just* the directories (the "type -d" part; setgid on files is not what we want, as this means those files then execute with the group's permissions, which can cause security problems in some cases). We then pipe that with the | to the xargs command to preprocess, and ultimately the output from that gets fed into chmod where we actually set the permissions mode.
```
find /PATH/TO/SHARE -type d -print0 | sudo xargs -0 chmod 2775
```


Hi , I have had heaps of issues setting up my samba shares on a new 8.04 server.  Finally I found and followed Eirikr's directions and I have got the users and groups mostly figured out, and the setgid feature working.  

My problem is that any new files created via a user on my windows box or ubuntu laptop are created with read only permissions for the group, hence no other user can modify that file.  I have added the create mode and directory mode settings to the shares to get around this, but the way i read Eirikr's description I shouldn't have to do that 

What am I missing?  Did I read the post wrong?

---

### Post by calif99x on 2008-05-24
This was interesting to learn, but did not help fix my problem which seems otherwise similar.

---

