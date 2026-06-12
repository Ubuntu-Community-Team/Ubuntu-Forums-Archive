---
title: "chroot service start at boot"
date: 2011-12-22
forum: Server Platforms
---

### Post by bogyit on 2011-12-22
Hello :)
I've installed a chroot system with deboostrap as explained here:

- [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

works perfectly and I've installed Nginx and MySQL inside this chroot (/srv/test_server/).

Now, I'm wondering if is possible, and how, to start nginx and mysql automatically when I start or restart my server. I tried to place a symbolic link of /srv/test_server/etc/init.d/nginx to /etc/init.d/ but doesn't seems to work. Is this a good practice? Because right now I'm starting these services manually. Any suggestions or documentation I can read? I've been searching for an answer but I didn't find anything.

Thank you for your attention.

---

### Post by bogyit on 2011-12-25
Solved! At the end it was simple. Here's my solution for ubuntu 11.10 server, in this example I'm using vsftpd:

1. install schroot
2. create a startup script in /etc/init.d/
3. use update-rc.d

```
sudo apt-get install schroot
sudo touch /etc/init.d/my_ftp.sh
sudo nano /etc/init.d/my_ftp.sh
```
inside my_ftp.sh I wrote:
```
#!/bin/bash
schroot -c my_server vsftpd &
```
where **my_server** is just the entry label for /etc/schroot.conf, after editing that file you can list all chroots with **schroot -l**
Anyway, at this point create launch scripts:
```
sudo update-rc.d my_ftp.sh defaults 99
```
You will see an output related to init scripts creation. After that just reboot to test the server.

**Reference:**

- [http://manpages.ubuntu.com/manpages/oneiric/man1/schroot.1.html](http://manpages.ubuntu.com/manpages/oneiric/man1/schroot.1.html)
- [http://www.cyberciti.biz/tips/linux-how-to-run-a-command-when-boots-up.html](http://www.cyberciti.biz/tips/linux-how-to-run-a-command-when-boots-up.html)

hope is useful and, please, advice if this is bad practice, bye :D

---

