---
title: "Automatic Time Sync each day."
date: 2007-01-15
forum: Server Platforms
---

### Post by Jamaicanyouth on 2007-01-15
Hi,
I have a Ubuntu 6.06 LAMP server and I would like to set it up so that each day it would synchronize with an internet time server.  Some type of cronjob maybe?  I am a Linux newbie so I need help with the command line, as the server environment is command line.  Any help would be greatly appreciated.

---

### Post by Jamaicanyouth on 2007-01-16
Does anybody have an idea?

---

### Post by Brazen on 2007-01-16
you want to use ntp: "apt-get install ntp"

You can google around to find docs on how to configure ntp.  It's pretty simple, you put a few lines for the servers you want to sync to, and then start the ntp daemon.

---

### Post by MJN on 2007-01-17
Check out [https://help.ubuntu.com/community/NTPTimeSynchronisation](https://help.ubuntu.com/community/NTPTimeSynchronisation)
 
Mathew

---

