---
title: "Setting up x11vnc"
date: 2007-04-02
forum: Server Platforms
---

### Post by Herm87 on 2007-04-02
Hi

I am encountering problems setting up a x11vnc server. I want to connect to the greeter logon via VNC, but the server can't connect to the display. Although I set the authenication file (correctly, I guess), the server's log says
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```
If I run the server from commandline after personally (and physically) logging into kde, it works fine using port 5901 and display 1 (actually showing display 0).
I'm a complete linux newbie and I may have forgotten something that might be obvious. Any ideas?

EDIT:
Ok, I had to modify the servers arguments to get it running. After I figured out that the authfile is generated each boot and not - as I persumed - each install, I wrote a little script that creates a symlink to the current authfile before starting the server with the arguments x11vnc -rfbauth /path-to-passfile -o /path-to-logifle -auth /pass-to-symlink -display :0 -many (the recommended flags -bg and -initd cause the server to fail).

---

