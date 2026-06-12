---
title: "pureftpd AND vsftpd BOTH with the same error: passive port range"
date: 2012-02-09
forum: Server Platforms
---

### Post by metafa on 2012-02-09
Hi @all,

I am really desperate at this point - I am searching on the web for about 6-7 hours now. 

I installed EHCP ([http://ehcp.net](http://ehcp.net)) and it works great - it also installed vsftpd with everything in it - mysql, authentication, tables, everything preinstalled, and works out of the box. But - declaring a passive port range does not work ```
pasv_min_port 65000
```[FONT=monospace] and [/FONT]```
pasv_max_port 65500
```[FONT=monospace]. [/FONT]I followed multiple tutorials, to set it up. I got passive mode working when I disable my firewall. When I dont - no chance. I always receive something like this on the client: ```
227 Entering Passive Mode (xxx,xxx,xxx,xxx,148,201)
```. 148*256 = 37888+201 = 38089. So how is it possible that the port which is sent to the server is below 65000 ?

After hours of trying with different config settings and what not I said to myself whatever, let's try pureftpd. Installed it - works with the same user database, same authentication method - done, works when I disable the firewall. But has the SAME PROBLEM?? gave ```
/etc/pure-ftpd/conf/PassivePortRange
``` ```
65000 65500
``` and when I restart the daemon it confirms it by saying Restarting ftp server: ```
Running: /usr/sbin/pure-ftpd-mysql -l mysql:/etc/pure-ftpd/db/mysql.conf -l pam -8 UTF-8 -O clf:/var/log/pure-ftpd/transfer.log -A -u 1000 -p 65000:65500 -E -B
``` . But still ftp client receives ```
227 Entering Passive Mode (xxx,xxx,xxx,xxx,208,202)
``` which comes down to port 53450. What is going on? How is it possible that 2 different softwares are giving the same error?

My system: Ubuntu Server 10.4, 32 bit

Can someone help here please.. At the moment I am really fustrated and my mind is blocked from ideas :( problem is, I have to have this running by tomorrow.. clients are waiting -.-

Many thanks in advance!

---

