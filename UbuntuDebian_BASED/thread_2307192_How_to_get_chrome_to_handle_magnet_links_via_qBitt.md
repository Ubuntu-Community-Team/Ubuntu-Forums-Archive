---
title: "How to get chrome to handle magnet links via qBittorrent"
date: 2015-12-22
forum: Ubuntu/Debian BASED
---

### Post by parker-hugh on 2015-12-22
I recently installed zorin 9 lite and when I use chrome browser and click magnet link, it doesn't offer any way to launch qBittorrent

I saw a slolution here...
[http://askubuntu.com/questions/311537/torrent-magnet-links-open-new-window-but-not-transmission](http://askubuntu.com/questions/311537/torrent-magnet-links-open-new-window-but-not-transmission)
The question owner accepted this as the best answer....
check defaults with:
```
xdg-mime query default x-scheme-handler/magnet
gvfs-mime --query x-scheme-handler/magnet
```
and set them with
```
xdg-mime default qBittorent.desktop x-scheme-handler/magnet
gvfs-mime --set x-scheme-handler/magnet qBittorrent.desktop
```
Assuming you have a qBittorrent.desktop file at /usr/share/applications/
.......................................................................................................
I checked and I have a qBittorrent.desktop file at /usr/share/applications/

Although I am not experienced in Linux, I followed the steps above and it didn't help.  I'm not sure if script done any harm to my system but here is the output of my steps....

```
kodi@SONY-VAIO-ZORIN:~$ xdg-mime query default x-scheme-handler/magnet
```
no default was returned from this code

```
kodi@SONY-VAIO-ZORIN:~$ gvfs-mime --query x-scheme-handler/magnet
The program 'gvfs-mime' is currently not installed. You can install it by typing:
sudo apt-get install gvfs-bin
kodi@SONY-VAIO-ZORIN:~$ 
```
I had to install program 'gvfs-mime'
```
kodi@SONY-VAIO-ZORIN:~$ sudo apt-get install gvfs-bin
[sudo] password for kodi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cifs-utils localechooser-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
Suggested packages:
  gvfs-backends-goa
The following NEW packages will be installed
  gvfs-bin
The following packages will be upgraded:
  gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
6 to upgrade, 1 to newly install, 0 to remove and 427 not to upgrade.
Need to get 50.0 kB/670 kB of archives.
After this operation, 477 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-bin i386 1.20.3-0ubuntu1.2 [50.0 kB]
Fetched 50.0 kB in 0s (331 kB/s)  
(Reading database ... 158933 files and directories currently installed.)
Preparing to unpack .../gvfs-backends_1.20.3-0ubuntu1.2_i386.deb ...
Unpacking gvfs-backends (1.20.3-0ubuntu1.2) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-fuse_1.20.3-0ubuntu1.2_i386.deb ...
Unpacking gvfs-fuse (1.20.3-0ubuntu1.2) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs_1.20.3-0ubuntu1.2_i386.deb ...
Unpacking gvfs:i386 (1.20.3-0ubuntu1.2) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-daemons_1.20.3-0ubuntu1.2_i386.deb ...
Unpacking gvfs-daemons (1.20.3-0ubuntu1.2) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-libs_1.20.3-0ubuntu1.2_i386.deb ...
Unpacking gvfs-libs:i386 (1.20.3-0ubuntu1.2) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-common_1.20.3-0ubuntu1.2_all.deb ...
Unpacking gvfs-common (1.20.3-0ubuntu1.2) over (1.20.1-1ubuntu1) ...
Selecting previously unselected package gvfs-bin.
Preparing to unpack .../gvfs-bin_1.20.3-0ubuntu1.2_i386.deb ...
Unpacking gvfs-bin (1.20.3-0ubuntu1.2) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up gvfs-common (1.20.3-0ubuntu1.2) ...
Setting up gvfs-libs:i386 (1.20.3-0ubuntu1.2) ...
Setting up gvfs-daemons (1.20.3-0ubuntu1.2) ...
Setting up gvfs:i386 (1.20.3-0ubuntu1.2) ...
Setting up gvfs-backends (1.20.3-0ubuntu1.2) ...
Setting up gvfs-fuse (1.20.3-0ubuntu1.2) ...
Setting up gvfs-bin (1.20.3-0ubuntu1.2) ...
kodi@SONY-VAIO-ZORIN:~$
``` 

```
kodi@SONY-VAIO-ZORIN:~$ gvfs-mime --query x-scheme-handler/magnet
Default application for 'x-scheme-handler/magnet': qBittorrent.desktop
Registered applications:
    qBittorrent.desktop
Recommended applications:
    qBittorrent.desktop
kodi@SONY-VAIO-ZORIN:~$
``` 
So it looks like this has returned the correct value as it shows qBittorrent.desktop as the Recommended application, is this correct? so I don't need to  run the second update? I'm not sure to be honest.
so run the first update...
```
kodi@SONY-VAIO-ZORIN:~$ xdg-mime default qBittorent.desktop x-scheme-handler/magnet
```
check result of first update....
```
kodi@SONY-VAIO-ZORIN:~$ xdg-mime query default x-scheme-handler/magnet
qBittorent.desktop
kodi@SONY-VAIO-ZORIN:~$ 
```
looks like this code worked as qBittorent.desktop is shown in output?

But after all this, chrome still does not recognise magnet links, does anyone know what is wrong and is there anything I have done that could harm my system?

Any help would be appreciated.How to get chrome to handle magnet links via qBittorrent
EDIT: here is the output of my qBittorrent.desktop

```
 kodi@SONY-VAIO-ZORIN:~$ cd /usr/share/applications/
kodi@SONY-VAIO-ZORIN:/usr/share/applications$ cat qBittorrent.desktop
[Desktop Entry]
Categories=Network;FileTransfer;P2P;Qt;
Exec=qbittorrent %U
GenericName=BitTorrent client
Comment=Download and share files over BitTorrent
Icon=qbittorrent
MimeType=application/x-bittorrent;x-scheme-handler/magnet;
Name=qBittorrent
Terminal=false
Type=Application
StartupNotify=false
StartupWMClass=qbittorrent 
```

---

### Post by Vladlenin5000 on 2015-12-22
What you did looks fine and should work with Firefox. Have you tested it already?
Chrome has no "Open with..." option. That alone should be enough to understand why it can't work as you wish.

---

### Post by coffeecat on 2015-12-23
Zorin - *Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by parker-hugh on 2015-12-23
> **Vladlenin5000 said:**
> What you did looks fine and should work with Firefox. Have you tested it already?
Chrome has no "Open with..." option. That alone should be enough to understand why it can't work as you wish.

I have tested it with Firefox and it works. The laptop belongs to my nephew and he prefers Chrome browser but if it's too difficult to get setup then I will just tell him to use Firefox if he is looking for torrent files to download, it's not a big problem to do that.

Thanks for feeback. At least I haven't broken the system.

---

