---
title: "RAM eater: cups"
date: 2013-12-09
forum: Server Platforms
---

### Post by papibe on 2013-12-09
Hi all

I used to have a printer attached to my home server, but the printer died a few months back and the new one is no longer connected to my server.

I was checking the RAM usage, and I realize I still had cups running:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1498       [COLOR="#FF0000"]**1461**[/COLOR]         36          0        249       1044
-/+ buffers/cache:        167       1330
Swap:         1906          0       1906

$ sudo service cups stop
[sudo] password for user: 
 * Stopping Common Unix Printing System: cupsd                           [ OK ] 

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1498        [COLOR="#FF0000"]**424**[/COLOR]       1074          0        180        107
-/+ buffers/cache:        136       1361
Swap:         1906          0       1906

```
WOW, I freed more than a gig of RAM! :confused:

I wonder if anyone have experience this, and if it is a problem with cups, or a configuration issue?

Thanks in advance.
Regards.

---

### Post by bashiergui on 2013-12-09
If cups is constantly polling its long lost printer then that could account for the ram usage. I suppose you could watch your network traffic to see what cups is up to.

---

### Post by tgalati4 on 2013-12-09
Check /var/log/cups for large log files.  That may account for some of the RAM usage.  Were there a bunch of pending print jobs waiting for this printer from other users?  That could also take up some space.

---

### Post by papibe on 2013-12-09
Thanks for tips bashiergui and tgalati4. I'll look into it.

Regards.

---

### Post by cariboo on 2013-12-12
Actually, you only freed up about 30MiB of ram, if you look at the buffer/cache line. The rest of the ram that was freed up was just reserved for cups, if another process needed the ram, it would be made available for it's usage

---

### Post by papibe on 2013-12-16
There was a 'ghost' process trying to print even after uninstall cups, so I image something was not properly working.

Thanks cariboo907, I think I understand better 'free' now. It also makes sense with the output of these tool: [ps_mem.py ]("https://raw.github.com/pixelb/ps_mem/master/ps_mem.py").

Thanks for all your help.
Regards.

---

