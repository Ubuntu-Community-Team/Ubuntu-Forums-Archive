---
title: "SMB share asks for password"
date: 2015-12-23
forum: Server Platforms
---

### Post by exsheeple on 2015-12-23
Im trying to share file from my PC running Ubuntu 14.04 with a media player running Kodi using windows network SMB.  Its asking for a password but I have setup one.  I tried my ubuntu login, negative.  Any ideas or guidance?  Thanks

---

### Post by Elishasmantle on 2016-01-01
Hello,

I followed this guide. This creates a samba share folder with no password required. You can set it up to only allow read access to the folder.
Much easier than if you need a username and password setup for Samba.

Thank You,

Elishasmantle

---

### Post by xsnake_ on 2016-01-01
What guide, if I may ask?

---

### Post by matt_symes on 2016-01-01
Thread moved to **Server Platforms**

---

### Post by MAFoElffen on 2016-01-01
What version of Samba are you using? Samba Version 4 on uses stronger password rules than previous versions.

But first, I'm sorry, but there are multiple ways to do so many things in Samba. Please try to be a little more specific in what you are trying to do or what you are having problems with. For instance, you mentioned 2 different things in your first post.
(1 of 2) Could mean that you setup a share, but when it asks for a username and password you could not login to access it. Usernames and passwords through net via smb--> 
```

smb://username:password@workgroup/server

```
Where the username and password of some user that has access "ON" the Server that Samba is a service of (where the share is) ... (not the client's computer) That is assuming a for a normal / default configured share.

You could enter your username and password when prompted, during the connect tot he share, or through a locally kept client credential file.

But you could also set up a samba user outside of pam (the server users list) where you can setup a user password for a samba user...

(2 of 2) Could be interpreted as you want to create a public share that does not need a username or password ... which there are several ways to do that. One would be to configure a public share, rights given to guests, that do not need a password to access. Another would be to configure access to your share from clients by IP address (which might fit what you mention).

Like I said, that one post could go 6 different ways, depending how someone interprets what you said. So what are you trying to do? I'll try to give you enough information for your to choose what might be best for that.

---

### Post by darkod on 2016-01-01
Couple of things to take into account for samba shares and user security:
1. I believe there has to be a samba user with the identical password and username as the user trying to access the share. With recent samba versions it is enough to create this samba user. Earlier also an identical linux user had to exist.

2. Regardless of the samba user you allow to access the share, linux file permissions are separate subject. You have to make sure the file/folder you are sharing has correct permissions to allow access by the user/group.

---

### Post by MAFoElffen on 2016-01-01
Samba can be configured to use a Samba User instead of Linux system user... I  think that is a duplication of efforts, and I administer things through a user... (manage as a piece of a larger picture and working together.)

Snip from my smb.conf
```

[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   name resolve order = bcast host lmhosts wins # <-- changed order fixes smb mounts on my network 


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


####### Authentication #######


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


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

############ Misc ############


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes




```
So login is a Linux user and their credentials ... I have no additional Samba users nor Samba passwords that I have to manage. Samba is just another service on that server...

As for permissions of a share:
```

[share1]
  comment = Home
  browsable = yes
  path = /home/mafoelffen/share1
  guest ok = no
  read only = no
  create mask = 0777

[Public Share1]
path = /home/public/share1
available = yes
writable = yes
browsable = yes
public = yes
guest ok = yes
guest only = yes
guest account = guestuser
# add a user name guestuser
# useradd -c "Guest User" -d /dev/null -s /bin/false guestuser

# passwordless
[Public Share2]
writable = yes
path = /home/public/share2
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes

```

---

### Post by MAFoElffen on 2016-01-01
Now if you were to add a Samba User outside of PAM, then you a a Linux User (if prior to Samba v4), add a samba user (if prior to Samba v4, then the same name as a Linux User), then add the username to the list of users in the "Account section of the smb.conf file...

But starting with Samba 4, then you can have a Samba user without having a Linux User...
so
```

adduser [COLOR=#ff0000]myNewUserName[/COLOR]
smbpasswd -a [COLOR=#ff0000]myNewUserName[/COLOR]

```
And the authorized samba user lists in each share section Example is for an accounts data share:
```

[accounts]
comment = Accounts data directory
path = /data/accounts
valid users = mfrior salivak raja [COLOR=#ff0000]myNewUserName[/COLOR]
public = no
writable = yes

```
But that is assuming that you did not setup users like my last post, to be validated by PAM.

But a different example of share access by Linux user group:
```

[accounting]
    comment = Accounting Department Directory
    writable = yes
    valid users = @account
    path = /home/samba/accounting
    create mode = 0660
    directory mode = 0770

[engineering]
path = /home/samba/engineering
guest ok = no
guest only = no
write list = @engineering
read list = 
valid users = @engineering

```

So ... in the last 2 posts is a myriad of different ways you can set access to Samba Shares.

---

### Post by darkod on 2016-01-02
But the root share folder still has to have correct read-write permissions for the user/group that will be using it, right? I mean, the 'create mode' and 'directory mode' take care of permissions for newly created items, but the folder where you are putting the share has to allow writing/access to start with, no?

This is what I meant when mentioning to double check permissions.

---

### Post by MAFoElffen on 2016-01-03
Yes, you are right. Access/permission are allowed by order of precedence, You can allow something then filter and restrict. You cannot allow anything that is already denied. It can be explicit or inherited. Explicii would be "this specific user" has this.
 
> 
Limits set by kernel-level access control such as file permissions, file system mount options, ACLs, and SELinux policies cannot be overridden by Samba. Both the kernel and Samba must permit the user to perform an action on a file before that action can occur.

Inherited order of precedence of users types go by:

... it goes by most general, then collapses along the way to less general/more specific--> other, groups, users.

Groups, users, and special identities in the domain
Groups and users in the domain and any trusted domains
Local groups and users on the computer where the object resides


Order of precedence of systems go by:
Linux System permission
Filesystem permissions
Samba permission

So a filesystem cannot be written to if no one has access to it with write permissions. Samba cannot write to a file system that was opened or mounted as as read-only...

So yes, Linux permissions have to be hierarchically set to be to read/write as appropriate, before the smb.conf can filter restrictions from those permissions. I sort of take that for granted, sometimes, that those things go hand-in-hand.

---

