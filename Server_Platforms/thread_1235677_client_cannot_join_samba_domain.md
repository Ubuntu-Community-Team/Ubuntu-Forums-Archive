---
title: "client cannot join samba domain"
date: 2009-08-09
forum: Server Platforms
---

### Post by rocknrollmouse on 2009-08-09
Hi,

Working through “ubuntu server guide 8-10” trying to configure a new server.  
I am trying to get samba to work as a pdc for windows clients, however when I try to add a client machine (win2k) to the domain I get:
“Your computer could not be joined to the domain because the following error has occurred:”
"Logon failure: unknown user name or bad password." 

Without joining the domain, I can see the ubuntu server, and its shares; I can access and change files in unprotected shares, and I can logon to access the protected ones.

This is a testbed server running ubuntu server 8.10; there are two users, the admin user created during installation, and a normal user created to test samba.  Both users can access the shares as above, but the admin user is failing to add a client machine.

smb.conf below (anything else please ask):
> 
#============= Global Settings =============

[global]
   workgroup = WIZARDS
   server string = %h server (Samba, Ubuntu)
   wins support = no
   dns proxy = no

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
	map to guest = bad user

########## Domains ###########
	domain logons = yes
	logon path = \\%N\%U\profile
	logon drive = H:
	logon home = \\%N\%U
	logon script = logon.cmd
	add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u

############ Misc ############
    preferred master = yes
   usershare allow guests = yes

#=========== Share Definitions =============
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
[netlogon]
   comment = Network Logon Service
   path = /srv/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no
[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /media/cdrom0
   guest ok = yes
   preexec = /bin/mount /media/cdrom0
   postexec = /bin/umount /media/cdrom0
[first10]
	comment = Ubuntu test share
	path = /srv/samba/first10
	browsable = yes
	guest ok = yes
	read only = no
	create mask = 0755
[media]
	comment = some big files to fill up drive
	path = /srv/samba/media
	browsable = yes
	guest ok = no
	read only = no
	write list = @mediausers
	create mask = 0775


---

### Post by HermanAB on 2009-08-09
Well, according to the error message, you are using a bad user name or password.  To join a domain, you need to use the PDC administrator user name and password, which is probably root and the rootpassword, not just any old user account.

---

### Post by rocknrollmouse on 2009-08-09
At a basic level, user name and password are good (proven on logon at server; logon to shell via putty; and logon to access shared folder).

Yes, if it were an m/s server we would need a user at domain admin level.

My understanding is that root is disabled on ubuntu (all versions).  I think this is why the (on-line) manual I'm working from includes this step:
> 
 With root being disabled by default, in order to join a workstation to the domain, a system group needs to be mapped to the Windows Domain Admins group. Using the net utility, from a terminal enter:

sudo net groupmap add ntgroup="Domain Admins" unixgroup=sysadmin rid=512 type=d

Note! 	

Change sysadmin to whichever group you prefer. Also, the user used to join the domain needs to be a member of the sysadmin group, as well as a member of the system admin group. The admin group allows sudo use. 


I altered the command to:
> 
sudo net groupmap add ntgroup="Domain Admins" unixgroup=admin rid=512 type=d

as 
the admin user created during install is not a mamber of sysadmin group, but is a member of admin;
there is no sysadmin group in /etc/group file.

As the user created during installation is for admin purposes, I didn't think this was "just any old user account" :confused:

---

### Post by rocknrollmouse on 2009-08-10
Re-activated the **root** account; 
tried to join the Win client into the domain using **root**;
=> fail with original error (see #1)
> 
“Your computer could not be joined to the domain because the following error has occurred:”
"Logon failure: unknown user name or bad password." 

](*,)

---

### Post by jbcola on 2009-08-14
Can you post the output of "net groupmap list" to show how the samba groups are mapped to the unix groups?

---

### Post by rocknrollmouse on 2009-08-14
> 
$ net groupmap list
Domain Admins (S-1-5-21-2100339787-3358467576-788203171-512) -> admin


then
> 
$ members admin


shows my admin user as only member

---

### Post by jbcola on 2009-09-09
Did you also add the root user to the  /etc/samba/smbusers file? :
root = administrator

---

