---
title: "[SOLVED] vsftpd: Failed to retrieve directory listing"
date: 2007-11-05
forum: Server Platforms
---

### Post by btaylor101 on 2007-11-05
Not sure what happened, but on Friday I was able to list directories, but as of today I am no longer able to retrieve directories with my FTP client. All other services are working and I removed and installed vsftpd and still no joy. I am using FileZilla as the client.

---

### Post by btaylor101 on 2007-11-05
It looks to be the transfer mode was causing the problem. I can only list if I use the active connection and not passive. Two questions with that:

1. What are the differences between Passive and Active

2.Is there a setting in vsftpd.conf that allows me to choose between passive and active?

---

### Post by MJN on 2007-11-06
Here is an excellent article on passive and active FTP connections:
 
[http://www.slacksite.com/other/ftp.html](http://www.slacksite.com/other/ftp.html)
 
For VSFTPD configuration see the man pages (pasv_* directives). Note that the choice of connection is decided by the client so you can only choose whether to accept passive connections and, if so, how to manage them. Prepare for a rocky ride...
 
Mathew

---

### Post by btaylor101 on 2007-11-06
Thank you for the link. Very informative and helpful. I was able to get into passive mode by specifying a small range of ports in vsftpd.conf by adding the lines:

> pasv_min_port=x
and
> pasv_max_port=x

I then added the range of ports into iptables and all works now.

---

