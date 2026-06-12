---
title: "Samba/Windows 7/Folder Redirection/Recycle Bin Issue"
date: 2012-07-18
forum: Server Platforms
---

### Post by tbeehler on 2012-07-18
All,

I am not quite sure where to post this, but I have an odd issue that I want to know the answer to. :)

I have several desktops with Windows 7 on a domain that connect to a Samba server on my Ubuntu 12.04 box.  On one share, if a person deletes a file, it goes into the proper place and the file name is there and easily copied back.  On the other share, the file is renamed to random letters/numbers.tmp file.  

Here's my smb.conf file for those two shares as well as my global config:

The Testshare works just fine, but the Users share does not.  Any ideas?  I appreciate all your help!


#======================= Global Settings =======================

[global]

	workgroup = Blah
	server string = Samba Server Version %v
	security = ads
	realm = Blah.LOCAL
	password server = 10.0.1.115
	domain master = no
	local master = no
	preferred master = no
	idmap backend = tdb
	idmap uid = 10000-99999
	idmap gid = 10000-99999
	idmap config TEST:backend = rid
	idmap config TEST:range = 10000-99999
	winbind separator = +
	winbind enum users = yes
	winbind enum groups = yes
	winbind use default domain = yes
	winbind nested groups = yes
	winbind refresh tickets = yes
	template homedir = /home/%D/%U
	template shell = /bin/bash
	client use spnego = yes
	client ntlmv2 auth = yes
	encrypt passwords = true
	restrict anonymous = 2
	log file = /var/log/samba/log.%m
	max log size = 50

[testshare]
	vfs objects = full_audit recycle
	recycle:exclude = *.tmp|*.TMP|*.temp|*.o|*.obj|~$*|*.~??|*.log|*.trace
	full_audit:success = mkdir rename unlink rmdir open pwrite	
	writeable = yes
	hide unreadable = yes
	path = /mnt/NAS/Testshare
	force directory mode = 0770
	force group = "Domain Users"
	force create mode = 0770
	comment = Test share
	create mode = 0770
	access based share enum = yes
	directory mode = 0770
   	full_audit:prefix = %u|%I|%m|%S
        recycle:keeptree = Yes
        full_audit:failure = none
	recycle:touch_mtime = yes
        recycle:versions = Yes
        recycle:repository = /mnt/NAS/recycle/%u
        recycle:directory_mode = 770
	# Hide share from users who don't have access
	# Hide files/directories if user doesn't have read access


[recycle]
	browseable = no
	inherit permissions = Yes
	writeable = yes
	path = /mnt/NAS/recycle/
	force directory mode = 770
	force create mode = 770
	create mode = 770
	inherit acls = Yes
	directory mode = 770



[Users]
	path = /mnt/NAS/Users
        vfs objects = full_audit recycle
        browseable = yes
        full_audit:success = mkdir rename unlink rmdir open pwrite
        full_audit:prefix = %u|%I|%m|%S
        recycle:keeptree = Yes
        full_audit:failure = none
        recycle:touch_mtime = yes
        recycle:versions = Yes
        recycle:repository = /mnt/NAS/recycle/%u
        recycle:directory_mode = 770
        recycle:exclude = *.tmp|*.TMP|*.temp|*.o|*.obj|~$*|*.~??|*.log|*.trace
	writeable = yes
        force directory mode = 0770
        force create mode = 0770
        create mode = 0770
        inherit acls = Yes
        directory mode = 0770
        hide unreadable = yes
        force group = "Domain Users"
        access based share enum = yes

---

