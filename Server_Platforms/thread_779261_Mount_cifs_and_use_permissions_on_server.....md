---
title: "Mount cifs and use permissions on server...."
date: 2008-05-02
forum: Server Platforms
---

### Post by natrixgli on 2008-05-02
Hello,

Here is the deal: I have an SSH server that employees are allowed to connect to, and would like to make a windows share on another server available.

Server 1: Ubuntu 7.10 server, AD domain member, ACL support.

Server 2: Win2K3 server, AD domain controller

I can mount \\server2\share on /media/whatever using mount.cifs, however I want ALL users to be able to access the share when logged into server 1 via ssh.

It works, assuming I mount the share as a domain admin, the problem is that when they browse to the share at /media/whatever the Windows ACL's are totally ignored allowing any user to have a field day and view everyone's files. Essentially they are connected as whatever domain admin mounted the share!

I do not want to have to create a separate mount point for each user. There has got to be a way to mount a windows share and have windows ACL respected by the Linux box....

This is only a temp. solution whilst we migrate data off the Windows box over to the Samba one.

Any help would be appreciated!


Cheerio,

-n8

---

