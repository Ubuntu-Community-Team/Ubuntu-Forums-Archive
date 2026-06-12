---
title: "ftp server:1 directory 3 mount points"
date: 2009-04-07
forum: Server Platforms
---

### Post by nejode on 2009-04-07
I have a ftp server with 3 local users chrooted to their home directories, and 1 annonymous directory for public downloads available to anyone (/home/ftp). I already bound (mount --bind) /home/ftp to /home/user1/public-ftp so user1 can upload files to the public directory, but how can I bind the same public directory to all three users so they can upload there too... one directory to 3 mount points? Is it possible?
Thanks beforehand... Nelson

---

### Post by smileypaul on 2009-04-07
Should be an option in the ftp config to follow symlinks

then add a symlink to each of their home directories

ln -s target source  (i believe, might be source target)

---

### Post by nejode on 2009-04-11
smileypaul: tried that but had problems with write permissions.  VSFTPD requires the public ftp directory to be owned by root.  Maybe creating a new group, changing the group of the directory, and adding all users to that group.  I'll try it out and post the results here... thanks!

---

