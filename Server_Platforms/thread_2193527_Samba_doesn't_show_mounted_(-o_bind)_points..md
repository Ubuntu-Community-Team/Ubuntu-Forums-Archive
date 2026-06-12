---
title: "Samba doesn't show mounted (-o bind) points."
date: 2013-12-13
forum: Server Platforms
---

### Post by veranyon on 2013-12-13
Have:
Ubuntu Server 12.04 (x86_64) with last updates.

/etc/fstab:
```
..
/mnt/media1/iron/1/images       /home/iron/1/zones/zalman/images
..
```
ls /home/iron/1/zones/zalman/images/
```
wallpapers_ru_020811_bonez_diary_of_dreams.jpg
wallpapers_ru_021103_luana_hallway_of_ghosts.jpg
wallpapers_ru_021126_quiet_autumn_morning.jpg
wallpapers_ru_040202_hemp_umka_odin.jpg
```

smb.conf:```
[global]
netbios name = main-server
server string =
workgroup = WORKGROUP
socket options=SO_RCVBUF=131072 SO_SNDBUF=131072 TCP_NODELAY
min receivefile size = 16384
use sendfile = true
aio read size = 16384
aio write size = 16384
passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
wins support = no
printing = CUPS
printcap name = CUPS
log file = /var/log/samba/log.%m
syslog = 0
syslog only = no
unix extensions = no


[media]
path = /mnt/media1/iron/1
browseable = yes
read only = no
guest ok = no
create mask = 0655
directory mask = 0755
force user = iron
veto files = /._*/.DS_Store/.TemporaryItems/.apdisk/Thumbs.db/desktop.ini/.AppleDouble/.AppleDB/.AppleDesktop/.DocumentRevisions*/.Spotlight*/.Trashes/.com.apple.*
delete veto files = yes
```

My changes on client side:
ls /Volumes/media/images/
```
wallpapers_ru_020811_bonez_diary_of_dreams.jpg
wallpapers_ru_021103_luana_hallway_of_ghosts.jpg
wallpapers_ru_021126_quiet_autumn_morning.jpg
wallpapers_ru_040202_hemp_umka_odin.jpg
```

!!!!>
mac:~ iron$ ls /Volumes/media/zones/zalman/images/
mac:~ iron$
nothing!

why???

---

### Post by veranyon on 2013-12-13
I can mount not "[COLOR=#000000][FONT=Ubuntu Mono]/mnt/media1/iron/1/images" and /home/iron/1/images. Result = 0.[/FONT][/COLOR]

---

