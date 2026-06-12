---
title: "[SOLVED] vsftpd under /var/run/ disappears after reboot"
date: 2008-11-29
forum: Server Platforms
---

### Post by kracheck on 2008-11-29
Hi there,

I have installed and configured the vsftpd server on ubuntu 8.04.  All is working nicely.  It starts up in standalone mode. I'm using virtual users and I'm able to login and download files.  There is however one thing I don't get at all. Whenever I reboot and start the server and try a :
ftp localhost 10021 (it's not listening on the standard port)
I get an error from the sever saying :
500 OOPS: vsftpd: not found: directory given in 'secure_chroot_dir':/var/run/vsftpd
Whenever I create that empty directory into /var/run everything works again.

So my question is, how come that the empty vsftp directory under /var/run seems to disappear after every reboot of my system ?

Thanks in advance

---

### Post by andguent on 2008-11-29
There are many directories on a standard Linux setup that intentionally reset every reboot. The /tmp directory is one, and apparently you stumbled into another. I wouldn't recommend using /var/run.

The "Linux System Administrator's Guide" helped me out immensely in trying to decode what the original Linux creators intended when they designed the directory structure. Have a look at this link for more info.
[http://tldp.org/LDP/sag/html/var-fs.html](http://tldp.org/LDP/sag/html/var-fs.html)

Most people setup FTP to be jailed into a users' home directory. For security purposes, sometimes its good to create a new user named 'ftp' just for this purpose. I've also seen /var/ftp, /var/www, and /opt/shared/ftp be used depending on your needs.

If you are just using it for internal testing and learning, just use /var/ftp instead of /var/run/vsftpd. It's less typing. :)

---

### Post by kracheck on 2008-11-30
Thanks a lot for your intervention.  A few simple steps solved the problem.

sudo mkdir /var/ftp
sudo nano /etc/vsftpd.conf - change the path in the secure_chroot.dir entry from /var/run/vsftpd to /var/ftp

reboot

fpt localhost 10021 worked without any problem

Thanks a lot

---

### Post by andguent on 2008-11-30
Glad it worked. Thanks for marking the thread solved.

---

