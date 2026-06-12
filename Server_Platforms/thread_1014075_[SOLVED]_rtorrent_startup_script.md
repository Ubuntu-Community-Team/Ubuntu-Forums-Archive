---
title: "[SOLVED] rtorrent startup script"
date: 2008-12-17
forum: Server Platforms
---

### Post by cdmike2k8 on 2008-12-17
Hello, I am following the directions to set rtorrent to startup at boot on my torrent server (ubuntu server 8.10).  Using either script on their website [here]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#StartingrTorrentonSystemStartup"), it seems to create the symbolic links in the different run level directories (/ect/rc*.d), but doesn't create the link in /etc/init.d.  ```
michael@fileserv:~$ ls -l /etc/rc?.d | grep rtor
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 K20rtorrent -> ../init.d/rtorrent
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 K20rtorrent -> ../init.d/rtorrent
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 S20rtorrent -> ../init.d/rtorrent
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 S20rtorrent -> ../init.d/rtorrent
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 S20rtorrent -> ../init.d/rtorrent
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 S20rtorrent -> ../init.d/rtorrent
lrwxrwxrwx 1 root root  18 2008-12-16 19:22 K20rtorrent -> ../init.d/rtorrent
michael@fileserv:~$ ls /etc/init.d | grep rtor
michael@fileserv:~$ 

```This shows that it is making the symbolic links in the folders, but that there is no script to start/stop.  There are no error messages when I run the script.  I attached how I configured the script in case I did something wrong in there.  Anyone know what I am doing wrong? Thanks, Michael

---

