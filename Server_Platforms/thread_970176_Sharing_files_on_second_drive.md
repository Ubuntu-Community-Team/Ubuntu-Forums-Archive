---
title: "Sharing files on second drive"
date: 2008-11-03
forum: Server Platforms
---

### Post by bloodantz14 on 2008-11-03
We have a small business and have 3 different areas and want to have a share folder for each one, e.g. Accounts, Projects and Client data.

We have only 4 computers right now. All the computer are windows except for the ubuntu one. We want a setup kind of like this: 

Computer 1 to have write access to Accounts, Projects and Clienta data.
Computer 2 to have write access to Projects and Client data.
and so on

Would we use users and user groups to do this?

We have Ubuntu 8.1 installed on a 80gb hardrive and 2 250gb harddrives setup in Raid1.

We set the mount point for the Raid1 as /mnt and have the 3 share files in there (accounts, projects and client data)

This is the first time i have ever touched linux and need help making this possible. Right now we can see the shares from the windows pcs but can't write to them.

We are also using webmin to do everything.

Any help would be appreciated

thanks

---

### Post by TwoWordz on 2008-11-04
Hi bloodantz14, 

You should post your samba configuration here (omit the comments) and also verify that your folders have the proper permissions. 

One common error is to setup samba right but forget to set the umask correctly on the actual folders on the file system. 

TW

---

### Post by bloodantz14 on 2008-11-04
```
#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	username map = /etc/samba/user.map
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = DIGITALDESIGN
	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

#   wins support = no

;   wins server = w.x.y.z

# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   bind interfaces only = yes



#### Debugging/Accounting ####


####### Authentication #######


########## Domains ###########


;   domain logons = yes
#
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

;   logon drive = H:
#   logon home = \\%N\%U

# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

#   domain master = auto

# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

;   winbind enum groups = yes
;   winbind enum users = yes

;   usershare max shares = 100


#======================= Share Definitions =======================

# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

;   read only = yes

  create mask = 0755

   directory mask = 0755

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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

;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[ddm_projects]
	guest account = jason
	writeable = yes
	delete readonly = yes
	path = /mnt/ddm_projects
	force group = ddm_staff
	force user = jason
	comment = Look at this
	hide dot files = no
	valid users = jason,@ddm_staff
	public = yes
	create mode = 777
	allow hosts = Development
	directory mode = 777

```

---

### Post by bloodantz14 on 2008-11-04
Whoops entered the code twice, so have deleted this post

---

### Post by TwoWordz on 2008-11-05
What are the permissions on /mnt/ddm_projects?

ls -l /mnt/ddm_projects

TW

---

### Post by bloodantz14 on 2008-11-05
drwxr-xr-x

Should that give us write capabilities?

---

### Post by devonps on 2008-11-06
> **bloodantz14 said:**
> drwxr-xr-x

Should that give us write capabilities?

The above settings will only allow the owner to write, all other users can only Read and eXecute the files.

A breakdown for you:

Owner has permissions: rwx
Group has permissions: r-x
Other has permissions: r-x

Where r = read, w = write, x = execute

BTW: The d at the front indicates this file is a directory.

On possible option is to set the permissions to 777 which will allow ALL users to read, write and execute. Of course your security policies may restrict this so I'd recommend a Google search of [CHMOD]("http://www.google.co.uk/search?source=ig&hl=en&rlz=&q=chmod&meta=") should help you understand the exact permissions you require.

Hope this helps,

Steve.

---

### Post by bloodantz14 on 2008-11-06
i tried 

```

sudo chmod 777 /mnt/ddm_projects

```

and i still get drwxr-xr-x when i type: ls -l /mnt/ddm_projects

do i have to save it somehow?

---

### Post by bloodantz14 on 2008-11-06
ok now for some reason its permission is d--------- and so is the /mnt directory. i don't know how i did that, but i it won't let me change it back.


Another thing, the fstab shows the option for umask as 777 on the mounted disc

[EDIT]

I read up on umask and found that it would have given me no permissions with 777 so i changed it to 000 and now typing "ls -l /mnt" gives me the permissions rwxrwxrwx.

but now when i try and access /mnt/ddm_projects from my windows machine it asks for a password and has the login name greyed out and only lets me login as a guest.

Any help on that?

the entry in my smb.conf for this share is;

```

[ddm_projects]
	force user = jason
	browseable = yes
	locking = no
	create mode = 0777
	path = /mnt/ddm_projects
	directory mode = 0777
	comment = Digital Design Media Project Files
	valid users = jason,@ddm_staff,@staff

```
and the logon of the windows machine is 'jason'

---

