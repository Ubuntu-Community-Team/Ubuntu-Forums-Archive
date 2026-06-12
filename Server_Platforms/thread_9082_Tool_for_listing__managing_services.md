---
title: "Tool for listing / managing services"
date: 2004-12-23
forum: Server Platforms
---

### Post by Rottweiler on 2004-12-23
Is there a simple tool to manage/control/list which services start at which runlevels?
 
 update-rc.d is the usual answer to such a question but it only allow you to set things and not list them.
 
 My background is RH/FC and I'm accustomed to /sbin/chkconfig.
 
 Thanks.

---

### Post by Mattt on 2004-12-29
[QUOTE=Rottweiler]Is there a simple tool to manage/control/list which services start at which runlevels?
 
 update-rc.d is the usual answer to such a question but it only allow you to set things and not list them.
 
 My background is RH/FC and I'm accustomed to /sbin/chkconfig.
 
 Thanks.[/QUOTE]

This may help

[http://www.ubuntuforums.org/showpost.php?p=35858&postcount=8](http://www.ubuntuforums.org/showpost.php?p=35858&postcount=8)

---

### Post by Rottweiler on 2004-12-29
Thanks, Mattt. I'll give that a whirl.
 
 I was contemplating writing something to do that. Maybe I won't have to.

---

### Post by britishtrident on 2005-01-02
[QUOTE=Rottweiler]Is there a simple tool to manage/control/list which services start at which runlevels?
 
 update-rc.d is the usual answer to such a question but it only allow you to set things and not list them.
 
 My background is RH/FC and I'm accustomed to /sbin/chkconfig.
 
 Thanks.[/QUOTE]
 Load Webmin either get  from the universe depository or down load in from webmin.com and run the install script    ---  choose Debian as the operating sysyem. Webmin is a very powerful user friendly tool  but 
**** BE AWARE ****   Webmin can open a security threat so once installed restrict acc by setting up its  IP address filters.

---

### Post by jdodson on 2005-01-03
[QUOTE=Mattt]This may help

[http://www.ubuntuforums.org/showpost.php?p=35858&postcount=8](http://www.ubuntuforums.org/showpost.php?p=35858&postcount=8)[/QUOTE]


ya, rcconf is great.

---

