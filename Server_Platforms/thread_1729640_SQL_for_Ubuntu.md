---
title: "SQL for Ubuntu"
date: 2011-04-15
forum: Server Platforms
---

### Post by JumpOnIt on 2011-04-15
Hello
 
Does anybody know if there is a command line to put into the Ubuntu terminal that will activate SQL. If there is then i would be grateful to know it.
 
Many Thanks
from
 
JumpOnIt

---

### Post by Joe of loath on 2011-04-15
[http://www.google.co.uk/search?q=ubuntu+mysql&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+mysql&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a)

---

### Post by elico on 2011-04-17
service mysql start
or
/etc/init.d/mysql start
or stop...
or status...
the other option is to run the daemon itself using:
> **/usr/sbin/mysqld** &
will take it also to background.

---

### Post by hamiljf on 2011-04-27
I am one of many having a problem sorting out MySQL.  Two or three distros ago I was messing with it and despite complete removal and reinstallation, and distro upgrades, I have an installaton that I can't get to work.  The syslog entries are

Apr 27 10:05:53 M575U init: mysql post-start process ( 19278 ) terminated with status 1
Apr 27 10:05:53 M575U kernel: [ 6529.035603] type=1505 audit(1303895153.605:233):  operation="profile_replace" pid=19366 name="/usr/sbin/mysqld"
Apr 27 10:05:54 M575U init: mysql main process ( 19370 ) terminated with status 2
Apr 27 10:05:54 M575U init: mysql main process ended, respawning

... repeating until doomsday.
Trouble is, I have no idea what sort of fix it is wanting.
Can anyone advise ?
(btw, using Lucid Lynx now)

---

### Post by Usa_Tony_Cuba on 2011-04-27
> **JumpOnIt said:**
> Hello
 
Does anybody know if there is a command line to put into the Ubuntu terminal that will activate SQL. If there is then i would be grateful to know it.
 
Many Thanks
from
 
JumpOnIt
Did you have installed mysql (server - or - client) , haven't you..?

---

