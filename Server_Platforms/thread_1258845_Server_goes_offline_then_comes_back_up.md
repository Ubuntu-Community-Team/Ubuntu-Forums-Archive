---
title: "Server goes offline then comes back up"
date: 2009-09-05
forum: Server Platforms
---

### Post by Cardale on 2009-09-05
I have used Ubuntu and Debian and over the course of using each OS which are great by the way.  I have encountered a very annoying problem.  I do web development and since it's local I use it as my development server and my production.  Randomly while I'm doing some editing or trying to refresh my website between changes it wont return anything.  404 error.  Without me doing anything it will come back on a few seconds later some time 30 seconds or more later.

What could this problem be attributed to?  I thought maybe the router, but want to check the OS first.

---

### Post by hessiess on 2009-09-05
Are you running the server on a wireless network by any chance?

---

### Post by Cardale on 2009-09-05
There are wireless devices connected to the router, but the server itself is wired with good old cat 5.

---

### Post by Cardale on 2009-09-05
bump

---

### Post by cariboo on 2009-09-05
Have you checked the apache2 error log located in /var/log/apache2?

---

### Post by Cardale on 2009-09-06
Yes and I don't see anything that would draw any attention or even related.

---

### Post by hessiess on 2009-09-06
Have you tryed acsessing it directly via the IP adress to rule out a DNS problem?

---

### Post by Cardale on 2009-09-06
Yes there is a problem with the DNS.  My domain hardly works.  I usually check both and when I do any ssh or sftp I always use the local ip address and I have those problems when editing files.  I was hoping once I fixed the server seemingly being unreachable I would inadvertantely fix the DNS issues.

The setup
Router - Linksys WRT54G - factory firmware - has a update client for DynDNS that seems to be working fine.
DNS - DynDNS - I paid for a custom dns service and bought my own domain that uses there name servers.
Server - Ubuntu 9.04 I believe fully updated with shorewall install accepting all HTTP and SSH traffic.

As far as configuration goes I don't know what else to do.  They don't cover any issues like this in tutorials.

---

### Post by Cardale on 2009-09-06
Still searching for an answer... :confused:

---

### Post by Cardale on 2009-09-07
I've been steady working at the problem for the last few days and I think I have narrowed some things down.  The server does occasionally crash during sftp and ssh which is unacceptable, but may be contributed to some sort of session timer that is disconnecting me, but this shouldn't totally stop apache correct? if that is even the cause.  

I believe the domain issue is caused by a bad router configuration which I don't understand yet, but if anyone is well versed with shorewall can kindly chime in whenever they wish. If I figure out a way to make it work I will post my findings thanks.

---

### Post by lynnet on 2009-10-31
I have meet the same problem. When I uploading many webpages with SFTP, the web server goes offline  occasionally. I can't connect to it with Ping, SSH and WWW untile reboot.

Ubuntu 9.04  server.
SSH Server ( with key file)
SFTP (FileZilla ftp), connect to it with IP address.

---

### Post by Cardale on 2009-10-31
I have left my server running now for a considerable time and it seems to be doing fine although I think if I restart the server it might encounter the same problems.  I am not sure what tables needed to be updated, but chances are it could of been some networking problem.  Make sure all your tables are configured correctly and your router if you have one is set on static IP address.

---

### Post by samosamo on 2009-10-31
The fact that you state "404," assuming you are not throwing geeky terms around, indicates communication between you and a web server is established. It is not a networking issue. It is either a bad web server configuration, or you are accessing a web server you don't intend to access (like typing the wrong hostname, or having a bad DNS config that makes you think you are accessing the correct machine).  The latter can be troubleshooted by simply accessing your server via it's IP address to see if the 404 comes up. If it doesn't, I would definitely inspect your web server's logs very closely.

---

