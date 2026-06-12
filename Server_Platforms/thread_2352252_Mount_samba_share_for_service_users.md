---
title: "Mount samba share for service users"
date: 2017-02-11
forum: Server Platforms
---

### Post by vader699 on 2017-02-11
I have a been searching for quite some time for a solution to my issue and have failed to find one that works.

I have a server that has all my media files on it.  I have a desktop that is running transmission with a vpn on it.  I am wanting to mount a share from the server to the desktop so that I can automatically place the files from transmission onto the server, they are being processed by sickgear running under user sickbeard.  When sick gear tries to process downloaded files it gets permission denied trying to move the files to the server share.  

Currently I am using samba to share my media folder for sickgear to access.  

My smb.conf on the server is 

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Plex-Files]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]    
server string = %h server (Samba, Ubuntu)    
server role = standalone server    
map to guest = Bad User    
obey pam restrictions = Yes    
pam password change = Yes    
passwd program = /usr/bin/passwd %u    
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .    
unix password sync = Yes    
syslog = 0    
log file = /var/log/samba/log.%m    
max log size = 1000    
dns proxy = No    
usershare allow guests = Yes    
panic action = /usr/share/samba/panic-action %d    
idmap config * : backend = tdb

[homes]    
comment = Home Directories    
read only = No    
create mask = 0644

[printers]    
comment = All Printers    
path = /var/spool/samba    
create mask = 0700    
printable = Yes    
browseable = No

[print$]    
comment = Printer Drivers    
path = /var/lib/samba/printers

[Plex-Files]    
comment = Plex Share    
path = /home/vader699/Plex    
force user = nobody    
force group = users    
group = users    
read only = No    
guest only = Yes    
guest ok = Yes

```

I have tried mounting both my home user directory with username and password and the Plex-Files share with guest.  Neither work.

```

//server-name/username  /mount-point  cifs username=USER,password=PASSWORD,iocharset=utf8,sec=ntlm 0  0
//server-name/Plex-Files /mount-point cifs guest,gid=mediaproviders,rw

```

As a logged in user to the desktop i can move create and delete any and all files in either mounted share.  Any other user like the one that sickgear is running under gets a permission denied error when trying to move or add files to either share.  

I am willing to use a different method beside samba.

Both server and desktop are on a local home network so security isn't the most important thing but would be nice to keep secure, so I learn to do it correctly. 

Also the server is command line only.

---

### Post by wildmanne39 on 2017-02-11
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-02-11
With samba sharing you have to think about two different parts of permissions for access:
1. The users you allow for the share in smb.conf
2. The linux file permissions for the path

Because of the linux file permissions it is not really good idea to share folder inside /home. Also more experienced users have been commenting here that permissions are needed for the full path all the way to the top level. This is why I would keep the path as short as possible.

For example, create a folder /plex. You can decide whether to use linux permissions 777 (allowing RW to others too) and then control users/groups only in smb.conf, or for example 770 and still specify users/groups in smb.conf. Also you can make the owner of that folder to be the user that will most access it (whether your username or sickbeard). You can also activate the group sticky bit to it.
```
sudo chown sickbeard:users /plex
sudo chmod 770 /plex
sudo chmod g+s /plex
```

After that move some media to test and reapply the ownership if needed. Share the folder in samba and check out the access.

If you have more shares to create I would create them again outside of /home.

---

### Post by vader699 on 2017-02-11
So if I'm reading this correctly you're saying that the permissions on the folder would need to be 777 all the way down to /home for samba to be able to write to the folder.  Which makes sense.  

If that's the case, I now have an different issue.  /home is on a separate partition from / and / doesn't have much space on it for all the files I'd need to move.  So I guess I get to repartition and make a new one for /plex.  

Thanks for the reply.

---

### Post by SeijiSensei on 2017-02-11
If the client and server both run Linux or some other *nix flavor, [NFS]("https://help.ubuntu.com/14.04/serverguide/network-file-system.html") is the preferred file-sharing method.  I only use Samba so Windows can see my server directories. All my machines running Linux use NFS.  The server can run both file-sharing protocols simultaneously.

---

