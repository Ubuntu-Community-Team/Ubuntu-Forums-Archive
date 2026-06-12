---
title: "Extermly high %CPU in ps output"
date: 2009-12-14
forum: Server Platforms
---

### Post by Aethedor on 2009-12-14
Hi,

one of my processes shows an extremely high %CPU in the 'ps' output:

```
[FONT="Courier New"]USER     PID   %CPU      %MEM VSZ   RSS  TTY   STAT START TIME        COMMAND
www-data 13729 93370072  0.4 119424 4820 ?     Ssl  09:05 21229866:17 /usr/sbin/hiawatha[/FONT]
```

The %CPU (and TIME) are extremely high, but also decreasing every second. When they reach zero, the next second they are extremely high again.

The process is a webserver, with almost no traffic according to network sniffers.

 The CPU load on the system remains zero:
 14:43:14 up 23:57,  2 users,  load average: 0.00, 0.00, 0.00

What is going on here?

I use Ubuntu 8.04 LTS, kernel is 2.6.31.5xls-domU. Server is a VPS.

---

### Post by Aethedor on 2009-12-15
Nobody?

---

### Post by Lars Noodén on 2009-12-15
Try following hiawatha in a little more detail.  

vmstat, top, and lsof can help a little to try to guess what it is doing.  

You can also try running the server standalone and not let it detach and become a daemon.  It that way you can also follow live and in more detail what it is doing.  That would be using the [**-d** option](http://www.hiawatha-webserver.org/manpages).

hiawatha doesn't appear to be in any of the Ubuntu repositories.  So you might get better help on one of the applications own mailing lists or forums.

---

### Post by Aethedor on 2009-12-15
I'm sorry, I think I should have mentioned that I am the author of Hiawatha.

With Hiawatha, there is nothing wrong. Running it for years without problems. If you look at what ps says, you'll see that it doesn't make any sence. 93370072% CPU usage is bu11sh1t. The output of 'w' shows 0.00 load. My guess is that it's a kernel bug. But because I use a non-Ubuntu kernel (one supplied by the VPS hosting company) I realize this forum isn't the right place for this issue. Thanks anyway.

---

