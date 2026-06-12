---
title: "1024 file descriptor limit"
date: 2011-05-04
forum: Server Platforms
---

### Post by pablop on 2011-05-04
Hi,

I'm running nginx for static files and as a proxy server for a comet IM server on ubuntu Jaunty.
On high load I'm hitting a limit of 1024 file descriptors.
I've tried increasing this limit but still can't pass 1024.

Does "more /proc/sys/fs/file-nr" gives me the global count of used file descriptors?

Why do I see a maximum of 1024 open file descriptors in /proc/sys/fs/file-nr if this is the global count for the machine and each user should have at least 1024 allowed file descriptors by default?

Is there a way to increase the limit while the server is running? 

Thanks.

Some relevant info on my server:

sudo more /proc/sys/fs/file-nr
1024	0	38001


sudo sysctl fs.file-max
fs.file-max = 38001

sudo nano /etc/security/limits.conf
...
*           hard    nofile          30000
*           soft    nofile          30000

I also added this to /usr/local/nginx/conf/nginx.conf:
worker_rlimit_nofile 10240;

Uncommented the following line in /etc/pam.d/su:
session    required   pam_limits.so

---

