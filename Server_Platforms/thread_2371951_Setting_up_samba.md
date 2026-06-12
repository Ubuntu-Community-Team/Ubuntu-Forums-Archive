---
title: "Setting up samba"
date: 2017-09-19
forum: Server Platforms
---

### Post by roadrawts on 2017-09-19
I'm trying to set up Samba for a network of 3 machines where one of them is to be a file server and the other 2 are clients.   They are all Ubuntu 16.04 Desktop systems.  The file server machine is named "FileServer" and the clients are named "A" and "B".

I installed Samba on all 3 machines and edited the smb.conf files (included below) accordingly (or so I thought).  What's happening is the following.
On either FileServer or a client from the file manager list if I click on:

a) Network - all that shows up is Windows Network.  If I click on Windows Network it disappears and nothing is displayed.
b) Connect to Server - If I click on Windows Shares on <ip adddress of FileServer smb://ip address of FileServer> and click on Connect then Shares shows up.  If I click on a directory my files are there.

What's not happening is when I first started this and clicked on Network, the Shares showed up in addition to Windows Networking.  Now, just the Windows Networking.

What changed is that I mistakenly decided to install Webmin to tweak the configuration.  A mistake on my part.  I was able to restrict the users of the Shares to only the users that I wanted.  So it wasn't a total loss.

I've included below the smb.conf files from both FileServer and a client machine.  Can you look through them and, possibly, let me know how to fix them.

Thanking you in advance.

Mel

```
=============================
FileServer smb.conf file
=============================

#======================= Global Settings =======================

[global]
	default = Shares
	write raw = no
	passdb backend = tdbsam
	read raw = no
	auto services = Shares
	server role = standalone server
	usershare allow guests = yes
	unix password sync = yes
	writeable = yes
	dns proxy = no
	syslog = 0
	path = /home/user1/Shares
	write list = user1,user2
	map to guest = bad user
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	workgroup = WORKGROUP
	passwd program = /usr/bin/passwd %u
	pam password change = yes
	valid users = user1,user2
	os level = 20
	panic action = /usr/share/samba/panic-action %d
	server string = %h server (Samba, Ubuntu)
	max log size = 1000

#   wins support = no

;   wins server = w.x.y.z

#### Networking ####

#   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes

#### Debugging/Accounting ####

#   syslog only = no

####### Authentication #######


########## Domains ###########

;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile

;   logon drive = H:
#   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

   usershare max shares = 10

#======================= Share Definitions =======================

#[homes]
#  comment = Home Directories
#   browseable = yes

#   read only = no

   create mask = 0775
   directory mask = 0775

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin

#This is what I added
[Shares]
	create mask = 0775
	directory mask = 0775
	browseable = yes
	guest ok = no
	read only = no

==========================
Client smb.conf file
==========================

#======================= Global Settings =======================

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
#   wins support = no

;   wins server = w.x.y.z

   dns proxy = no

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m

   max log size = 1000

#   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Domains ###########

;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile

;   logon drive = H:
#   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   usershare max shares = 100
   usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin

;[allusers]
;comment = All Users
;path = /home/shares/allusers
;valid users = @users
;force group =  users
;create mask = 0660
;directory mask = 0771
;writeable = yes

[Shares]
comment = Share Directory
browseable = yes
valid users =%S
writeable = yes
create mask = 0775
directory mask = 0775
read only = no
```

---

### Post by slickymaster on 2017-09-20
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by Morbius1 on 2017-09-20
**[COLOR=#0000cd]This is going to be a long post because there are many things messed up  with your configuration.[/COLOR]**

Probably because you used Webmin your server smb.conf is way more complicated and convoluted than it needs to be and you have things in the wrong place. For example, in the [global] section you have **valid users = user1,user2**. Since it's in the global section not where it belongs the only people that can even see your shares by browsing are those users. Linux doesn't do that through it's file manager browse mechanism which probably explains why they don't show up on the clients . 

You have the whole share definition in the [global] section none of which belongs there:
> writeable = yes
path = /home/user1/Shares
write list = user1,user2
valid users = user1,user2
You've discombolulated your [homes] share by selectively un-commenting certain lines which end up becoming defaults to all shares.

My advice is to start over:

[1] Stop using Webmin.

[2] There is a factory fresh copy of the default smb.conf so:

** Rename the one you are using now:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.orig
```
** Copy the default one to the /etc/samba location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
[3] Then add your share definition to the end of the smb,conf file:
```
[Shares]
         path = /home/user1/Shares      
         guest ok = no
         read only = no
         valid users = user1,user2

```
Save the file and restart smbd:
```
sudo service smbd restart
```


[COLOR=#0000cd]**Side note1**[/COLOR]: You didn't ask about the client smb.conf but there is a mistake in it.

First, you need to get acquainted with a diagnostic utility called testparm. To use it open a terminal and run:
```
testparm -s
```
If you run that on the client machine you will notice at the end this:
> [Shares]
comment = Share Directory
valid users = %S
read only = No
create mask = 0775
directory mask = 0775
directory mode = 0775
[COLOR=#0000cd]**available = No**[/COLOR]
Your share is disabled. The output of testparm tells you why at the top of the output:
> WARNING: No path in service Shares - making it unavailable!
NOTE: Service Shares is flagged unavailable.

The only share that does not require a path is the [homes] share. All others need to have a path specified or else Samba kicks it out.

[COLOR=#0000cd]**Side note2 - only if you are interested**[/COLOR]: You are using Samba in an all Linux network and you are  using the Windows method of host discovery - netbios. There is another way that is faster, less convoluted, and more predictable so on all your machines but especially on the server:

[1] Make sure avahi is installed on your server:
```
sudo apt install avahi-daemon
```
[2] Create a file as root at /etc/avahi/services/samba.service.
[3] Add this to the file:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
[4] Make sure avahi-daemon is installed on all your client machines.

From the client your server will automatically show up under Network in their file managers as **FileServer SMB** - not under Windows Network since we are no longer using the Windows Network discovery method - directly under Network.

An even better approach would be to assign a static ip address to all your machines and connect to them that way.

---

