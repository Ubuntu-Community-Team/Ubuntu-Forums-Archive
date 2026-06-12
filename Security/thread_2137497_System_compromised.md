---
title: "System compromised?"
date: 2013-04-20
forum: Security
---

### Post by modest intentions on 2013-04-20
Okay brief background, im pretty new to linux  iv started using the os back in november and im still a greenhorn c: anywho lately my system as been a little bit slower than usual and seems like its running harder than it should at certain points, i switched to the gnome (no effects) desktop  and it helps a lil bit, but my system and especially internet is slower than usual. I did a Netstat -npl as iv read that brings up all the open connections but for me it seems like there are ALOT of ports open? (8118 and 8123 is my proxy) heres a pastebin of the Netstat -npl. If you need more info just let me know, THANK YOU VERY MUCH Ubuntu famjam ^.^

[http://pastebin.com/embed_js.php?i=zPXbYP0L](http://pastebin.com/embed_js.php?i=zPXbYP0L)

also what is 
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN      1335/vmware-authdla

and
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           1287/vmnet-natd 

I do not have any Virtual machine open

---

### Post by Soul-Sing on 2013-04-21
virtual machines do create a network 'fork'. And natd and also vmnet are related to this alternative network. So you must have (had) a virtual machine set-up.
´LISTEN' means no connection. It is a problem removing these services.

---

### Post by The Cog on 2013-04-21
Ignore all those unix socket connections. That's all just local inter-process communication, not network connections, and there are always loads of them. You can use -tuw as an argument to netstat to tell it you only want tcp, udp and raw sockets listed. 

You can ignore any network socket listening on 127.0.0.1 or ::1 as this is the loopback address and cannot communicate to other machines.

Of the remaining ones, only the two vm ones you pointed out look unusual to me. I assume they are something to do with vmware but I'm not familiar with that. They may be services that run all the time, even if there is not currently any vm running. Have you installed vmware? If so, then it's probably normal. 
Maybe someone familiar with vmware can confirm?

---

