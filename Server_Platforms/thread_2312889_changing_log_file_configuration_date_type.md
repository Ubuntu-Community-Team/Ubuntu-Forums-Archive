---
title: "changing log file configuration date type"
date: 2016-02-08
forum: Server Platforms
---

### Post by kervansoft on 2016-02-08
Hi,

[COLOR=#000000]148.112.237.222 - hftp2 [[/COLOR][COLOR=#ff0000]06/Feb/2016[/COLOR][COLOR=#000000]:10:15:02 +0200] "GET /home/hftp2/wa/dd/D027_06.02.2016/80.txt" 200 12272641

this is my log file of pure-ftpd server ubuntu 14.04 LTS

I want to change date format
06/Feb/2016 to 06.02.2016


is there any way like editing configuration file of pure-ftpd or etc.
I want to change configuration of transfer.log file. I dont know here is the configuration file.




[/COLOR]

---

### Post by blueridgedog on 2016-02-08
I read the man page for the server.  I don't think you can change it.  If you need the other format, you will need to write a log parsing script that corrects if for post processing.

---

