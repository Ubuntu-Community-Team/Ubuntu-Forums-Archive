---
title: "sudo tasksel to install LAMP server does not work"
date: 2009-04-24
forum: Server Platforms
---

### Post by fcuk112 on 2009-04-24
so i manually installed mysql-client-5.1 and mysql-server-5.1.  then i remembered i should probably install the LAMP server using sudo tasksel instead.  but this tries to install mysql 5.0 and so i get an aptitude failed (100) error.  

when i try to uninstall mysql-client-5.1 and mysql-server-5.1 it says these packages are not installed and suggests to run apt-get -f install.  when i run that i get the following:

```

franky@BIGBRO:~/Dropbox/Projects/rails/events/config$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  postfix libmysqlclient16 bsd-mailx mailx
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 117425 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what should be the best way to proceed for me?  all i want is tasksel to run without problems (i don't mind MYSQL 5.0 instead of 5.1).

thanks.

---

### Post by KilianValkhof on 2009-04-29
Hey, I just had this problem, you can solve it by going into synaptic, finding mysql-server5.1 and selecting "complete removal" instead of regular removal. 

Then also do that with apache2, php5 etc, and you can just install the server with tasksel and it will work :)

---

### Post by katakaio on 2009-10-20
I had a similar problem and solution on my Hardy server. I had Apache already installed, and tasksel would hang at 0% when installing lamp-server. After doing a simple *sudo apt-get remove apache2*, I was able to install the LAMP stack. A minor inconvenience, but worth it to install the whole stack at once with tasksel. All my Apache pages and settings were saved, and I had the stack installed in seconds. Thank you Ubuntu! :P

---

### Post by jonny-5 on 2009-12-11
Mine is hanging at 0% and I do not have apache2 installed yet. What would be the problem?
Thanks

---

### Post by JonRohan on 2009-12-11
Can you try "tasksel" and select LAMP server from that menu? It will probably yield the same error. If it does then you'll need to install the packages separately. LAMP is a combination of packages.

---

### Post by TwiceOver on 2009-12-11
I don't know about everyone else, but every time I have ever used tasksel and installed LAMP it always "seems" to hang at 0% and then just completes after a while of waiting.  I think there is a bug in the progress meter.

Start it and walk away for about an hour, if it isn't done by then, it probably really won't finish.

---

### Post by Vegan on 2009-12-12
I recently did a fresh install and I had no problems installing any packing on the Pentium IV. Works like a charm.

Was even mercifully quick to complete.

---

### Post by Cheesemill on 2009-12-12
Does the following work?
```
sudo apt-get install lamp-server^
```

PS - Yes there is a caret (^) at the end of lamp-server^ , it's not a typo.

---

### Post by skotl on 2010-09-15
Easy fix for me. tasksel (and apt-get) could not connect to the Ubuntu FTP server. For me, the problem was a too-strict iptables configuration.

---

### Post by skotl on 2010-09-15
Oops - correction. It was port 80/HTTP I couldn't get out on, not FTP. Same cause though; added HTTP outgoing to iptables and it works now.

---

### Post by progone on 2010-09-25
It's happened to me.  The fix for me is to install it as 'root'.

---

