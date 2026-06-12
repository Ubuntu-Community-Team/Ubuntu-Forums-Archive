---
title: "Autostart Ruby Apps on Reboot"
date: 2009-11-09
forum: Server Platforms
---

### Post by spauldingsmails on 2009-11-09
Hi

First off let me point out that I do not really know much at all about installing and configuring ruby on rails applications, so I'm not even sure if the terminology I'm using is correct.

Anyway, I have a ruby on rails application that I am running on Ubuntu 8.10 and have deployed using the rake command;

```
sudo rake bibapp:start
```

The application runs fine until the server is rebooted and then I need to log in via ssh and execute the command again.

I've read somewhere that the ruby gem "daemon" handles the starting and stopping of ruby applications deployed this way, including restarting them if they unexpectedly crash. While I'm unable to prove whether this is working for me, an unexpected reboot of my hosted server has shown me that my application does restart on server boot.

Any help would be much appreciated.

Cheers


Hayden

---

