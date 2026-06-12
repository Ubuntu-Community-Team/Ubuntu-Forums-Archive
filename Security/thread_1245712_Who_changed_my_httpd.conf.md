---
title: "Who changed my httpd.conf??"
date: 2009-08-20
forum: Security
---

### Post by neilengineer on 2009-08-20
My test Ubuntu server is running in a LAN.
One day, I noticed the httpd.conf is modified. Some odd lines were added, something like:

[root@localhost bin]# vi /etc/httpd/conf/httpd.conf 
<device DEVNO="0x0801" TIME="1249271650" UUID="ACC1-31E1" TYPE="vfat">/dev/sda1</device>
<device DEVNO="0x0802" TIME="1249271650" LABEL="sda3" UUID="86096e50-069c-46a6-8736-bcd2684830f5" SEC_TYPE="ext2" TYPE="ext3">/dev/sda2</device>
<device DEVNO="0x0803" TIME="1249271640" UUID="9a0a4f43-5c04-438e-b75a-6e2ff5847a7d" SEC_TYPE="ext2" TYPE="ext3">/dev/sda3</device>
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule worker.c>
StartServers         2
MaxClients         150
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule>

#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, in addition to the default. See also the <VirtualHost>
# directive.
#

Sometimes the lines added come from /etc/passwd. And it happens now and then.
BTW, the file system is on a 2G CF card.
I guess it is caused by fscking a corrupt file system on CF card. But I can not make it happen now.

---

