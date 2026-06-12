---
title: "vncserver code=exited, status=255"
date: 2016-12-23
forum: Ubuntu/Debian BASED
---

### Post by iacoposk8 on 2016-12-23
Hello everyone! following this guide I configured vncserver on kali linux on raspberry 2.
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)
From the client with VNC viewer I get this error: The connection was refused by the computer
While I get from the server:
```

root@kali:/tmp/.X11-unix# systemctl start vncserver@:1.service -l
Job for vncserver@:1.service failed because the control process exited with error code.
See "systemctl status vncserver@:1.service" and "journalctl -xe" for details.
root@kali:/tmp/.X11-unix# systemctl status vncserver@:1.service
&#9679; vncserver@:1.service - Start TightVNC server at startup
   Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: disabled)
   Active: failed (Result: exit-code) since Fri 2016-12-23 09:57:37 UTC; 17s ago
  Process: 1474 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 :%i (code=exited, status=1/FAILURE)
  Process: 1454 ExecStartPre=/usr/bin/vncserver -kill :%i > /dev/null 2>&1 (code=exited, status=255)

dic 23 09:57:36 kali systemd[1]: Starting Start TightVNC server at startup...
dic 23 09:57:36 kali systemd[1454]: pam_exec(login:session): conversation failed
dic 23 09:57:36 kali systemd[1454]: pam_unix(login:session): session opened for user mezzo by (uid=0)
dic 23 09:57:37 kali systemd[1474]: pam_exec(login:session): conversation failed
dic 23 09:57:37 kali systemd[1474]: pam_unix(login:session): session opened for user mezzo by (uid=0)
dic 23 09:57:37 kali systemd[1]: vncserver@:1.service: Control process exited, code=exited status=1
dic 23 09:57:37 kali systemd[1]: Failed to start Start TightVNC server at startup.
dic 23 09:57:37 kali systemd[1]: vncserver@:1.service: Unit entered failed state.
dic 23 09:57:37 kali systemd[1]: vncserver@:1.service: Failed with result 'exit-code'.
root@kali:/tmp/.X11-unix# 

```

---

### Post by howefield on 2016-12-23
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by iacoposk8 on 2016-12-27
Does anyone know a way to debug?

---

