---
title: "disable mysql autostart"
date: 2007-06-06
forum: Server Platforms
---

### Post by ramboza on 2007-06-06
I'm sorry, i've found some similar topics, but none of them really helped...
I've 7.0.4, installed mysql server, and i do not want it to start automatically on the system boot.

As for apache2 - there's a corresponding file at /etc/default/apache2 which you can edit to enable/disable running this service on boot.

But how to disable mysql autostart? 

update-rc.d mysql remove - says: 
update-rc.d: /etc/init.d/mysql exists during rc.d purge

There are also no entries in system-preferences-sessions-startup programs for mysql (and for apache2...)

---

### Post by turinglabs on 2007-06-06
Remove actually deletes the script - use '-f' to force it if this is really what you want. Something like 'update-rc.d mysql stop 2 3 4 5 .' might work to just stop the service.

I have never liked update-rc.d, I usually install the 'sysv-rc-conf' package, it gives you a curses interface where you can selectively enable/disable scripts in each runlevel (note - the changes you make with it take effect right away).

---

### Post by ramboza on 2007-06-06
Thanks a lot man! Very clever and useful package!

---

### Post by dustigroove on 2007-06-06
[FONT=Arial][SIZE=2][COLOR=Black]Very nice, glad I came across this post.

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by hs8kic on 2007-12-12
Thank you is pretty cool tool.

---

