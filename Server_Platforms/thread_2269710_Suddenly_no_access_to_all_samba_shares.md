---
title: "Suddenly no access to all samba shares"
date: 2015-03-17
forum: Server Platforms
---

### Post by vTali on 2015-03-17
Hello everybody,

I'm writing to you because I'm confused with with my NAS. I bought some new hardware and built my own nas a year ago now. IM running Ubuntu 14.04 LTS Server Edition. The Problem is, that i've no access to my samba shares anymore. Yesterday, everything was fine. Today, i editet some scripts for Minecra and backup-stuff, i did some updates wit sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove and added 3 samba shares (music, games, movies) to my smb.conf. Then I restarted SAMBA and nothing works. For Example: I'm running pyload on it. I downloaded with pyload a youtube video into my /downloads path. This worked and the video is there. In my samba share i have the download path and in force user, there is this pyload user. When I try to connect with my Windows 8.1 machine, it shows me the message "access denied".


This is my smb.conf:
```
[global]workgroup = WORKGROUP
security = user
share modes = yes
wins support = yes
unix extensions = no
#hide files = /desktop.ini/Thumbs.db/
vfs object = recycle
        recycle:repository = .recyclebin
        recycle:directory_mode = 0775
        recycle:keeptree = Yes
        recycle:versions = Yes
        recycle:touch = Yes
        recycle:touch_mtime = Yes
        recycle:maxsize = 0


[homes]
comment = Home Directories
browsable = no
read only = no
create mode = 0750


[Media]
path = /media/wdred1/media
comment = media share
valid users = sysadmin, vitalij, daniel
write list = sysadmin, vitalij, daniel
force user = sysadmin
inherit permissions = true


[Movies]
path = /media/wdred1/movies
comment = movie share
valid users = minidlna, vitalij, daniel
write list = minidlna, vitalij, daniel
force user = minidlna
inherit permissions = true


[Games]
path = /media/wdred1/games
comment = game share
valid users = sysadmin, vitalij, daniel
write list = sysadmin, vitalij, daniel
force user = sysadmin
inherit permissions = true


[Music]
path = /media/wdred1/music
comment = music share
valid users = sysadmin, vitalij, daniel
write list = sysadmin, vitalij, daniel
force user = sysadmin
inherit permissions = true


[Family]
path = /media/wdred1/home
comment = family share
valid users = sysadmin, vitalij, daniel, mama
write list = sysadmin, vitalij, daniel, mama
force user = sysadmin
inherit permissions = true


[Downloads]
path = /media/wdred1/downloads
comment = download share
valid users = pyload, sysadmin, vitalij, daniel
write list = pyload, sysadmin, vitalij, daniel
force user = pyload
inherit permissions = true


[Transfer]
path = /media/wdred1/transfer
comment = transfer share
valid users = sysadmin, vitalij, daniel, roman
write list = sysadmin, vitalij, daniel, roman
force user = sysadmin
inherit permissions = true


[Public]
path = /media/wdred1/public
comment = public share
valid users = sysadmin, vitalij, daniel, roman, gast
write list = sysadmin, vitalij, daniel, roman, gast
force user = sysadmin
inherit permissions = true


[Minecraft]
path = /opt/minecraft
comment = minecraft share
valid users = minecraft, vitalij
write list = minecraft, vitalij
force user = minecraft
inherit permissions = true


;[cloud daniel]
;path = /media/wdred1/owncloud/Daniel
;comment = daniel cloud share
;valid users = www-data, daniel
;write list = www-data, daniel
;force user = www-data
;inherit permissions = true


;[cloud vitalij]
;path = /media/wdred1/owncloud/Vitalij
;comment = vitalij cloud share
;valid users = www-data, vitalij
;write list = www-data, vitalij
;force user = www-data
;inherit permissions = true


;[public]
;path = /media/wdred1/alle
;public = yes
;writable = yes
;comment = smb share
;printable = no
;guest ok = yes
```

I'm really confused what to do, because i need the data from my nas. Everything is there. I still have a 1 week old backup, but it would be more comfortable to access the data via my nas.
Hope someone could help me.

Best wishes,
vTali

---

### Post by vTali on 2015-03-17
I found out, that I can access the [Minecraft] share. I don't know why, but now, I can also access the [Movies] Share. Everything else, is still not accessable

---

### Post by wyliecoyoteuk on 2015-03-17
You might need to resync your unix and samba users

Only common thing I can see is that Minecraft and Movies don't have sysadmin as the default user.

---

### Post by vTali on 2015-03-17
I already reinstalled samba. Therefore I hadn't any user in samba. I readded them with sudo sambapasswd -a username. I can't figure out the problem. I cannot access my home directory via samba. I tried to change the user sysadmin in for example [Public] with minecraft and done chown -R minecraft /pathtoPublicFolder, but it doesn't work. Are the user in Unix corrupt or is there another problem?

---

