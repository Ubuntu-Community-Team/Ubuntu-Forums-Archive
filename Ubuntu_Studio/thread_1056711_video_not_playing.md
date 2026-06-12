---
title: "video not playing"
date: 2009-02-01
forum: Ubuntu Studio
---

### Post by albanian_kernel on 2009-02-01
hello to everyone,i've some probs with ubuntu 8.04 LTS,when i went to youtube all the videos will not play,same for the streaming and all the videos on the web...i've installed everything that's needed to play the videos but the problem persist!can someone help me? plz:(

---

### Post by albanian_kernel on 2009-02-01
--08:50:43--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.30.70
Connecting to fpdownload.macromedia.com|88.221.30.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:50:44 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
 maybe this one can affect me?

---

### Post by albanian_kernel on 2009-02-01
root@fation-hacker:~# wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
--09:57:19--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
           => `install_flash_player_10_linux.tar.gz.3'
Resolving fpdownload.macromedia.com... 88.221.30.70
Connecting to fpdownload.macromedia.com|88.221.30.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3.962.157 (3.8M) [application/x-gzip]

100%[====================================>] 3.962.157    224.53K/s    ETA 00:00

09:57:34 (266.16 KB/s) - `install_flash_player_10_linux.tar.gz.3' saved [3962157/3962157]

root@fation-hacker:~# tar zxf install_flash_player_10_linux.tar.gz
root@fation-hacker:~# sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
root@fation-hacker:~# rm -rf ~/install_flash_player_10_linux/
root@fation-hacker:~# sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/


not working yet  :(  what's wrong???

---

### Post by TenPlus1 on 2009-02-01
Go here: [http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

Select .deb for Ubuntu 8.04+ from the drop-down selection

Download and install .deb for latest working Flash 10 plugin...

---

