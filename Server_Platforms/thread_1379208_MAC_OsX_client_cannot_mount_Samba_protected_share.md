---
title: "MAC OsX client cannot mount Samba protected share"
date: 2010-01-12
forum: Server Platforms
---

### Post by MoRoBoShi on 2010-01-12
Ciao,
I recently set up a Samba server (Ubuntu 8.10 desktop) in a Social Businness Office. 
All the guys in there have different laptops and OS.

Here is how my smb.conf file look in the share section.

[private folder]
path = /path/to/private
comment = private
valid users = user1 user2
directory mask = 0777
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no[FONT=monospace]
[/FONT]encrypt password = yes[FONT=monospace]
[/FONT]smb passwd file = /etc/samba/smbpasswd


It work fine for Win and Ubuntu, but access  this folder with Mac OsX gives this error:

smb_mount: open session failed!: syserr = Broken pipe

It seems that authentication is ok, but for some reason it cannot mount the device.

I know this is not the right place to talk about OsX issues.

I would like to exclude if there are some options I miss in the smb.conf.

Thanks in advance!

---

### Post by MoRoBoShi on 2010-01-15
Ciao!
I found a solution suitable for all clients (win, mac, linux).
I createda link in my home folder on the server:

user@server:~$ ln -s /path/to/private

then I modified /etc/samba/smb.conf this way:

[private folder]
path = /path/to/private
comment = private
valid users = user1 user2
directory mask = 0777
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no[FONT=monospace]
[/FONT]encrypt password = yes[FONT=monospace]
[/FONT]smb passwd file = /etc/samba/smbpasswd

[private folder]
 path = /home/user/private <----this is the symbolic link
 comment = private
 valid users = user1 user2
 directory mask = 0777
 read only = no
 available = yes
 browseable = yes
 writable = yes
 guest ok = no
 public = no
 printable = no
 share modes = no
 locking = no[FONT=monospace]
[/FONT]encrypt password = yes[FONT=monospace]
[/FONT]smb passwd file = /etc/samba/smbpasswd


Now OsX clients are able to mount and browse the samba protected folder.

---

### Post by ICEB3AR on 2010-01-15
So the only thing you've changed is that you put in a link as path-value in the smb.conf instead of the "real" path?

I'm asking because I have to deal with that topic (mac and samba) within the next weeks.

---

### Post by cmadooly on 2010-01-15
> **MoRoBoShi said:**
> Ciao!
I found a solution suitable for all clients (win, mac, linux).
I createda link in my home folder on the server:
 
user@server:~$ ln -s /path/to/private
 
then I modified /etc/samba/smb.conf this way:
 
[private folder]
path = /path/to/private
comment = private
valid users = user1 user2
directory mask = 0777
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
encrypt password = yes
smb passwd file = /etc/samba/smbpasswd
 
[private folder]
path = /home/user/private <----this is the symbolic link
comment = private
valid users = user1 user2
directory mask = 0777
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
encrypt password = yes
smb passwd file = /etc/samba/smbpasswd
 
 
Now OsX clients are able to mount and browse the samba protected folder.
 
I'll give this a shot. I set up a samba server for windows users but I may leave the option open if someone starts using a mac.

---

### Post by MoRoBoShi on 2010-01-18
Hi ICEB3AR,
yes, the only thing I've done is to point the shared folder to a symlink.


[]("http://ubuntuforums.org/member.php?u=994999")

---

