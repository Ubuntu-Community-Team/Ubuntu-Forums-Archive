---
title: "Automatic backup to FTP"
date: 2011-08-10
forum: Server Platforms
---

### Post by imhotep531 on 2011-08-10
I'm running 10.04.2 LTS and would like to install a program that does the following:

1. Automatically backs up the contents of a RAID 1 array to an FTP directory.

2. Does a comparison so only the new or changed files are backed up rather than copying every file every time.

3. Allows me to define a backup schedule (i.e. once a week or day)

Does anything like this exist for Ubuntu?

---

### Post by a2j on 2011-08-10
I use rsync to do just that. that is the best way to back up linux and mac boxes.

---

### Post by ruffEdgz on 2011-08-10
> **a2j said:**
> I use rsync to do just that. that is the best way to back up linux and mac boxes.

To add to this comment, this tutorial might be helpful to you with what you are trying to accomplish:

[http://ubuntuforums.org/showthread.php?t=1447506](http://ubuntuforums.org/showthread.php?t=1447506)

---

### Post by HermanAB on 2011-08-10
Howdy,

Use one of these:
rsync, unison, wput

---

### Post by jakupl on 2011-08-10
If you are doing it outside LAN, than FTP is a bad idea. FTP was not designed with security in mind, so all traffic remains unencrypted during transport.
In that case, I would (and do) use rsync over ssh. I followed this relatively simple tutorial and It worked perfectly.
[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

Sorry if that doesn't answer your question.
If it has to be FTP outside LAN, you should use one of these. [http://en.wikipedia.org/wiki/File_Transfer_Protocol#Secure_FTP](http://en.wikipedia.org/wiki/File_Transfer_Protocol#Secure_FTP)

There are excellent programs that to backups, but I've always done it by hand, so I can't help you there..

---

