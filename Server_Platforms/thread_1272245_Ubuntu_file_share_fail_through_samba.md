---
title: "Ubuntu file share fail through samba"
date: 2009-09-21
forum: Server Platforms
---

### Post by Scorc on 2009-09-21
:popcorn:
So i just installed Ubuntu Server Edition i386 on an old comp and my Win7 x64 does cannot edit/creat files that the Samba program hosts..XP can tho so I am a bit lost but as Win7 is just RC1 that might be all there is to the problem. When I try to edit I get a "acsess denied" msg. Is there another setting I need to change in smb.conf? or am i just f'd and reduced to using FreeNAS instead? The server was to host files for my computers so I didn't have to download updates 5million times (...exageration, but still a lot of times) and to netwrok a printer to the house (which is why I chose Ubuntu).
 
 
 
 
 
....And yes, I am a lame Win user who knows very little a bout the linux os's.
 
 
Thank you for you time and help in advance.

---

### Post by alienatom on 2009-09-21
Did you make sure your Windows 7 is using the same workgroup name?

Sometimes is mshome or workgroup or whatever you set it up to be. It believe it needs to match whatever samba has setup in the samba configuration file. I haven't used WIN7 but you can usually check by right clicking on my computer then properties then computer name or something similar. It should be there someplace.

---

### Post by alienatom on 2009-09-21
You also might have to edit the /etc/samba/smb.conf file in the shares section to read something like this if you want all users to have access to do whatever to the files. This gives read and write-ability. I am not sure if this setup is proper but it works.

[movies]
        comment = movies to share
        path = /media/share/movies
        browseable = yes
	writeable = yes
	read only = no
	guest ok = yes

Just change the path to wherever your files reside.
You might have to set the directory to writable as well.
If you want to go all out no restrictions.

---

### Post by Scorc on 2009-09-22
Win7 has the correct workgroup (used the default..which was WORKGROUP in both nicly enough)

---

### Post by openfly on 2009-09-22
Are you using the same user / pass to connect in both situations?  Also check the perms on the directories and files.  Dump examples if you can.

---

### Post by Scorc on 2009-09-22
> **alienatom said:**
> You also might have to edit the /etc/samba/smb.conf file in the shares section to read something like this if you want all users to have access to do whatever to the files. This gives read and write-ability. I am not sure if this setup is proper but it works.
 
[movies]
comment = movies to share
path = /media/share/movies
browseable = yes
    writeable = yes
    read only = no
    guest ok = yes
 

 
 
Did not work. It is a permissions thing on Win7's part. "it does not own/have write acess" And there is no way to input my Win7 acct into the Ubuntu/samba as far as I know, which would solve the problem I think.

---

### Post by Scorc on 2009-09-22
> **openfly said:**
> Are you using the same user / pass to connect in both situations? Also check the perms on the directories and files. Dump examples if you can.
 
Not completly sure what you are talking about but I used [https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html)
to set up the file server so I created the dir and then set the permissions. It does not require a password from XP but for Win7 I just login using my Ubuntu user/password.

---

### Post by Scorc on 2009-09-22
wait,
 
>  
First, edit the following key/value pairs in the *[global]* section of /etc/samba/smb.conf: 
workgroup = EXAMPLE
... 
security = user
The *security* parameter is farther down in the [global] section, and is commented by default. Also, change *EXAMPLE* to better match your environment. 

 
and
 
>  
After installing samba edit /etc/samba/smb.conf. 
Change the *workgroup* attribute to what is appropriate for your network, and change *security* to share: 
workgroup = EXAMPLE 
... 
security = user
 
Does that mean that I need to change the word security to share or change user to share?
 
 
Current settings
 
>  
#======================= Global Settings =======================
 
[global]
 
 

   workgroup = WORKGROUP
 
   server string = %h server (Samba, Ubuntu)
 
#   wins support = no

;   wins server = w.x.y.z
 
   dns proxy = no

;   name resolve order = lmhosts host wins bcast
 
#### Networking ####

;   interfaces = 127.0.0.0/8 eth0
 
;   bind interfaces only = yes
 
 
 
#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
 
   max log size = 1000

#   syslog only = no

   syslog = 0
 
   panic action = /usr/share/samba/panic-action %d
 
 
####### Authentication #######
 
#   security = user

   encrypt passwords = true
 

  
   passdb backend = tdbsam
 
     obey pam restrictions = yes
 
   unix password sync = yes
 
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 
   pam password change = yes
 
 
   map to guest = bad user
 
########## Domains ###########
 
;   domain logons = yes
 
;   logon path = [\\%N\profiles\%U]("file://%25n/profiles/%25U")

#   logon path = [\\%N\%U\profile]("file://%25n/%25U/profile")
 
 
;   logon drive = H:
#   logon home = [\\%N\%U]("file://%25n/%25U")
 
 
;   logon script = logon.cmd
 
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
 
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
 
 
; add group script = /usr/sbin/addgroup --force-badname %g
 
########## Printing ##########
 
#   load printers = yes
 
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
 
############ Misc ############
 

;   include = /home/samba/etc/smb.conf.%m
 

#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY
 

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
 
 
#   domain master = auto
 
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
 

;   winbind enum groups = yes
;   winbind enum users = yes
 
 

;   usershare max shares = 100
 
   usershare allow guests = yes
 
#======================= Share Definitions =======================
 

;[homes]
;   comment = Home Directories
;   browseable = no
 

;   read only = yes
 
;   create mask = 0700
 
;   directory mask = 0700
 

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
;   write list = root, @lpadmin
 
 
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
 
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
 

[share]
 
 comment = Ubuntu Storage
 
 path = /srv/samba/data
 browsable = yes
 guest ok = yes
 read only = no
 create mask = 0755


---

### Post by alienatom on 2009-09-22
Try this website... it helped me out when I was trying to sort all of this out.

[https://calomel.org/samba.html](https://calomel.org/samba.html)

I use security = share
And my smb.conf is pretty much what that website shows.

I don't have Win7 running on my network but I have Vista and that crappy system can access the samba share.

One thing I had to do was to chmod the directory to writeable so any user could write to it. That is, chmod to 0777 the directory you want to be able to work with. You can then set up access to it via the samba config. 

For example, 

chmod 777 /media/share/movies 
Then open up the samba config and set it to read only or writeable. Or define users that have access it to instead of guests. Just be careful make sure you don't chmod any directories which could compromise your system. 

Anyway.. check that website out because it breaks down the settings and what they do pretty well.

---

### Post by Scorc on 2009-09-23
totally gonna try/use that....first bit of helpfulness that i got sofar...i tried the liux part of cnet and they just kept trying to get me to do it from Win7...but my printer is so old the RC doesnt have the driver for it and XP  doesnt have any of the other drivers to be able to network it.

---

### Post by badger_fruit on 2009-09-23
here's an example SMB.conf file which I copy to any new installs I do (any distro), restart samba and it just works.

```

[global]
        printing = cups
        printcap name = cups
        cups options = raw
        map to guest = Bad User
        include = /etc/samba/dhcp.conf
        usershare allow guests = Yes
        netbios name = MYCOMPUTERNAME
        workgroup = MYWORKGROUP
        server string = "COMPUTER DESCRIPTION"
        name resolve order = bcast host lmhosts wins

[A_SHARE]
        comment = SHARE COMMENTS
        path = /path/to/share
        guest ok = yes
        read only = no
        force user = name_of_local_user

```

You'll need to modify some bits to suit your needs but they'll be quite apparent I hope!

---

