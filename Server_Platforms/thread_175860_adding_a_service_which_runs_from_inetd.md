---
title: "adding a service which runs from inetd"
date: 2006-05-13
forum: Server Platforms
---

### Post by paulur on 2006-05-13
Hi everyone,

I'm trying the small web server, micro-httpd, which  runs from inetd.  but got troubles to start it.

As the manul's instruction: 
first "make install", and then,

"add a line like this to /etc/inetd.conf:
micro_http  stream tcp nowait nobody  /usr/local/sbin/micro_httpd micro_httpd dir", where dir is the directory to be served.

"Then add a line like this to /etc/services:
    micro_http   8000/tcp   #Micro HTTP server

But when I reboot the machine, then send a http request like: [http://localhost:8000](http://localhost:8000), the error msg says that the connection is refused.

Thank you very much in advance!

Regards,
Paul

---

### Post by ape on 2006-05-14
You need to modify the line that the man page told you to put into the inetd.conf file and change /usr/local/sbin/micro_httpd to /usr/sbin/micro_httpd.  The binary isn't installed into /usr/local/sbin.

You also don't need to reboot to test this out.  Just find the PID of the inetd process (`ps -ef | grep inetd`).  This issue the command `kill -1 <PID of inetd>`.  This will force the inetd process to re-read the /etc/inetd.conf file without rebooting the machine.

--Ape--

---

### Post by paulur on 2006-05-14
Ape, 

Thank you so much for helping me.

[QUOTE=ape]You need to modify the line that the man page told you to put into the inetd.conf file and change /usr/local/sbin/micro_httpd to /usr/sbin/micro_httpd.  The binary isn't installed into /usr/local/sbin.
[/QUOTE]

I did as you taught, but the error still the same. 

BTW, "man micro_httpd" of the version installed in my machine says that inetd.conf should be changed as  ".../usr/local/sbin/micro_httpd", and I found that "make install"
....
BINDIR =        /usr/local/sbin
...
cp micro_httpd ${BINDIR}/micro_httpd

Thanks again!

Regards,
Paul

---

### Post by ape on 2006-05-14
Paul,

 My apologies, I thought you were using the micro-httpd .deb package, not building it from source.

 When I saw your post, I installed the package through apt-get and after modifying the location of where the entry in inetd.conf was looking for the micro-httpd binary (man page is incorrect for the location the Ubuntu package installs the binary), it worked fine for me.

 What entries are in your /var/log/daemon.log file pertaining to micro-httpd when you are getting these errors?

--Ape--

---

### Post by paulur on 2006-05-14
Ape, 

That's really nice of you.

The /var/log/daemon.log reports like this:

"localhost last message repeated 4 times".

btw, i'm not sure whether i installed it correctly. what i did was:
1. download the source code to a directory SOURCE
2. cd SOURCE
3. sudo make install
4. edit /etc/inetd.conf
5. edit /etc/services



Thanks!

Paul

---

### Post by ape on 2006-05-20
Paul,

  What do you see if you try to telnet to port 8000?  Does it appear that any process is listening on that port at all?  

  Can you start up the micro-httpd process manually and connect to it then?  I'm trying to narrow down if it's a problem with micro-httpd itself or if it's an inetd issue.

---

### Post by paulur on 2006-05-20
[QUOTE=ape]Paul,

  What do you see if you try to telnet to port 8000?  Does it appear that any process is listening on that port at all?  

  Can you start up the micro-httpd process manually and connect to it then?  I'm trying to narrow down if it's a problem with micro-httpd itself or if it's an inetd issue.[/QUOTE]

Hi Ape,

Thanks for caring.

I've solved the problem by using xinetd instead of inetd, although still been confused why inetd doesn't work.....


Paul

---

