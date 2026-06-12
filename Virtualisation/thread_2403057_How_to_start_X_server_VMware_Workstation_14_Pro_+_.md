---
title: "How to start X server? VMware Workstation 14 Pro + Ubuntu 18.04"
date: 2018-10-07
forum: Virtualisation
---

### Post by zzzhhh on 2018-10-07
I typed "startx", but responded the following errors:


```
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console

```

I pressed Ctrl+Alt+F1 but could not switch to pure terminal mode. So how can I start X server? I am running Ubuntu 18.04 in VMware Workstation 14 Pro. Thank you for your help.

---

### Post by TheFu on 2018-10-07
Which 18.04 variant?  Server doesnt have an X/Server.  

All the desktops should startup with X by default, unless you specifically chose to use Wayland instead, so something else is happening.  Also, if you are remoting into the system the client/server architecture for X11 is backwards  - the remote system is the X-client and the physical machine you sit behind is the X-server.

I dont have VMware.

---

### Post by zzzhhh on 2018-10-07
It turns out that the cause is I forgot "sudo".

---

### Post by TheFu on 2018-10-07
> **zzzhhh said:**
> It turns out that the cause is I forgot "sudo".

Yep.  xorg runs as root.

---

