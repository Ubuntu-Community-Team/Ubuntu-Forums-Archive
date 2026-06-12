---
title: "LDAPv3 - Ubuntu Desktop 11.10 - Open Directory"
date: 2011-10-19
forum: Server Platforms
---

### Post by FiVAL on 2011-10-19
Hi / Hello !

Here at our company we like to mix everything together. So our Open Directory server is Apple's OS X. Our clients are Windows XP (most), Apple OS X (second most) and the developers work with Ubuntu. The Windows and the OS X users work now for a couple of years perfect on the Open Directory Server without problems. Their environments are in sync and access is granted... Because we want for new workstations to shift to Ubuntu. Ubuntu also has to get connected with the Open Directory Server. This is the part we get stucked.

(see also [http://ubuntuforums.org/showthread.php?t=1863140](http://ubuntuforums.org/showthread.php?t=1863140))

After a tip from this forum I started with LDAPv3 with "succes" on this Ubuntu Desktop! When I use the commands '**getent passwd**' & '**getent group**' i see all my network accounts. Also can i use my network user accounts to login locally with ssh, '**ssh networkuser@localhost**'.

_Only now I have a very strange error_. When I use this ssh command to login, the system creates a homedirectory in '**/99/99/**' or sometimes in '**/dev/99/**' !! Does anyone knows what I did wrong?

(logging in by the loginscreen of ubuntu 11.10 does nothing at all. The authentication goes OK, but then a black screen fliks and I'm back in my login screen... How ever, this is my second problem. First i want to fix my homedirectory problem.)

ThX!

-------------

I installed & configured:
```
sudo apt-get install libnss-ldapd libpam-ldapd
```

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         files ldap
group:          files ldap
shadow:         files ldap
hosts:          files dns ldap
networks:       files
protocols:      db files
services:       db files
ethers:         files ldap
rpc:            db files
netgroup:       ldap nis
```

```
#
# /etc/pam.d/common-session - session-related modules common to all services

# here are the per-package modules (the "Primary" block)

session [default=1]                     pam_permit.so

# here's the fallback if no module succeeds

session requisite                       pam_deny.so

# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around

session required                        pam_permit.so

# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".

session optional                        pam_umask.so umask=002

# and here are more per-package modules (the "Additional" block)

session required                        pam_unix.so
session optional                        pam_mount.so
session [success=ok default=ignore]     pam_ldap.so minimum_uid=1000
session optional                        pam_ecryptfs.so unwrap
session required                        pam_mkhomedir.so skel=/etc/skel/ umask=0022
session optional                        pam_ck_connector.so nox11

# end of pam-auth-update config
```

---

### Post by newbie-user on 2011-10-19
Where are your home directories located?  In my setup, our home directories are located on an nfs share on the OpenDirectory server, and we mount the nfs share on the Ubuntu desktops in /etc/fstab.

---

### Post by FiVAL on 2011-10-20
From the Ubuntu Desktop he could mount his HomeDir by SMB, AFP or SSH on this Apple OpenDir Server. (with the Windows and Apple clients no problem)

But I didn't put anything in the FSTAB. Do you have an sample?
Also I want to keep 1 or 2 local user accounts on this desktop with there own HomeDir (if possible).

---

### Post by FiVAL on 2011-10-20
I have made a big progress thanks to you!

First of all I did make a mistake on the server in the OpenDir with my test account. I did forget the enter a location for the homedir. Now I did (just like the other Apple User Accounts) and Ubuntu Desktop gives an error when i try to login:
*Unable to create and initialize directory '/Network/Servers/<servername>/Users/<user>'*

So I guess I have to make a local directory: '/Network/Servers/<servername>/Users/' and mount this (by the FSTAB) with the server! :-)

An examples that I found was:
```
//ntserver/docs /mnt/samba smbfs username=docsadm,password=D1Y4x9sw 0 0
```

BUT the username and password I can't give of course. It has to be by LDAP. Or does the Desktop mount BEFORE i login on the Desktop??

---

### Post by FiVAL on 2011-10-20
Okeej, I hope i'm almost there.. :-)
I don't think I need to use FSTAB, but the libpam-mount & smbfs.

First I did make a local mountpoint directory (in the same way as my Apple Clients):
**/Network/Servers/<servername>/Users/**

And tried the following command while I was logged in on the Ubuntu Desktop with a local administrator account:

```
sudo smbmount //<server>/<..>/users/ /Network/Servers/<servername>/Users/ -o user=<networkLDAPtestuser>
```

This is working perfect!!

So I guess that I now have to find out how the pam_mount.conf.xml has to be configured so I can mount at login.

An other thing I still don't get. If this will work, what will happen when (by ssh) a second person will login at the same desktop!?

---

### Post by newbie-user on 2011-10-20
Cool.  Use whatever method works best for your environment.

Here's what I do on my client computers to get them to load the home directories at login:

1.  in /etc/fstab:
[server]:/path/to/folder/containing/homedirs /Network/Servers/[server.example.net]/path/to/folder/containing/homedirs nfs rsize=8192,wsize=8192 0 1

2.  mkdir -p /Network/Servers/[server.example.net]/path/to/folder/containing/homedirs


This, of course, assumes you have an nfs share for the folder containing the home directories.  In my setup, a second user can ssh into a client while another user is logged in and it will load the home directory for the second user.

Also, all local accounts on the client will still be able to log in and have local home directories.  Oh, and nfs-common has to be installed on the Ubuntu client in order to access the nfs shares.  I believe you can also set up the samba shares in fstab so that it will automount when the client boots.

---

### Post by FiVAL on 2011-10-20
(I reply by my mobilephone, so i keep it very short)

What I don't understand in your config, which user mounts?
I guess the root, because you use the FSTAB.
Are the homedirs then still private between the first and the second user how are working at the same time??

---

### Post by newbie-user on 2011-10-20
The setting in fstab mounts the nfs share.  On the server, the nfs share is the folder that contains all the home directories.  So the client computer mounts the nfs share when it boots.  This means that all home directories are available for access, depending on which user logs into the client.  The nfs share itself, though, is readable by all.  The home directories are still private and the permissions are set on the server itself, so even if another user logs in, they can't access any other user's folder.

The user's homedir is set in OpenDirectory to /Network/Servers/[server]/path/to/home/[username] and fstab mounts /Network/Servers/[server]/path/to/home.

So here's the script I use to add users to OpenDirectory.  The script needs to be run on the OpenDirectory server and requires the first and last names of the user and the user's UID.  We manually assign the UID and use it as the user's initial password.  Change [GID], [admin password], [group name], and /path/to/ to suit your needs.

#!/bin/bash
#
#This script adds a new user to OpenDirectory 081211
#
#Usage: ./newuser.sh [firstname] [lastname] [uid]

#Creating user account:
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -create /Users/$1$2
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -create /Users/$1$2 UserShell /bin/bash
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -create /Users/$1$2 RealName "$1 $2"
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -create /Users/$1$2 UniqueID $3
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -create /Users/$1$2 PrimaryGroupID [GID]

#Creating home directory:
mkdir /path/to/home/$1$2
chown -R $1$2:[group name] /path/to/home/$1$2
chmod -R 700 /path/to/home/$1$2
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -create /Users/$1$2 NFSHomeDirectory /Network/Servers/[server]/path/to/home/$1$2

#Set password:
dscl -u diradmin -P [admin password] /LDAPv3/127.0.0.1 -passwd /Users/$1$2 $3

---

### Post by FiVAL on 2011-10-25
@newbie-user

NFS is also the solution for me!
Everything works (in the terminal) perfect...

But now I have to following problem:
[https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874?comments=all](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874?comments=all)

Are U already using Ubuntu 11.10 (AMD64) with lightdm?

---

### Post by newbie-user on 2011-10-27
I haven't tried it with the 64-bit version of 11.10.  I'll try the 64-bit next.  I do seem to have a problem with the 32-bit version where it doesn't seem to load the permissions correctly for the nfs share.  In this problem, Ubuntu 11.10 doesn't seem to pass the correct username to OpenDirectory, so access is denied to the home directory.  This is solved by changing the permissions on the home directory to 755, then the user can log in, but this is not an acceptable solution.  I'll look more into it and try the 64-bit version.  Too bad, though, it worked perfectly in 10.04.  :(

---

### Post by newbie-user on 2011-10-27
Okay, so I've tested it with 11.10 x64 and I can get users to log in only if I set the permissions on their home folders to 701 instead of 700.  I'm not really sure what's going on there.

---

### Post by newbie-user on 2011-10-28
> **FiVAL said:**
> @newbie-user

NFS is also the solution for me!
Everything works (in the terminal) perfect...

But now I have to following problem:
[https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874?comments=all](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874?comments=all)

Are U already using Ubuntu 11.10 (AMD64) with lightdm?

I read through that bug report again and noticed that they used autofs.  Personally, I've never been able to get autofs to work in my setup.  Here's what I have installed on my Ubuntu 11.10 client:

1. libpam-ldap (answer "no" to root as database admin, choose ldap version 3, no ldap privileges for root, no database require login)
2. libnss-ldap
3. nfs-common

My /etc/ldap.conf was edited as follows (pam_filter is an added line at the end of the conf file):

base cn=users,dc=[server],dc=[domain],dc=[net] 
uri ldap://[server ip]
nss_base_group cn=groups,dc=[server],dc=[domain],dc=[net]?one
pam_filter !(uid=root)

My /etc/nsswitch.conf is as follows:

passwd: files ldap 
group: files ldap 
shadow: files ldap

And /etc/fstab was as previously posted, along with mkdir -p ...

That's all there is to my client setup.

---

### Post by FiVAL on 2011-11-04
Sorry for the late reply. But we had big trouble with
an exchange server... So the planned move from exchange
to courier for December came early :-)

NeXt week a gonna test again on the Ubuntu Login.

The last status for me was also autofs with gdm.
(and did very good, i believe)

---

