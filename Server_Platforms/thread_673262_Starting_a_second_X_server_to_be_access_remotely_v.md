---
title: "Starting a second X server to be access remotely via VNC - problems"
date: 2008-01-20
forum: Server Platforms
---

### Post by Svenstaro on 2008-01-20
I'm trying to run a virtual WinXPx64 on my Ubuntux64 using VMWare started by tightvncserver which is started by X on another screen. 
On Debian, I accomplished it by running this script:
(with the only exception that on Debian I use xtightvnc instead of tightvncserver)

```
#!/bin/sh

PATH=/bin:/usr/bin:/usr/bin/X11:/usr/local/bin:/sbin:/usr/sbin:/usr/local/sbin
DISPLAY=localhost:1

# for xauth
export HOME=/root

case "$1" in
  start)
    echo -n "Starting tightvncserver"
    cd /opt/vmware
    nohup startx "vmware -x -q /opt/vmware/winxpimage" -- /usr/bin/tightvncserver :1 -geometry 1280x1024 -depth 16 -rfbauth /root/.vnc/passwd 2> /var/log/vmware-vnc/xvnc-err.log > /var/log/vmware-vnc/xvnc.log &
    echo "."
  ;;

  restart)
    /etc/init.d/vmware-vnc stop
    /etc/init.d/vmware-vnc start
  ;;

  stop)
    echo -n "Stopping "
	killall 
  ;;

  *)
    echo "Usage: /etc/init.d/vmware-vnc {start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

Sadly, this no longer works on Ubuntu. The error I get is:

> Xlib: connection to ":1.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

Now I did a bit of research on the magic cookie and added myself to the magic cookie list. 
> xauth list
machine/unix:0  MIT-MAGIC-COOKIE-1  5663813b335cc574f93eec55d750ce43
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  5663813b335cc574f93eec55d750ce43
machine:1  MIT-MAGIC-COOKIE-1  40de4f8e6aa92481d82a5cfa53af1d57
machine/unix:1  MIT-MAGIC-COOKIE-1  40de4f8e6aa92481d82a5cfa53af1d57
localhost:1  MIT-MAGIC-COOKIE-1  fd8a566465091ba6e8a215796e68826c
localhost.localdomain/unix:1  MIT-MAGIC-COOKIE-1  fd8a566465091ba6e8a215796e68826c
machine:0  MIT-MAGIC-COOKIE-1  df8d5581e2e0efa8667c8c6fb853c568


Still no-go. Ideas?

---

### Post by Svenstaro on 2008-01-20
Ah shoot! The only difference WAS the problem. I didn't even think about THAT! I'm now using Xvnc, tightvncserver wasn't meant to be run on another display.

---

### Post by HermanAB on 2008-01-20
SSH is just so much less trouble and it is secure too.

Cheers,

Herman

---

### Post by Svenstaro on 2008-01-21
You mean like tunneling VNC through SSH? Well actually it doesn't really matter because the server is local. If it was through WAN I'd tunnel through SSH of course.

---

