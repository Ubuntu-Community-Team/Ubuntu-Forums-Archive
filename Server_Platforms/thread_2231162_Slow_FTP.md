---
title: "Slow FTP"
date: 2014-06-23
forum: Server Platforms
---

### Post by Darren_Scott on 2014-06-23
I would like to say thank you to all for all the help and great amount of information that is here on the forums. 

I recently have as of (2 hours ago) been able to setup my own webserver at home. Would have been done alot faster but ended up in the hospital. Getting older is not always fun. 

Now I do have one quick question if I may.

I am using 14.04 server and pure-ftp 
I used this install guide [http://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p2](http://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p2)
but the upload from my machine to the server right next to me is slower than the second coming to put it bluntly. Now as I am slowly learning all of this I am not sure what would control this and how to fix it. 

Any help is appreciated 
DarrenS

---------
I may be dyslexic but I look at it as if I am running my own OS.

---

### Post by cariboo on 2014-06-24
Moved to Server Platforms.

---

### Post by Darren_Scott on 2014-06-24
Well it seems that using pure-ftpd and trying to upload anything over the size of 5,000 bytes it slows right down and even sometimes stops uploading. 
Would anyone be able to point me in soem direction on what a cause for this might be.?

Darren

---

### Post by tgalati4 on 2014-06-24
Who is your internet service provider?  It is possible that your ISP is throttling your connection.  ISP's typically have terms-of-service (break out the reading glasses) that limit your ability to use a web server or any type of file-transfer service.  So look through your terms-of-service to see if that is the case. 

In the meantime, use *iperf* set up as a server and client on another machine and test the raw throughput of your connection.  Search the forums for *iperf* for examples of how to use it.  Post your results.

---

### Post by Darren_Scott on 2014-06-25
I have a business account thought Plus net here in the UK, and they assure me that there is no throttling going on. 
I was studying what is going on and here is the issue so far 
[COLOR=#111111][FONT=Lucida Grande]Uploading files and it seems anything larger than (6,478 bytes) times out.
[/FONT][/COLOR]Now this is with ProFtpd as well it seems.

I will look into using iperf and see what is going on. 

Darren

---

### Post by Darren_Scott on 2014-06-25
I got the information on how to use it from 
[http://ubuntuforums.org/showthread.php?t=2191608&highlight=iperf](http://ubuntuforums.org/showthread.php?t=2191608&highlight=iperf)


This is from the server using the putty client to log in. 

Here is a update with iperf
iperf -c iperf.scottlinux.com
------------------------------------------------------------
Client connecting to iperf.scottlinux.com, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.69 port 43363 connected with 173.230.156.66 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  14.4 MBytes  12.0 Mbits/sec

---

