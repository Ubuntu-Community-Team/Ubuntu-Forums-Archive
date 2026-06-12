---
title: "Backup Ubuntu 14.04 and restore question"
date: 2016-05-12
forum: Server Platforms
---

### Post by Wythefan on 2016-05-12
Sorry I'm new to this.....I have a Ubuntu server 14.04 TLS on Rackspace built as a host on VM Ware  I would like to move it to my local server room as a VM Ware host.  Is it possible to back it up the Rackspace server and restore to my local VMware server?

---

### Post by lukeiamyourfather on 2016-05-12
I would call Rackspace support and ask if you can download the virtual disk image for your host. It's technically possible to do but not sure if they support it or not. That would be the most straightforward way of doing it.

---

### Post by darkod on 2016-05-12
Yes, check with their support, but also you have another option.

Depending what exactly you have running on the server, you can use this situation and set up the new 16.04 LTS at home, then just transfer the needed data and configuration setup. That way you will be on the latest LTS too... And you will need to transfer only the minimum amount of data (no OS files).

---

