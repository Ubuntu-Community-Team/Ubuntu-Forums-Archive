---
title: "vsftpd upload file/folder permissions"
date: 2011-06-20
forum: Server Platforms
---

### Post by cvandal on 2011-06-20
Hello,

Can someone tell me if it is possible to configure vsftpd so that when I upload a file, it's permission is set to 644 and when I upload a folder, it's permission is set to 755?

At the moment, when I upload a file, it's permission is 600 and when I upload a folder, it's permission is set to 700.

---

### Post by cvandal on 2011-06-21
I worked it out :)

Uncomment #local_umask=022

I still don't fully understand how this fixed it, but it did none the less.

---

### Post by falko on 2011-06-21
Here's a umask explanation: [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

### Post by windwardquay on 2011-07-26
It doesn't work for me and now I am getting cross with it!

I have vsftpd installed on a 10.04 server and whatever I upload as a user ends up as files 0600 whereas I want files 0644.

In vsftpd.conf have uncommented local_umask=022 in /etc/vsftpd.conf and done "restart vsftpd" but still the same.

So either it isn't reading that or it is being overridden somewhere. Or perhaps restarting vsftpd is no enough?

I have looked at at /etc/profile and that has umask 022 but ~/.bashrc did not have anything so I added unmask 022. Now I get files folders 0755 rwxr-xr-x and files 0644 rw-r--r--.

So where should I leave this. There is clearly a server default of 066 which overrides vsftpd.conf but which is overidden by bashrc.

---

