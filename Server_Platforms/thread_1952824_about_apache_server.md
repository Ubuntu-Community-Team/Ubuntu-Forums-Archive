---
title: "about apache server"
date: 2012-04-05
forum: Server Platforms
---

### Post by yavuz.maslak on 2012-04-05
Hi 

i use ubuntu11.10. i will install lamb server. there will be 5000 visitors concurrently on my web site.
how should i install lamb server? 
is the lamb server gonna  need to set special values for apache server 's settings?  
thanks

---

### Post by lisati on 2012-04-05
I think you mean "lamp", not "lamb". You might want to have a read through this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Lars Noodén on 2012-04-05
If you're just serving up static web pages then you won't need MySQL, just Apache.  Python and Perl are already installed in Ubuntu by default so you won't need to worry about them either.  

Here are some tips on tuning Apache
[http://www.debianhelp.co.uk/apacheperformance.htm](http://www.debianhelp.co.uk/apacheperformance.htm)

though with the relatively low traffic, you might not need to change much from the defaults.

---

### Post by yavuz.maslak on 2012-04-05
Yes i mean lamp server.

ok, i read the link you gave me. i already install lamp server. 
But is there any special settings for concurrent 5000 visitors?
am i to use prefork_module or mpm_worker_module or threads in apache.conf?
which settings am i to use for below values ?
<IfModule mpm_worker_module>
    StartServers         12
    MinSpareThreads      25
    MaxSpareThreads     175
    ThreadLimit         194
    ThreadsPerChild      25
    ServerLimit         12000
    MaxClients          10000
    MaxRequestsPerChild   0

Thanks  .

---

### Post by CharlesA on 2012-04-05
You should be fine with the default settings.

Just make sure to monitor the system occasionally if you experience slowdown.

---

### Post by SeijiSensei on 2012-04-05
> **CharlesA said:**
> Just make sure to monitor the system occasionally if you experience slowdown.

If you start increasing the number of active server daemons, make sure you have lots of memory in the machine.  You don't want the server swapping to disk while it tries to manage a bunch of simultaneous connections.

---

