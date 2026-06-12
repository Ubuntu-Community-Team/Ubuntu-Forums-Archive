---
title: "Can't Connect to LocalHost."
date: 2016-08-30
forum: Server Platforms
---

### Post by jwj12 on 2016-08-30
hi i been having issues connecting to localhost:8085 i'm setting up a software called timetrex my apache2 is running but im still unable to access localhost i get  unable to connect message from firefox  says firefox can't establish a connecting to the server at localhost:8085 any help would be greatly appreciated thankyou.

---

### Post by TheFu on 2016-08-30
Welcome to the forums.
a) is apache running? Check the status.
b) is apache listening on that port?  Use lsof to see that. Also, the relevant apache conf files could be helpful.
c) is timetrex configured correctly?  Can't help with that.
d) is there a firewall running and blocking that port?  Check that with whatever interface to netfilter you use - ufw, gufw, iptables, ipset, whatever.... Just be consistent.

Probably a "Server" subforum question, not a "new to ubuntu" question.  Apache is a server and really NOT for end users.

BTW, the version of Ubuntu and Apache matters for providing the commands to do those things. Which versions are being used?

When you post conf files or output from commands (which you should do), please, use "code tags" in the post so things line up and are easy to read. Posting the commands AND the output are helpful, since experts will be able to see the options and results, not an incomplete interpretation (sometimes).

---

### Post by jwj12 on 2016-08-30
versions
apache2 v2.4.18-2ubuntu3.1
ubuntu server 16.04

apache is running  status says active running 
the firewall is disabled 
timetrex in order to install u have to able to access localhost/filepath thats the part im trying to do.

---

### Post by jwj12 on 2016-08-30
if i run a lsof | grep 8085 i get nothing i do see a bunch of apache though

---

### Post by TheFu on 2016-08-30
Relevant apache config files please - the sites-enabled/ directory is probably sufficient.  Also, check that the listener in apache is on that port, not the default. That setting could be in a few different places.

---

### Post by jwj12 on 2016-08-30
so looking at the sites-enabled its all set up as default not sure what to do there to be honest. i did add port 808 to listen in ports file

---

### Post by jwj12 on 2016-08-30
this is honestly the first time working with ubuntu/setting up anything like this.

---

### Post by jwj12 on 2016-08-30
so update i can access [http://localhost](http://localhost) i cant access [http://localhost:8085/interface/install/install.php(link](http://localhost:8085/interface/install/install.php(link) used to install timetrex)
not sure if its an apache setting i'm missing or a setting in timetrex at this point

---

### Post by TheFu on 2016-08-30
Php?  Can't help. Don't use it.  There are many how-to guides for setting up apache with php on Ubuntu.  BTW, none of this is meant for people new to servers, Linux, apache.  Apache has thousands of different settings.  The defaults are designed for a static website, not php-driven + DB-driven web-apps.  Found this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)  - it also suggests using the "Server Guide" for the release of Ubuntu being run.

Best of luck to you.

---

