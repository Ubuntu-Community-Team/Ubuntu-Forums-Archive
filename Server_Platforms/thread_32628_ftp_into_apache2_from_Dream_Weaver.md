---
title: "ftp into apache2 from Dream Weaver"
date: 2005-05-08
forum: Server Platforms
---

### Post by baza41 on 2005-05-08
I'm trying to set up Dream Weaver on my iMac so I can save pages direct to my Hoary server. I can attach as a normal user, but this won't let me write to /var/www/. I need to be able to ftp in as root but I don't seem able.

Any advice would be helpful.

Baza

---

### Post by JonahRowley on 2005-05-08
You're going to have to run an ftpd.  There are a number of them, but I haven't used any in a long while.  If I were you, I'd figure out how to hook dreamweaver up to sftp, which runs from sshd and is a lot safer.

Or you can go the command-line route.  I use rsync over ssh, edit the files client-side and rsync them up.  It's not that hard to set something like that up, and I'm sure OSX has an rsync client.

---

### Post by LordHunter317 on 2005-05-08
FTPing as root is a retarded idea.

So would be breaking a chroot FTP so you access /var/www even if you changed it's ownership.

---

### Post by saltydog on 2005-05-10
I usually log into my www Hoary server with Dreamweaver thru an sftp connection. On the server is running the ssh daemon, and Dreamweaver allows you to connect to a secure ftp server (sftp).

---

