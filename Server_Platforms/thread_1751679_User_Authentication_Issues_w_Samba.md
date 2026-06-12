---
title: "User Authentication Issues w/ Samba"
date: 2011-05-06
forum: Server Platforms
---

### Post by fubeca6 on 2011-05-06
I have a small windows/ubuntu network setup with a samba server hosting shared files. I have two users who need to access the shares. I can authenticate with one user "chad" (from either win or ubuntu) but not the other "maegen". 

Both users have local accounts on the server and have logged in via $su [user] in the terminal. Both accounts are pretty identical.

Here's the [global], [authentication] and custom shares area of my smb.conf file, please let me know if you have any ideas!

```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LINES
   netbios name = server

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
   os level = 33
###**** The Following Lines are being added 05/04/2011 ****
   preferred master = true
   domain master = true
   local master = yes
;  os level = 200
;  wins support = yes

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = yes

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast



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
#   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


# Shared 500GB HardDrive on server:

[User_Home]
    path = /home
    read only = no
    writable = yes
    browsable = yes
    valid users = chad maegen

[Shares]
    path = /media/Shared_Files
    read only = no
    writable = yes
    browsable = yes
    valid users = chad maegen



```Thanks!

---

### Post by Toz on 2011-05-06
Have you added maegen to the local samba password file?
```
sudo smbpasswd -a maegen
```

---

