---
title: "Samba struggles"
date: 2009-03-04
forum: Server Platforms
---

### Post by Lumpy3 on 2009-03-04
I'm still trying to configure a basic Ubuntu Server 8.10 for home use.  All I'm looking for to start with is a simple network share for Music, Video and backups of the various WinXP computers we have.

I'm a linux newb, but I must have read about 500 pages by now so I'm getting somewhere.

I've used the guide on this forum:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
to set up my smb.conf file.

I've named the Ubuntu Server "Atom-NAS"  From my xp computer I can ping the IP addy fine.  I can also see the server Atom-nas (different capitolization) in my Workgroup Computers.  But, when I double click on it I get  a WinXP error that //Atom-nas is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access perissions.  The network path was not found.

I've used both sudo useradd to add my XP login name/password and smbpasswd to set up a samba user with the same name/password.

Any idea what I'm doing wrong?

Thanks.

---

### Post by Lumpy3 on 2009-03-04
Here is my smb.conf



[global]

## Browsing/Identification ###

netbios name = Atom-NAS
server string = 
workgroup = MSHOME
wins support = yes
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SNDBUF=8192


#### Networking ####

interfaces = 10.10.10.0/8 eth0
bind interfaces only = yes

#### Debugging/Accounting ####


####### Authentication #######

security = user
;encrypt passwords = true
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
syslog = 1
syslog only = yes


########## Domains ###########

########## Printing ##########

############ Misc ############

#======================= Share Definitions =======================

;[homes]
   ;comment = Home Directories
   ;browseable = no

[Music]
   path = /media/sdb1/Music
   browseable = yes
   read only = No
   guest ok = No
   create mask = 0644
   directory mask = 0755
   force user = Kurt
   force group = Kurt

---

### Post by Lumpy3 on 2009-03-04
Also, if I 
smbclient -L Atom-NAS
I get the error:
Connection to Atom-NAS failed (Error NT_STATUS_CONNECTION_REFUSED)

I get this error if I use the IP instead of the server name also.

Any help is appreciated.

---

### Post by HermanAB on 2009-03-04
Here is a doc on debugging Samba problems:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by happyhacker on 2009-03-04
I probably went through the same struggles as you and having played with Samba for several weeks getting more confident. But I installed webmin which gives me GUI access to all of Sambas configuration. I would not do without it now so highly recommend you install it. You can also access the Ubuntu users and add them, etc. (I assume you've configured these so the windows PCs are recognised).

If you cant ping or access at the level you describe then your problem is probably not Samba. I use workgroups so make sure these are the same on both/all machines. The problem may also be with the hosts file on Ubuntu. Bit of a novice myself, hope this helps.

---

