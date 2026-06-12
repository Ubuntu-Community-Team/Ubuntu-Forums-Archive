---
title: "Ubuntu File Server in Windows Domain"
date: 2008-01-08
forum: Server Platforms
---

### Post by uncle hammy on 2008-01-08
Hi all,

I am trying to install a file server running Ubuntu Server 6.06 in our windows Active Directory Domain.  

So far, I have successfully successfully configured the server and joined the domain, as outlined here [http://ubuntuforums.org/showthread.php?t=280702&highlight=kerberos+on+dapper](http://ubuntuforums.org/showthread.php?t=280702&highlight=kerberos+on+dapper) 

I have enabled acl support in fstab when / is mounted.

I have configured /etc/samaba.smb.conf with a share [Data] as follows...

[data]
comment = data share on storage2
path = /home/shares/data
read only = no
create mask = 0775
directory mask = 0775
browsable = yes
public = yes
writable = yes
force create mode = 0775
force directory mode = 0775
force security mode = 0775
guest ok = no
inherit permissions = yes
nt acl support = yes

I have created a directory /home/shares/data set up as follows...

owner: root
chmod -R o= /home/shares
setfacl -R -m g:'DOMAIN\Domain Admins':rwx /home/shares
setfacl -R -x g:'DOMAIN\Domain Users' /home/shares

Now, when viewing the share from a windows workstation, the permissions on the share are correct (server\root: full control, domain\domain admins: full control, domain\everyone: no permissions).  However, I have the following issues, and seem unable to resolve them so far...

1.  If I create a directory or file in the share, the permissions are correctly inherited down, but it also adds a read & write entry for DOMAIN\Domain Users.  Now, because I can modify ACL entries to files created in the share, I can remove this entry, but I would really rather it didn't appear in the first place...just inherit the permissions on the from the "root" share, and no more.

Can anyone provide some assistance sorting out these issues?

TIA,
Hammy

---

### Post by uncle hammy on 2008-01-08
Just an update...

I determined that in fact it's worse than I realized...

If I create a directory (from windows) in the share, it actually gives the group Domain Users full control to the directory.

If I create a file (from windows) in the new directory created in the share, it gives the group Domain Users read & write to the file.

If I create a file (from windows) in the share, it gives the group Domain Users read & write to the file.

---

### Post by njparton on 2008-01-08
Guest ok = no and public = yes potentially won't help.

Use one or the other, they both aim to do the same thing.

If you're trying to force the use of usernames passwords use:

guest ok = no

otherwise use:

guest ok = yes

to allow universal access (well not literally, access from within your LAN).

Find a good samba options guide on the web, a lot of the options avaible or similar to one another (or identical as in this case).

---

### Post by uncle hammy on 2008-01-08
Doesn't seem to make a difference. 

As far as I can piece together from testing, I think it has to do with the Linux user/group/other permission structure....

It seems that when I create a directory / file from windows in the share the following happens...

1.  Linux user/group/other permissions are set according to the chmod settings of the parent folder. 
     a. DOMAIN\My User is set as owner, and gets the inherited Linux "user" permission
     b. DOMAIN\Domain Users is selected from my active directory group memberships and gets the inherited Linux "group" permissions
     c. DOMAIN\Everyone gets the inherited Linux "other" permission

2. ACL entries added via setfacl are then inherited down as well

Trying various combinations of chmod doesn't seem to make a difference either.  For example, if I set the owner on the root share as root:DOMAIN\Domain Admins, when a file is created, it still makes the owner group on the new file as DOMAIN\Domain Users.

---

### Post by njparton on 2008-01-08
In your original post you seem to suggest that you've given "everyone" no permissions to the share yet you seem to be asking why "everyone" are having problems.  Have I got that correct?

Also check the global create masks and other options higher up the samba config file.

In fact, can you post your complete smb.conf file?

---

### Post by uncle hammy on 2008-01-08
No,

"Eveyone" seems to be fine, it inherits the "other" permissions from the default ACL of the share.

However, an ACL entry for "Domain Users" is always added to new Directories or Folders created from windows in the share.  It adds a rw permission for files, or a rwx permission for directories.

I am assuming it is pulling "Domain Admins" from the group membership of the user who creates the file / directory and using it as the group in the default ACL.  Mostly because getfacl /new directory shows "DOMAIN\Domain Admins" in the first group: line.

I guess what I am trying to do (and may bot be able to) is remove ALL permissions from the share, then add back my own ACLs, and have any files or folders in the share inherit only those ACLS, as well as a single new ACL for the creator of the file / folder.

Something like...

chmod u+rwx /share
chmod go-rwx /share

setfacl -m g:'DOMAIN\Domain Admins':rwx /share
setfacl -m g:'DOMAIN\Some Group':rw /share
setfacl -m u:'DOMAIN\Some User':r /share

My idea is now, Domain Admins have rwx, Some Group has rw, Some User has r access to the share, and any files of directories created in it (both existing and new ones when created)....and that's it.

Dose that make sense?

My smb.conf file...

[global]
workgroup = BUIST
realm = BUIST.BC
server string = %h server (Samba %v, Ubuntu)
wins support = no
wins server = 10.10.1.9
password server = VS1
enable privileges = yes
allow trusted domains = no
dns proxy = no
name resolve order = host wins bcast
log file = /var/log/samba/log.%m
max log size = 1000
log level = 3
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = ADS
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
invalid users = root
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
printing = cups
printcap name = cups
cups options = raw
socket options = TCP_NODELAY
time server = yes
map to guest = nobody
idmap uid = 16777217-33554431
idmap gid = 16777217-33554431
winbind enum users = yes
winbind enum groups = yes
template shell = /bin/bash

#======================= Share Definitions =======================
[data]
comment = data share on storage2
path = /home/shares/data
read only = no
create mask = 0775
directory mask = 0775
browsable = yes
public = yes
writable = yes
force create mode = 0775
force directory mode = 0775
force security mode = 0775
guest ok = no
inherit permissions = yes
nt acl support = yes

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700

---

### Post by uncle hammy on 2008-01-08
> **uncle hammy said:**
> 
Something like...

chmod u+rwx /share
chmod go-rwx /share

setfacl -m g:'DOMAIN\Domain Admins':rwx /share
setfacl -m g:'DOMAIN\Some Group':rw /share
setfacl -m u:'DOMAIN\Some User':r /share
When I try this, the chmod entry that removes permissions for the group owner entry (chmod go-rwx) sets a mask that all extended ACL group entries inherit.  So, when I add extended ACL entry for Domain Admins of rwx, it ends up with an effective permision of nothing.

I seem to be going around in circles.

---

### Post by koenn on 2008-01-08
It might have something to do with the

create mask = 0775
directory mask = 0775

force create mode = 0775
force directory mode = 0775
force security mode = 0775


which govern the permissions of newly created files/directories. You probably have to look those up (man) and look into man umask as well to see if you can get the desired effect. 

The unix / linux permissions also have a bit that makes files inherit permissions of their parent dir rather than through the user/group that creates them. IRC this is set on the parent directory - i forgot wat it's called - could be the 'sticky' bit.

---

### Post by uncle hammy on 2008-01-08
That makes sense (perfect sense in fact).  However, I have played around with various settings I even set....

create make = 0000
directory mask = 0000
force create mode = 0000
force directory mode = 0000

which as far as my bit math tells me should be no permissions for u,g,o for files or directories being created or copied from windows to linux.  

Same deal though...new files are created with a group owner of "Domain Users" with a rw permission, and new directories are created with a group owner of "Domain Users" with a rwx pemrission.  Go figure?

I also played around with force group / force user.  If I add a line

force group = 'DOMAIN\Domain Admins'

then all access to the share from windows is lost.

---

### Post by uncle hammy on 2008-01-08
Got it!(sort of)

create mask =, etc doesn't work correctly still.

However, I ended up creating my share, then...

chown administrator:'DOMAIN\Domain Admins' /share
chmod u+rwx,g+rw**s**,o-rwx /share

the setflag(s) in the group permission was the ticket.  Now all directories and files created within the share inherit the parent's group, rather than the creating user's primary group.

I would still like to figure out what's up with the create masks though

---

### Post by koenn on 2008-01-08
> the setflag(s) in the group permission was the ticket
yep, that s is the one I couldn't remember

I've never had to worry about those create masks, so I don't know wha's the deal with them, either.

---

### Post by telecomando on 2008-02-11
I am having the same issue on a server I set up.  But you lost me in the shuffle here.  What exactly did you do to fix this "everyone" issue?
Thanks!

---

### Post by telecomando on 2008-02-27
So I finally figured it all out.  I was still having certain groups show up in shares that should not be there, IE domain users.  No matter what I did it would always be there.
So what you need to do is 
setfacl -b /somepath/somefolder
(or setfacl -k /somepath/somefolder to remove the default permissions as well.)
to remove all the ACL entries, the use setfacl to add your permissions.
The "Everyone" group still shows up, but that is mapped to the "other" group so I think it will always be there, with no permissions.

---

