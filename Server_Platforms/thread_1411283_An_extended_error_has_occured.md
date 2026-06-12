---
title: "An extended error has occured"
date: 2010-02-19
forum: Server Platforms
---

### Post by dhillis on 2010-02-19
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
 
followed this tutorial for the most part. USing 9.10 so had to venture out for some of the updates. Have everything mounted and have samba configured (probably not right though)
 
Used a single hard drive and I am trying to share a ntfs partition, /dev/sda4. 
While in windows if I try to map a network drive I try connecting to [\\c40fs\sda4]("file://\\c40fs\sda4") since this is what shows up when I click browse and find the server. I set up a user account on the server as well as on samba. Both are ve (video editing) with the password panthers. This is set up for a classroom. 
 
Please help me figure out what I did wrong this time and get connected. Might be monday before I can get anything updated...

---

### Post by windependence on 2010-02-19
The user must exist on the Windows machine. Also, I don't believe Windows does NFS. 

-Tim

---

### Post by dhillis on 2010-02-20
oh...i thought windows did ntfs...so do I need to redo it with FAT32?  Also, since this is for a school classroom and each kid has his own login.....do I need to add a user account on the server for each person that is going to be logging into it so that the kids windows network account is the same name and password as the server?  That would really become a pain.....or does it only need to be the same account name and every kid can have the same password?

---

### Post by RJARRRPCGP on 2010-02-20
> **dhillis said:**
> oh...i thought windows did ntfs...so do I need to redo it with FAT32?  

You don't need FAT32 unless it's based on Windows 95. (Windows 95, Windows 98 and Windows ME)

---

### Post by RJARRRPCGP on 2010-02-20
> **dhillis said:**
> oh...i thought windows did ntfs...so do I need to redo it with FAT32?  

--

---

### Post by joberly on 2010-02-20
Let's make sure Samba is running properly before we get into users and groups.

Can you post the output of the command 'testparm' and also post the config file /etc/samba/smb.conf ?

Also what is the specific problem? You can see the share, just cannot access it? Does it ask for a username and password?

---

### Post by dhillis on 2010-02-22
Here is the output of testparm.   Yes, the problem is that I can see the server but I cannot connect to it.  It does not get to the point of asking for a username and password.  IS there a way to post the actual file without having to retype smb.conf?
 
load smb config files from /etc/samba/smb.conf
precessing section "[printers]"
precessing section "[print$]"
processing section "[sda4}
Loaded service files OK
Server role: ROLE_STANDING
press enter to see a dump of your service definitions
 
[global]
server string =%h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = yes
pam password change = yes
passwd program = /usr/bin/passwd %u
passwd chat = *enter/snew/s*/spasswrd:* %n\n *Retype/snew/s*/spassword:* %n\n *password/supdated\ssuccessfully* .
unix password sync = yes
syslog = o
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = no
usershare allow guest = yes
panic action = /usr/share/samba/panic-action %d
 
[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = yes
browseable = no
browsable = no
 
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
 
[sda4]
comment = public folder
path = media/store
force user = nobody
force group = no group
read only = no
create mask = 0777
directory mask = 0777
guest ok = yes

---

### Post by dhillis on 2010-02-22
Till I find out how to post the file i'll tell you this. All I changed was under the sections where it says "#The following setting only takes effect if 'domain logons' is set" I changed the line 
; logon drive = J
 
Don't know much about the coding that linux uses but am assuming that the ; makes this line a comment?
on edit:  reread the file.  Noticed this is a comment that changes the default values of the file.
 
Also, at the bottom I added this code.
 
[sda4]
comment = Public Folder
path = media/store
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group

---

### Post by dhillis on 2010-02-22
Here is the smb.conf file 
 
changed extension to .doc to upload. May need to change back to .conf to open.
 
on edit: Did some more research and changed 
force group = no group 
 
to 
 
force group = nogroup
 
and added this line
 
guest ok = yes
 
this also changed what was happening....i now get an error 
 
the specified network name is no longer available

---

### Post by dhillis on 2010-02-23
alright..got the server up and running....I was able to access the partition as well as another teacher here on campus. Now I have added a user for ethompson is both the server and samba but I keep getting an error when trying to connect.
 
Specified network name is no longer available.
 
What do I need to check now?

---

