---
title: "log server"
date: 2007-08-12
forum: Server Platforms
---

### Post by cubytes on 2007-08-12
Hi,

does anyone know of a centralized log server?

If so:

-who makes it?

-windows or Linux?

-user-friendly or pain in the ...?


I had an idea the other day in class, my idea was a centralized log/audit server that can be put on a network and with little configuration be able to seek and  import log files from web servers, DCs, switches, fire-walls, proxy servers and more, maybe even network monitor data. Once imported the log files will be archived and erased from the original device or box.

I wanted to make a user-friendly interface to display log file data, in charts, graphs, time-lines, and more user-friendly details. 

If there is such a program, or service, or server role with that capability then I apologize for my ignorance.....................

---

### Post by foxylad on 2007-08-12
Syslog and syslog-ng both have the capability to log to remote servers, so you can set up all your servers to log to one central server and process the logs there.

[http://www.linux.com/articles/57220](http://www.linux.com/articles/57220)

---

### Post by cubytes on 2007-08-13
thank you

---

