---
title: "Ubuntu 12.04 rsync + webdav"
date: 2012-06-08
forum: Server Platforms
---

### Post by tkkaisla on 2012-06-08
I wanna back up my drive to my webdav-clouddrive using rsync. I am already edited davfs2.conf file section [COLOR=#000000][FONT=verdana]use_locks to 0 and using http instead of https. All folders are set up chmod 777 for testing reasons but no help. Webdav-clouddrive is mounted /media/nebula. I get following error.
[/FONT][/COLOR]```

hallinta@SSV-uServer:~$ sudo rsync -r --progress --delete /media/verkkolevy /media/nebula/verkkolevy
[sudo] password for hallinta: 
sending incremental file list
verkkolevy/jännää/tadaa.txt
           0 100%    0.00kB/s    0:00:00 (xfer#1, to-check=0/4)
rsync: mkstemp "/media/nebula/verkkolevy/verkkolevy/jännää/.tadaa.txt.Iy26YW" failed: Resource temporarily unavailable (11)

sent 169 bytes  received 34 bytes  1.96 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

```
Sorry my bad english skills.:oops:

Hope someone can help.

---

