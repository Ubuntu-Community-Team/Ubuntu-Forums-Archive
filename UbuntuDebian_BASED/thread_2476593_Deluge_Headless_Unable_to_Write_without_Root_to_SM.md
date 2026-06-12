---
title: "Deluge Headless Unable to Write without Root to SMB Mounted Share on NAS"
date: 2022-06-30
forum: Ubuntu/Debian BASED
---

### Post by willdab345t on 2022-06-30
Hi all, I've trawled through countless threads and changed my fstab options hundreds of times now to try to resolve this issue, hopefully it's something simple to resolve. My RP4 SD card died so I set it up again using USB boot yesterday. It's running Raspbian and primarily used as a PIHole. I decided to put a headless Deluge client on it and followed a guide to set it up (this guide: [https://pimylifeup.com/raspberry-pi-deluge/](https://pimylifeup.com/raspberry-pi-deluge/)). I created a directory in /mnt/ and gave my user 'pi', group 'pi' 777 access and chowned it then mounted the SMB NAS share. I am not a very good Linux user as mainly used Windows my whole life but googled my way through all this as I've done a few times before with other Ubuntu installations I've played with.

Everything seemed to go well except when I got to adding a torrent to Deluge through the headless client, it is stuck at downloading at '0%', I've come to learn this means it doesn't have some permission it needs, write most likely on the mount, however everything seems correct as far as I know.

When I run Deluge non headless and elevate with sudo it can and does download as normal, just not when using the headless client. The two services from the headless guide are set up as 'pi', which is my RP account and also permissions are set for pi for RW on the SMB NAS share. It seems to be this is a problem with the mount, as everything else seems fine. Further from this, when I load a torrent that has already downloaded some data via headless, it does recognise the data and checks it before starting the download, which then never connects to peers as as above, assuming it doesn't have write access. I can also navigate to the mount and add a new folder without problem.

I also tried an NFS share which had the same problem.

I have tried a bunch of fstab mount options from googling, I'm sure there's something there that needs to be changed.
NAS share is using SMB3 by the looks of it (there is an SMB 3 encryption option) and is a ReadyNas 6 unit from Netgear, their site states it's SMB3 also.

Currently fstab looks like this: //192.168.1.49/Videos /mnt/nas/videos cifs username=*redacted*,password=*redacted*,workgroup=WORKGROUP,noperm,rw,uid=pi,gid=pi,forceuid,forcegid,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0

Mount permissions are currently: pi@pi:/mnt/nas $ ls -ltotal 0
drwxr-xr-x 2 pi pi 0 Jun 30 11:04 videos

Would appreciate some help, feel I'm very close to get this working but have insufficient knowledge of Linux file system permissions and mounting, etc.

Cheers,
Will

---

### Post by ActionParsnip on 2022-06-30
What username does the deluge process run as?

---

### Post by willdab345t on 2022-06-30
it runs using 'pi' same as my RP username, same as the account on the NAS. There are two services, as listed in guide I linked and followed, one for the Deluged daemon and one for the web service, details below (I changed the UMASK parameter to 000 during testing on both the below configs):

[COLOR=#B9B9B8][FONT=SFMono-Regular]sudo nano /etc/systemd/system/deluged.service

[/FONT][/COLOR][COLOR=#B9B9B8][FONT=SFMono-Regular][Unit]Description=Deluge DaemonAfter=network-online.target[Service]Type=simpleUser=piGroup=piUMask=007ExecStart=/usr/bin/deluged -dRestart=on-failureTimeoutStopSec=300[Install]WantedBy=multi-user.target

[/FONT][/COLOR][COLOR=#B9B9B8][FONT=SFMono-Regular]sudo nano /etc/systemd/system/deluge-web.service

[/FONT][/COLOR][COLOR=#B9B9B8][FONT=SFMono-Regular][Unit]Description=Deluge Web InterfaceAfter=network-online.target deluged.serviceWants=deluged.service[Service]Type=simpleUser=piGroup=piUMask=027ExecStart=/usr/bin/deluge-web -dRestart=on-failure[Install]WantedBy=multi-user.target[/FONT][/COLOR]

---

### Post by ActionParsnip on 2022-06-30
Can you please give the output of:
```

ps -ef | grep -i deluge | grep -v grep

```
Thanks

---

### Post by willdab345t on 2022-06-30
pi@pi:~ $ ps -ef | grep -i deluge | grep -v grep
pi           404       1  2 17:27 ?        00:00:05 deluge-web
pi           601       1 10 17:27 ?        00:00:18 /usr/bin/python3 /usr/bin/deluged -d

---

### Post by coffeecat on 2022-06-30
Raspbian, not Ubuntu.

*Thread moved to Debian based sub-forum.*

---

### Post by willdab345t on 2022-07-01
*bump*

---

### Post by willdab345t on 2022-07-01
After some more testing it seems deluge headless cannot write to anywhere, not just a share, if I run Deluge as a standalone client it's fine as either sudo or 'pi' to any location.

---

