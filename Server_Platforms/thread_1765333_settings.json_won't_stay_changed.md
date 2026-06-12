---
title: "settings.json won't stay changed"
date: 2011-05-23
forum: Server Platforms
---

### Post by wlraider70 on 2011-05-23
I'm working on getting transmission-deamon working with remote access.

everything says edit


sudo nano /etc/transmission-daemon/settings.json

specifically
  "rpc-whitelist
  

however, as soon as I do. "sudo service transmission-daemon restart" the settings reset.

---

### Post by papibe on 2011-05-23
Stop the server first:
```
$ sudo service transmission-server stop
```
Edit the file, and then start it:
```
$ sudo service transmission-server start
```
The file is overwritten every time transmission stops.

Regards.

---

### Post by wlraider70 on 2011-05-23
thank you that fixed the immediate problem, but what happens if if restart the computer?

Whats the permanent fix?

---

### Post by papibe on 2011-05-23
That's the way transmission-daemon works. But now that you made the changes, they will stay there after a reboot.

The only thing to remember is that if you need more changes, stop the service before editing the settings.json file.

Regards.

---

### Post by wlraider70 on 2011-05-23
ok, i guess that works.

thanks

---

