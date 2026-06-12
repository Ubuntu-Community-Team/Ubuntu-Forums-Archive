---
title: "Unable to log on to phpmyadmin - Encoding problem?"
date: 2009-03-25
forum: Server Platforms
---

### Post by uNople on 2009-03-25
Note: this was solved by a reboot (d'oh)

I am having a problem logging into my phpmyadmin. It comes up with strange characters on the logon screen. I can log in fine with the CL MYSQL client. This only affects this server, I have other ubuntu servers with phpmyadmin on, and they are all fine. The versions on these servers are all the same.

Here are some screenshots of the error:
[ATTACH]107555[/ATTACH]
[ATTACH]107556[/ATTACH]
[ATTACH]107557[/ATTACH]
[ATTACH]107558[/ATTACH]

The config for php on this server is standard. The only thing I added to the Apache config is restricting what IP addresses can get onto the server (apart from that, it is standard).

Everything was installed using apt - no compiled programs are installed.

The server itself is a VM, but so are all bar one of my other ubuntu servers, and as I said, they are all fine, this is only affecting this.

Other info:

Kernel version:
```

root@server04:/etc# uname -r
2.6.27-7-server

```


php versions:
```
ii  libapache2-mod-php5               5.2.6-2ubuntu4.1              server-side, HTML-embedded scripting languag
ii  php5-cli                          5.2.6-2ubuntu4.1              command-line interpreter for the php5 script
ii  php5-common                       5.2.6-2ubuntu4.1              Common files for packages built from the php
ii  php5-gd                           5.2.6-2ubuntu4.1              GD module for php5
ii  php5-mcrypt                       5.2.6-0ubuntu2                MCrypt module for php5
ii  php5-mysql                        5.2.6-2ubuntu4.1              MySQL module for php5
ii  phpmyadmin                        4:2.11.8.1-1                  MySQL web administration tool
```

---

### Post by lukemacneil on 2009-03-25
I'm having the same issue. Reboot resolved it for a minute, but if I log out and back in.. same problem.

---

