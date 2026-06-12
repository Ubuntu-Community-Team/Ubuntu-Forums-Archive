---
title: "PAM  authentication failure"
date: 2008-12-16
forum: Security
---

### Post by capibolso on 2008-12-16
My PAM module seems to work right but it fails in authentication. Althought it can't authenticate, the session module works and the software who uses it executes well.

For example, when I login through "gdm" using pam to authenticate against an ldap server
/var/log/auth.log shows

> 
pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=myuser
pam_unix(gdm:session): session opened for user myuser by (uid=0)


Any ideas?

---

### Post by ibutho on 2008-12-16
Sorry. wrong thread. I have reported it for deletion.

---

### Post by Vantrax on 2008-12-17
IM going to have to assume your .conf file is correct for your organization for either AD or LDAP.

This is out of some docco that I did for my work in Linux lab environments, I get the monkeys to use gedit as it saves a ~ file of edits as they go and I can roll back changes remotely if they break something, and because its graphical and alot of them are still not comfortable in terminal. If all else fails there is the .orig backup.

/etc/pam.d/common-auth - Make a backup copy of the original file, then modify it

sudo cp /etc/pam.d/common-auth /etc/pam.d/common-auth.orig 

gksudo gedit /etc/pam.d/common-auth

Comment out or delete the existing entries
#auth	requisite	pam_unix.so nullok_secure 
#This is for windows file sharing via samba
#auth	optional	pam_smbpass.so migrate missingok 

Add these new entries in this order
# must have a valid shell 
auth	required      pam_shells.so 

#allow local login, ignore broken shadow entry 
auth   sufficient    pam_unix.so try_first_pass 

#allow valid ldap login 
auth   [default=1 success=ignore]   pam_succeed_if.so uid > 1000 quiet
auth    sufficient    pam_ldap.so use_first_pass 

#deny access if none of the above are valid 
auth    required      pam_deny.so

/etc/pam.d/common-account  - Make a backup copy of the original file, then modify it

sudo cp /etc/pam.d/common-account /etc/pam.d/common-account.orig 

gksudo gedit /etc/pam.d/common-account

Comment out or delete the existing entry:
account	required	pam_unix.so

Add these new entries in this order:
# user must have a valid shell 
account   required      pam_shells.so 

#allow local account, ignore broken shadow entry 
account   required   	pam_unix.so broken_shadow

/etc/pam.d/common-password - Make a backup copy of the original file, then modify it

sudo cp /etc/pam.d/common-password /etc/pam.d/common-password.orig 

This file should contain no valid entries unless you want people to change their network password from linux.

gksudo gedit /etc/pam.d/common-password

Comment out or delete these entries:
password   requisite   pam_unix.so nullok obscure md5
password   optional   pam_smbpass.so nullok use_authtok use_first_pass missingok

/etc/pam.d/ common-session  - Make a backup copy of the original file, then modify it

sudo cp /etc/pam.d/common-session /etc/pam.d/common-session.orig 

gksudo gedit /etc/pam.d/common-session

This line should already exist, if not add it:
session   required   pam_unix.so


I hope it helps. Be very careful of the order in which you use sufficient and required, and the order of the list in general.

---

### Post by capibolso on 2008-12-26
As you are assuming my .conf file is correct for my organization because another host with Ubuntu 7.10 can login right without the message of authentication failure.

The files you mention are very similar to mine, they are as follows

/etc/pam.d/common-auth
auth       required     pam_env.so
auth       sufficient   pam_unix.so likeauth nullok
auth       sufficient   pam_ldap.so use_first_pass
auth       required	pam_warn.so
auth       required     pam_deny.so

/etc/pam.d/common-passwd
password   sufficient   pam_unix.so nullok md5 shadow use_authtok
password   sufficient   pam_ldap.so use_first_pass
password   required	pam_warn.so
password   required     pam_deny.so

/etc/pam.d/common-session
session    required     pam_limits.so
session    required     pam_mkhomedir.so skel=/etc/skel/
session    required     pam_unix.so
session    optional     pam_ldap.so
session    required	pam_warn.so

but the error message on /var/log/auth.log continues appearing (on Ubuntu 8.10).

---

