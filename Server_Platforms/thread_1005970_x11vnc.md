---
title: "x11vnc"
date: 2008-12-08
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-08
I'm running ubuntu 8.04 and x11vnc 0.9.3.  I'm having trouble getting it running.

When I run "x11vnc" with no arguments, it tries to open :0 but fails:
```

08/12/2008 20:51:56 *** XOpenDisplay failed (:0)
*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.

```

When I run "x11vnc -create" the server seems to start properly.
```

The VNC desktop is:      desktop:0
PORT=5900

```

However, when I connect to it with the windows realvnc viewer I get this server error:
```

PORT=5900
08/12/2008 20:54:22 Got connection from client 10.11.12.254
08/12/2008 20:54:22   other clients:
08/12/2008 20:54:22 wait_for_client: got client
08/12/2008 20:54:22 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh /tmp/x11vnc-find_display.CgbF4Q
08/12/2008 20:54:23 wait_for_client: find display cmd failed
08/12/2008 20:54:23 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.CgbF4Q Xvfb
trying N=20 ...
08/12/2008 20:54:23 wait_for_client: read failed: /bin/sh /tmp/x11vnc-find_display.CgbF4Q Xvfb
08/12/2008 20:54:23 fgets: Bad file descriptor

```

The viewer gives this error:
```

read: Connection reset by peer (10054)
Do you wish to attempt to reconnect to shwick.com:0?

```

I'm not sure why this happens.  I also tried starting the server with sudo- it gives the same error.

I'm pleased that the -listen option works, that's why I switched to x11vnc in the first place.  vnc4server doesn't have the ability to listen on a specific interface.

---

### Post by eldragon on 2008-12-08
when i used x11vnc i had to specify the display myself

try this
```

$ x11vnc -display :0 -shared -forever

```

of course, xorg needs to be up and running in order to work

---

### Post by Shwick2 on 2008-12-08
I don't think I have a xorg desktop running, so I have to use the "-create" option.

I tried "x11vnc -create -shared -forever" but I get the same error.

---

### Post by krunge on 2008-12-08
> **Shwick2 said:**
> I don't think I have a xorg desktop running, so I have to use the "-create" option.

I tried "x11vnc -create -shared -forever" but I get the same error.

If you just run "x11vnc" or "x11vnc -display :0" **YOU** need to already be logged into your X session.  Otherwise there is no X server x11vnc can attach to.

If you want to have x11vnc export your GDM (or other) Login greeter, look under "Continuously" here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

If you want to use the "x11vnc -create" option (this is a poor man's 'vncserver', slower but gives you all of x11vnc's many features) you will need to install the "xvfb" package.

---

### Post by Shwick2 on 2008-12-08
Awesome it works after I installed xvfb, thanks!!!

---

