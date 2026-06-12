---
title: "Minidlna"
date: 2013-11-13
forum: Server Platforms
---

### Post by addison.gott on 2013-11-13
I'm new to Ubuntu server and I have ran into a problem with minidlna. When i go to edit the /etc/minidlna.conf I specify which directories to share, but when I do sudo service minidlna restart i get error messages that my media directories can not be accessed. I have tried changing the locations and used nauticulus (Not sure how you spell it) to change permissions, but nothing seems to work. Can anyone offer any help on how to get them to work?

Error messgage: 
root@mediaserver:~# sudo service minidlna restart
 * Restarting DLNA/UPnP-AV media server minidlna                                parsing error file /etc/minidlna.conf line 71 : good with NetworkManager
[2013/11/13 02:29:14] minidlna.c:478: error: Media directory "A,/home/public/Music" not accessible [No such file or directory]
[2013/11/13 02:29:14] minidlna.c:478: error: Media directory "P,/home/public/Pictures" not accessible [No such file or directory]
[2013/11/13 02:29:14] minidlna.c:478: error: Media directory "V,/home/public/Videos" not accessible [No such file or directory]
                                                                         [ OK ]
When I use the exact location they are at I get this:
root@mediaserver:~# sudo service minidlna restart
 * Restarting DLNA/UPnP-AV media server minidlna                                [2013/11/13 02:32:48] minidlna.c:478: error: Media directory "A,/home/americannuke/Music" not accessible [Permission denied]
[2013/11/13 02:32:48] minidlna.c:478: error: Media directory "P,/home/americannuke/Pictures" not accessible [Permission denied]
[2013/11/13 02:32:48] minidlna.c:478: error: Media directory "V,/home/americannuke/Videos" not accessible [Permission denied]
                                                                         [ OK ]

---

