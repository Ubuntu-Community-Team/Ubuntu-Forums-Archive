---
title: "Installation GTA IV"
date: 2010-05-17
forum: Wine
---

### Post by H0lyGanGs7eR on 2010-05-17
Hello, i saw in PlayOnLinux that I can run GTA IV under Linux, but I have some problems, I ran PlayOnLinux and it wanted the installation files to be mounted as CD drive. So I tried with this command:
```
niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ sudo mount -o loop -t iso9660 GTA\ IV\ DVD\ 1.iso /data/mountcdrom/
[sudo] password for niki: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ dmesg | tail
[33610.027532] wlan0: direct probe to AP 90:e6:ba:5f:10:87 (try 1)
[33610.031323] wlan0: direct probe responded
[33610.031331] wlan0: authenticate with AP 90:e6:ba:5f:10:87 (try 1)
[33610.033459] wlan0: authenticated
[33610.033495] wlan0: associate with AP 90:e6:ba:5f:10:87 (try 1)
[33610.035767] wlan0: RX AssocResp from 90:e6:ba:5f:10:87 (capab=0x411 status=0 aid=2)
[33610.035788] wlan0: associated
[33610.051300] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33620.742528] wlan0: no IPv6 routers present
[36205.084401] ISOFS: Unable to identify CD-ROM format.
niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ 

```

Please help, i LOVE this game. My /data/ partition is NTFS, if this can be a problem. Waiting for your answers. :)

---

### Post by hikaricore on 2010-05-17
> **H0lyGanGs7eR said:**
> Hello, i saw in PlayOnLinux that I can run GTA IV under Linux, but I have some problems, I ran PlayOnLinux and it wanted the installation files to be mounted as CD drive. So I tried with this command:
```
niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ sudo mount -o loop -t iso9660 GTA\ IV\ DVD\ 1.iso /data/mountcdrom/
[sudo] password for niki: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ dmesg | tail
[33610.027532] wlan0: direct probe to AP 90:e6:ba:5f:10:87 (try 1)
[33610.031323] wlan0: direct probe responded
[33610.031331] wlan0: authenticate with AP 90:e6:ba:5f:10:87 (try 1)
[33610.033459] wlan0: authenticated
[33610.033495] wlan0: associate with AP 90:e6:ba:5f:10:87 (try 1)
[33610.035767] wlan0: RX AssocResp from 90:e6:ba:5f:10:87 (capab=0x411 status=0 aid=2)
[33610.035788] wlan0: associated
[33610.051300] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33620.742528] wlan0: no IPv6 routers present
[36205.084401] ISOFS: Unable to identify CD-ROM format.
niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ 

```

Please help, i LOVE this game. My /data/ partition is NTFS, if this can be a problem. Waiting for your answers. :)



Unless something has changed [GTA4 barely runs under wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8757") if you're lucky.
The frontend (POL) would had to have done something miraculous very recently.. you are probably mistaken.

It should be also mentioned that we don't support piracy on these forums and this thread will be closed.

---

### Post by jpeddicord on 2010-05-17
> **hikaricore said:**
> It should be also mentioned that we don't support piracy on these forums and this thread will be closed.

Indeed. Please take this elsewhere.

---

