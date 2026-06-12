---
title: "Command line tool to create .torrent files"
date: 2008-09-13
forum: Server Platforms
---

### Post by captbaritone on 2008-09-13
I am currently running rtorrent on my ubuntu headless server. I would like to create a torrent, which rtorrent cannot do itself. I have found many references to command line tools that can create them, but I cannot find references to any packages that contain these tools. Can someone tell me which ubuntu package to install to get maketorrent or mktorrent or any command line tool to create a torrent?

---

### Post by atoc on 2008-09-13
> **captbaritone said:**
> I am currently running rtorrent on my ubuntu headless server. I would like to create a torrent, which rtorrent cannot do itself. I have found many references to command line tools that can create them, but I cannot find references to any packages that contain these tools. Can someone tell me which ubuntu package to install to get maketorrent or mktorrent or any command line tool to create a torrent?
Why the necessity of having the programs in a deb?
If they're available in an archive (tar.gz etc), just download unarchive and run them from where ever you put the programs

---

### Post by the real bmaker on 2010-08-13
I have just finished a stand-alone command line / shell tool for creating torrents using Linux or Windows.

Download, usage examples and more can be found on its homepage:
[http://wiki.robertnitsch.de/doku.php?id=en:coding:py3createtorrent](http://wiki.robertnitsch.de/doku.php?id=en:coding:py3createtorrent)

Please note it requires Python 3.1! (May work with Python 3.x other than 3.1, too.)

---

### Post by majedaly on 2011-11-11
you can use ctorrent it is in the repos
usage
ctorrent -D 50 -U 10 torrent_file.torrent
which means download file.torrent setting the download speed limit to 50k/s and max upload 10k
to send it to the background (comes handy when you are connecting to a remote system with ssh and want to close the connection) just press 0 then 8
To check the progress at any time, log on to the remote system and  run
ctorrent -c  torrent_file.torrent

---

