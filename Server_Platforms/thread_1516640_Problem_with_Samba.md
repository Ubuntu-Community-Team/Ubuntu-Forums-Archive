---
title: "Problem with Samba"
date: 2010-06-24
forum: Server Platforms
---

### Post by SamAdam on 2010-06-24
Currently I am running Ubuntu Server edition 10.04.  My problem is that I cannot connect to my Samba share with my windows computer.  I've been following the guide ([This guide]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html#post297919")) and as of right now my config file looks like this:

[global]
netbios name = NAS
server string = NAS Server
workgroup = WORKGROUP
security = user
encrypt passwords = yes
smb passwd file = /var/lib/samba/passdb
log file = /var/log/samba/%m.log
max log size = 1000
syslog = 0
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
wins support = yes
hostname lookups = yes
hosts equiv = /etc/hosts
hosts allow = 192.168.0.0/255.255.255.0 localhost
hosts deny = All
interfaces = lo eth0
bind interfaces only = yes
guest ok = yes
browse list = yes

[public]
path = /media/Disk1
comment = Shared Folders
guest ok = yes
create mode = 0766
browseable = yes
public = yes
read only = no

I have tried several variations of this configuration, and been searching on what my problem may be for near 2 days now with no luck.  My ultimate goal is to have my shares accesable by multiple users from different computers but only grant them read only access, and the admin will obviously have r/w permissions.  But for now, it would be a nice start to just be able to access the files.

If i type in //NAS into my address bar it prompts me for a user name and password.  But then it leads me to an empty folder, not showing the other directories within the shared directory.  At one point a while back i had it actually showing the folder, but it was saying i didn't have access to those folders, so i'm pretty sure its not a connection problem.

Any help is greatly appreciated, if you need logs or something to help diagnose my problem ill be happy to post them.

---

### Post by kenada on 2010-06-24
what permissions do you have on the folders?

---

### Post by SamAdam on 2010-06-24
Its set to owner: root, group: root and everything enabled (everyone has R/W/X).  I was trying to change the permissions on the directory level at one point, is this my problem?

---

