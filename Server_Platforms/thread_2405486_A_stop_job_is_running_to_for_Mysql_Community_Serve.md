---
title: "A stop job is running to for Mysql Community Server"
date: 2018-11-06
forum: Server Platforms
---

### Post by pmratpoison on 2018-11-06
I have installed ubuntu 18.04 on a virtual machine as a staging/backup server for my LAMP-based development project.
When I execute sudo systemctl poweroff I get the message
```
A stop job is running to for Mysql Community Server
``` and then it's has to wait for 10 minutes.
Other than being annoying, I do not know if MySQL service stops gracefully after that, which, if not, might lead to all kinds of corruption trouble.
I have seen all the suggestions on stackexchange-et-al and askubuntu, but to little avail
I have come to understand that this might have something to do with time desynchronisation, but I could not make sense of what to do in order to change the order in which MySQL service loads.
Can anyone provide a solution?
Thank you!!!

---

