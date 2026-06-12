---
title: "[SOLVED] apt-proxy: 6.06 servers dload thru proxy from inet"
date: 2007-09-29
forum: Server Platforms
---

### Post by andb on 2007-09-29
I have one 6.06 server set up as an apt-proxy server. All of the desktop clients (edgy, feisty) work fine. 

The other 6.06 servers were hanging when dloading headers. So I had to change /etc/apt/apt.conf, as per [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

Acquire::http::Proxy "false";
change this to
Acquire::Proxy "false";

Problem is this: while the clients of  apt-proxy (the 6.06 servers) are then able to read header files and download the appropriate .deb files, the files are ALWAYS downloaded form internet, even when they are already cached at the apt-proxy server.

The machines are all in my home, with a limited bandwidth connection, so maintaining a full mirror of the repositories is not appropriate, nor do I want each machine to be pulling down updates, as I do lots of testing using virtual machines. 

Anyone know a fix for this behavior, to get the other client 6.06 servers to pull from the apt-proxy server's already cached .debs?

---

### Post by Braino on 2007-09-29
I've experienced the exact same behavior in 6.06. The problem is with the permissions on the files you have already downloaded via apt-proxy (located in /var/cache/apt-proxy). When apt-proxy goes looking to see if it already has a file that is being requested, it doesn't see the package because it doesn't have the permissions. A quick fix is to do a 'chmod -r a+rx /var/cache/apt-proxy' . It seems like apt-proxy isn't trying to read the files as the aptproxy user (which the files belong to). I have since been using Debian unstable, which has the newest version available of apt-proxy, and have not experienced this problem yet. I would recommend trying to download a backport of a more recent version.

---

### Post by andb on 2007-10-01
Thanks for the reply. I tried changing file permissions this way, in order to keep permissions right on dirs and files:

find /var/cache/apt-proxy/ -type d | while read var1; do sudo chmod 755 $var1; done

find /var/cache/apt-proxy/ -type d | while read var1; do sudo chmod 644 $var1; done

when I run 'netstat -ac', I still get outbound connections to the repositories for packages I know are there.

Dapper backport repository doesn't have a newer version so I'll move my other servers to either 7.04server or to debian. I've been planning to restructure a bit, and this is a good excuse.  

Thanks again for the reply.

---

