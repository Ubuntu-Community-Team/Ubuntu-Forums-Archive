---
title: "PureFTPD slow when uploading multiple files"
date: 2019-01-16
forum: Server Platforms
---

### Post by wwatanabe on 2019-01-16
Hi All ! 


Thanks for helping us everyday !


I've just install an Ubuntu 18.04 server following the Perfect Server ([https://www.howtoforge.com/tutorial/perfect-server-ubuntu-18.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-18.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)) instructions.


We're using PureFTPd Server for FTP connections.


I'm hosting the server on DigitalOcean Droplet, and when I run a speedtest I get:


root@cloud01:~# ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Digital Ocean (111.11.11.11)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Ridge Wireless (Cupertino, CA) [5.08 km]: 2.717 ms
Testing download speed................................................................................
Download: 853.46 Mbit/s
Testing upload speed................................................................................................
Upload: 683.06 Mbit/s


The problem is:


OLD Scenario - Shared Server in a Brazilian ISP
When I send a 112MB file to the server (PureFTP too) it takes about 00:00:31 (average: 3.6MB/s)


NEW Scenario - VPS Droplet in DigitalOcean SFO2
When I send a 112MB file to the server (PureFTP) it takes about 00:00:34 (average 3.2MB/s)


Its not a big difference and it is ok for me.


BUT, When I send 100 files of 12KB:


OLD Scenario takes 00:00:06 (about 360KB/s)


NEW Scenario takes 00:01:45  (about 11KB/s)


The same happens when I'm deleting files, on the new server it takes too longer than in the old server.


========================


LOGs


New_Scenario: [https://pastebin.com/iVyyQHvW](https://pastebin.com/iVyyQHvW)
Old_Scenario:  [https://pastebin.com/BD6Zy3vd](https://pastebin.com/BD6Zy3vd)

CONF:

NewServer Conf: [https://pastebin.com/6kvbmCWn](https://pastebin.com/6kvbmCWn)


========================


So we know that the problem remains in working with a lots of file, and not with the size of the file. So, we don't think it's a bandwidht problem but in the communication between client and server before each file transfer.


Any clue will be appreciate !




Thanks in advance !

---

