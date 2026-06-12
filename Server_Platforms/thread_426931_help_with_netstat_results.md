---
title: "help with netstat results"
date: 2007-04-28
forum: Server Platforms
---

### Post by adza on 2007-04-28
hi there... i have just installed LAMP on my feisty desktop... the last lines of the netstat -ta command concern me a little.... could someone please explain to me what these results are? I don't think that they should be there myself... how do i turn these off?

tcp        0      0 adza-pc.local:54009     ohiggins.ubuntu.com:www TIME_WAIT  
tcp        0      0 adza-pc.local:44082     c-67-168-224-243.:56418 ESTABLISHED
tcp        0      0 adza-pc.local:47839     dhcp80ff5505.dynam:9718 TIME_WAIT  
tcp        0      0 adza-pc.local:47703     dhcp101093.res-ha:13114 TIME_WAIT  
tcp        0      0 adza-pc.local:33166     cg-in-f103.google.c:www ESTABLISHED
tcp        0      0 adza-pc.local:41915     128.164.35.237:40139    ESTABLISHED
tcp        0      0 adza-pc.local:43245     c007b.crwg.uic.ed:38309 ESTABLISHED

---

### Post by nixfaced on 2007-04-29
A good place to start would be to run 'sudo netstat -tupan'.  The -p switch displays the process responsible for each network connection.  Then you can stop whatever program is responsible for the connections you don't want.

---

