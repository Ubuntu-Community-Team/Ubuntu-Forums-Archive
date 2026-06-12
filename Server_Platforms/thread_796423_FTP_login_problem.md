---
title: "FTP login problem"
date: 2008-05-16
forum: Server Platforms
---

### Post by mitjab on 2008-05-16
I install ftp server (proftpd) but i can not login in it. It works a long time, but now when i upgrade to 8.04 version stop working. I search in forum but i can not find solution.

This i can see in log:
May 16 18:07:23 server proftpd[6416] mitjab.homelinux.net (cpe2-25-222.cable.triera.net[::ffff:82.149.25.222]): FTP session opened.
May 16 18:07:23 server proftpd[6416] mitjab.homelinux.net (cpe2-25-222.cable.triera.net[::ffff:82.149.25.222]): USER mitjab (Login failed): Invalid shell: '/bin/bash'

What is wrong? user mitjaba nd directory exist.

Thx for help!

---

### Post by geertn on 2008-05-16
Check if /bin/bash is listed in /etc/shells

---

### Post by Donb01 on 2008-05-16
I believe there is something in the ubuntu release notes for 8.04 that says /bin/bash was replaced by /bin/dash, and you need to create a symbolic link for /bin/bash.

Somebody is going to blast me for the syntax here because I suck at symbolic links, but it is something along the lines of:

ln -s /bin/bash /bin/dash   

the order of the two paths may be reversed or I may be missing some parameters.  If you make that link (successfully!) it should work.

---

### Post by mitjab on 2008-05-16
symbolic link already exist

root@server:/home/mitjab# ln -s /bin/bash /bin/dash
ln: creating symbolic link `/bin/dash': File exists


Check if /bin/bash is listed in /etc/shells

i add /bin/bash in /etc/shells and now working.

thx boath for help!

---

