---
title: "Samba shares using Active Directory permissions"
date: 2010-07-20
forum: Server Platforms
---

### Post by UKccampbell on 2010-07-20
Hello all, this is my first time here and just wanted to start by saying thank you for all your work.  You have saved me many headaches in the last 3 years of running various Ubuntu projects for work.

I however have a problem, that after 2 weeks of browsing the forums and other sites, I cannot find a solution for.  Before I ask the question, some background is in order (sorry for wall of text)


I am the IT Manager at a research facility.  We have a fairly unique network configuration in order to support all of the different projects we have going on.  We have Red Hat, Ubuntu, Windows XP/Vista/7, Windows Servers 2003, Ubuntu servers, Red Hat servers, and even a few Netgear ReadyNAS and Buffalo Terastations.  Over the last few years, I have been migrating all of my users and accounts to a single ACL list, which I chose to be a Windows AD 2003 server.  95% of my users work on Windows platforms and just use ssh tunnels to develop on our linux boxes.  

However, i ran in to a problem with our Linux boxes not being able to symbolic link on my Windows 2003 file shares.  Of course, this is a problem with Windows not supporting symbolic links.  I know 2008 does support this feature, but given the economy and the budget restraints, we cannot afford to purchase the updates we would need, so now I am moving all of my shares to a Ubuntu 10.04 server using Samba.  I have joined the server to my AD domain successfully, i can login using my AD credentials, and even assign ownership and group permissions using AD users/groups.

Here is my question.

I would like to keep the AD permission schemes intact.  I have several shares that contain folders that have individual permission settings.  For example, I have a /shared directory that contains about 50 different folders.  Some of these folders I allow my users to write data to, some just read, and others I deny access to complete groups and just allow key groups to access (for example, personnel data should only be accessed by the Administrative staff).

Is there a way to make this work?

I can assign uid and gid manually per folder in Samba, but i would like to have the possibility to add multiple users and groups with permissions to folders, which I do not believe can be done with the standard chown commands.  Currently, I can see the folder permissions from my Windows box, but when I try to edit the permission settings, it defaults back to full access.  So my AD permissions are not being saved.

I would be happy to supply any of the configuration files and my setup process.

---

### Post by capscrew on 2010-07-20
> **UKccampbell said:**
> Hello all, this is my first time here and just wanted to start by saying thank you for all your work.  You have saved me many headaches in the last 3 years of running various Ubuntu projects for work.

I however have a problem, that after 2 weeks of browsing the forums and other sites, I cannot find a solution for.  Before I ask the question, some background is in order (sorry for wall of text)


I am the IT Manager at a research facility.  We have a fairly unique network configuration in order to support all of the different projects we have going on.  We have Red Hat, Ubuntu, Windows XP/Vista/7, Windows Servers 2003, Ubuntu servers, Red Hat servers, and even a few Netgear ReadyNAS and Buffalo Terastations.  Over the last few years, I have been migrating all of my users and accounts to a single ACL list, which I chose to be a Windows AD 2003 server.  95% of my users work on Windows platforms and just use ssh tunnels to develop on our linux boxes.  

However, i ran in to a problem with our Linux boxes not being able to symbolic link on my Windows 2003 file shares.  Of course, this is a problem with Windows not supporting symbolic links.  
Are you sure this is a "Windows" problem.  In the past Samba was able to follow sym links, but recently there have been changes due to security problems. See [**_here _**]("http://www.samba.org/samba/news/symlink_attack.html")> .

I know 2008 does support this feature, but given the economy and the budget restraints, we cannot afford to purchase the updates we would need, so now I am moving all of my shares to a Ubuntu 10.04 server using Samba.  I have joined the server to my AD domain successfully, i can login using my AD credentials, and even assign ownership and group permissions using AD users/groups.

Here is my question.

I would like to keep the AD permission schemes intact.  I have several shares that contain folders that have individual permission settings.  For example, I have a /shared directory that contains about 50 different folders.  Some of these folders I allow my users to write data to, some just read, and others I deny access to complete groups and just allow key groups to access (for example, personnel data should only be accessed by the Administrative staff).

Is there a way to make this work?

The permission are ultimately controlled by the file system permissions.  This means that Samba can only restrict a users ability but can't grant permission that the filesystem does not allow.> 

I can assign uid and gid manually per folder in Samba, but i would like to have the possibility to add multiple users and groups with permissions to folders, which I do not believe can be done with the standard chown commands.  

Currently, I can see the folder permissions from my Windows box, but when I try to edit the permission settings, it defaults back to full access.  So my AD permissions are not being saved.
I would look at Linux ACL's.  See [**_here_**]("http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists").> 
I would be happy to supply any of the configuration files and my setup process.

---

### Post by UKccampbell on 2010-07-20
> Are you sure this is a "Windows" problem.  In the past Samba was able to  follow sym links, but recently there have been changes due to security  problems. See [**_here_**]("http://www.samba.org/samba/news/symlink_attack.html")It actually is a Windows problem pre Server 2008.  Like I stated, the shared files are currently stored on a Windows 2003 AD server, which is formatted NTFS.  2003 uses junction points instead of symbolic links, and the two Operating Systems translate the commands differently, thus breaking the links.  2008 does support it though, but I can't buy any licenses at the moment.  However the sym links work fine within the Linux OS.

> I would look at Linux ACL's.  See [**_here_**]("http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists").I have acl's enabled, but I need the ability to give multiple users access to different directories and I would prefer not to create a different group for each directory I need to grant access to.  With Windows, I can specify multiple users and multiple users to have different access to the same folder, which is very handy to have in place.  chmod and chown work for single user/group, but again I need to be able to grant multiple user/group access to these folders.

---

### Post by UKccampbell on 2010-07-20
Here are my configuration files.  These are the files I had to update in order to log in using my domain credentials, and it tells the kernel to first look for the domain login before looking at the local /etc/passwd file for the user account.

/etc/krb5.conf
```
[logging]
    default = FILE:/var/log/krb5.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmind.log

[libdefaults]
    default_realm = XXX.XXX.XXX
    dns_lookup_realm = false
    dns_lookup_kdc = false
    ticket_lifetime = 24h
    forwardable = true

[realms]
    XXX.XXX.XXX = {
        kdc = win2003.xxx.xxx.xxx
        admin_server = win2003.xxx.xxx.xxx
        default_domain = XXX.XXX.XXX
    }

[domain_realm]
    .kerebos.server = XXX.XXX.XXX
    .xxx.xxx.xxx = XXX.XXX.XXX

[kdc]
profile = /var/kerebos/krb5kdc/kdc.conf

[appdefaults]
pam = {
    debug = false
    ticket_lifetime = 36000
    renew_lifetime = 36000
    forwardable = true
    krb4_convert = false
}
```/etc/samba/smb.conf
```
#GLOBAL PARAMETERS
[global]
   workgroup = XXX
   realm = XXX.XXX.XXX
   preferred master = no
   server string = XXXXXX
   security = ADS
   encrypt passwords = yes
   log level = 3
   log file = /var/log/samba/%m
   max log size = 50
   printcap name = cups
   printing = cups
   winbind enum users = Yes
   winbind enum groups = Yes
   winbind use default domain = Yes
   winbind nested groups = Yes
   winbind separator = +
   idmap uid = 600-20000
   idmap gid = 600-20000
   template primary group = "Domain Users"
   template shell = /bin/bash

[homes]
   comment = Home Direcotries
   valid users = %S
   read only = No
   browseable = No

[printers]
   comment = All Printers
   path = /var/spool/cups
   browseable = no
   printable = yes
   guest ok = yes

[shared]
   comment = Shared Directories
   path = /shared
   writable = Yes
   create mask = 0775
   directory  mask = 0775
```/etc/nsswitch.conf
```
# /etc/nsswitch.conf
#

passwd: files winbind
shadow: files winbind
group: files winbind

#hosts: db files nisplus nis dns
hosts: files dns wins

# Example - obey only what nisplus tells us...
#services: nisplus [NOTFOUND=return] files
#networks: nisplus [NOTFOUND=return] files
#protocols: nisplus [NOTFOUND=return] files
#rpc: nisplus [NOTFOUND=return] files
#ethers: nisplus [NOTFOUND=return] files
#netmasks: nisplus [NOTFOUND=return] files

bootparams: nisplus [NOTFOUND=return] files

ethers: db files
netmasks: files
networks: files dns
protocols: db files
rpc: files
services: files

netgroup: files

publickey: nisplus

automount: files
aliases: files nisplus
```
/etc/pam.d/common-auth
```
#%PAM-1.0
# This file is auto-generated.
# User changes will be destroyed the next time authconfig is run.
auth required /lib/security/$ISA/pam_env.so
auth sufficient /lib/security/$ISA/pam_unix.so likeauth nullok
auth sufficient /lib/security/$ISA/pam_winbind.so use_first_pass
auth required /lib/security/$ISA/pam_deny.so

account required /lib/security/$ISA/pam_unix.so
account sufficient /lib/security/$ISA/pam_succeed_if.so uid < 100 quiet
account sufficient /lib/security/$ISA/pam_winbind.so use_first_pass
account required /lib/security/$ISA/pam_permit.so

password requisite /lib/security/$ISA/pam_cracklib.so retry=3 type=
password sufficient /lib/security/$ISA/pam_unix.so nullok use_authtok md5 shadow
password sufficient /lib/security/$ISA/pam_winbind.so use_first_pass
password required /lib/security/$ISA/pam_deny.so

session required /lib/security/$ISA/pam_limits.so
session required /lib/security/$ISA/pam_unix.so
session required /lib/security/$ISA/pam_winbind.so use_first_pass
session required /lib/security/pam_mkhomedir.so
```

---

### Post by capscrew on 2010-07-20
> the shared files are currently stored on a Windows 2003 AD server, which is formatted NTFS

Sorry, I missed that.  So the files are served from a Windows host.  Then the Samba daemon (smbd) doesn't really figure into this at all.  If the Linux host has the latest package called "smbfs" (CIFS/SMB user land FS) then it should be able to mount the Windows share.  In fact any CIFS/SMB share.

But I am confused as you also state the share is at /share.  Your smb.conf file (which configures smbd) also shows it.

Can you simply state where the shares are and what type of hosts you expect to mount the shares?  Do you expect to manage Linux file permissions from a Windows Server management tool?

---

### Post by UKccampbell on 2010-07-20
> **capscrew said:**
> Sorry, I missed that.  So the files are served from a Windows host.  Then the Samba daemon (smbd) doesn't really figure into this at all.  If the Linux host has the latest package called "smbfs" (CIFS/SMB user land FS) then it should be able to mount the Windows share.  In fact any CIFS/SMB share.

But I am confused as you also state the share is at /share.  Your smb.conf file (which configures smbd) also shows it.

Instead of trying to find a solution for a sym link to work on Windows partitions, I am trying to reverse the process by keeping the data on a ubuntu 10.04 server but assign permissions from my AD.  My samba file is set up as a temporary shared folder at /shared, which I can connect to from my Windows computer to access the files there.  From there, I want to be able to assign users/groups from AD (see below)

> Can you simply state where the shares are and what type of hosts you expect to mount the shares?  Do you expect to manage Linux file permissions from a Windows Server management tool?

I don't have to manage it with a Windows Management tool, I just need to be able to assign more permissions than just uid, gid, and rwx.  For example (this is not a real example, but a hypothetical example):

My director needs to update Personnel Reviews and be able to share that data with our Administrative Assistant and our Financial Officer.  I also want users to be able to read their own reviews, but not be able to see anyone else's or make changes to anything.  So in Windows I would typically set up a directory structure and each user would have their own folder.  The root directory permissions would allow the 3 people above read/write/modify access and all of the sub folders would inherit the permissions.  Then I would just go through each user's folder and add that user to read that folder.  But there may be a folder in there that I want to add yet another person to the group of users who have read/write (for example, a low-level employee has a supervisor who may need to comment on the review).  

I need to be able to replicate that kind of permission flow in a Ubuntu box.  it doesn't have to be identical to the Windows management tools, but somehow be able to assign multiple users and groups access to directories

---

### Post by capscrew on 2010-07-20
> **UKccampbell said:**
> Instead of trying to find a solution for a sym link to work on Windows partitions, I am trying to reverse the process by keeping the data on a ubuntu 10.04 server but assign permissions from my AD.  My samba file is set up as a temporary shared folder at /shared, which I can connect to from my Windows computer to access the files there.  From there, I want to be able to assign users/groups from AD (see below)



I don't have to manage it with a Windows Management tool, I just need to be able to assign more permissions than just uid, gid, and rwx.  For example (this is not a real example, but a hypothetical example):

My director needs to update Personnel Reviews and be able to share that data with our Administrative Assistant and our Financial Officer.  I also want users to be able to read their own reviews, but not be able to see anyone else's or make changes to anything.  So in Windows I would typically set up a directory structure and each user would have their own folder.  The root directory permissions would allow the 3 people above read/write/modify access and all of the sub folders would inherit the permissions.  Then I would just go through each user's folder and add that user to read that folder.  But there may be a folder in there that I want to add yet another person to the group of users who have read/write (for example, a low-level employee has a supervisor who may need to comment on the review).  

I need to be able to replicate that kind of permission flow in a Ubuntu box.  it doesn't have to be identical to the Windows management tools, but somehow be able to assign multiple users and groups access to directories

Not going to happen.  The file systems are incompatible  in that way.  Not being able to implement multiple groups has long been a failing of Linux FS.  When I say this I am referring to the standard EXT FS.  I am not sure about the others.  You might check BtrFS.  This will be the file system of the future for Linux.

---

### Post by UKccampbell on 2010-07-20
I was afraid that was the answer.  Oh well, back to the drawing board.

---

### Post by capscrew on 2010-07-20
> **UKccampbell said:**
> I was afraid that was the answer.  Oh well, back to the drawing board.

Sorry there was no magic bullet.  :-(

---

### Post by mcarrara on 2010-07-20
While I am not using AD and have never tried them there is some support for Access Control Lists in Samba.  You may want to look at them and see if that is what you need.

Mark

---

