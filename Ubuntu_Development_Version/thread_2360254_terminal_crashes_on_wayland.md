---
title: "terminal crashes on wayland"
date: 2017-05-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-05-02
when using the nautilus option of terminal in the menu bar in a wayand session it will crash and burn.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1687796](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1687796)

---

### Post by mc4man on 2017-05-02
Is this only on folders on the Desktop?
(- gnome-terminal-server crashed with SIGSEGV in _XSend()

---

### Post by ventrical on 2017-05-03
If you log on with wayland session , click  'open terminal' from the right-click menu on the desktop it will crash n burn.. then .. log out of wayland and log in with gnome-classic and it will come up to report gnome-terminal-server error - and then that window will crash as it is a dumb terminal report. I loaded a screen capture program ,<vokoscreen> but wayland will not play/record properly.

I'm using..

```

Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.19.3 driver: N/A
           Resolution: 1440x900@59.75hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 17.0.4 Direct Rendering: Yes

```

---

### Post by ventrical on 2017-05-03
and...

---

### Post by ventrical on 2017-05-03
> **mc4man said:**
> Is this only on folders on the Desktop?
(- gnome-terminal-server crashed with SIGSEGV in _XSend()

in wayland yes..classic,shell not affected. ctrl+alt+t not affected in wayland.

---

### Post by jbicha on 2017-05-03
Are you using artful-proposed?

If you are, could you update your gnome-terminal to 3.24 to see if that fixes the issue?

(Of course, I believe y'all know that I don't recommend using -proposed for Ubuntu releases before they are released as stable.)

---

### Post by ventrical on 2017-05-03
> **jbicha said:**
> Are you using artful-proposed?

If you are, could you update your gnome-terminal to 3.24 to see if that fixes the issue?

(Of course, I believe y'all know that I don't recommend using -proposed for Ubuntu releases before they are released as stable.)

I'll check it out.

regards..

edit: No work .. same thing, flashes open then gone , just like apps during unity8 testing.

---

### Post by ventrical on 2017-05-03
And the 'wayland session' is not even using wayland , it is using x11 .. so there are serious issues here..

```

ventrical@ventrical-System-Product-Name:~$ ps aux | grep gnome-shell
gdm        883  0.5  4.2 2121516 131744 tty1   Sl+  08:57   0:04 /usr/bin/gnome-shell
ventric+  1703  0.0  0.4 614924 15092 ?        Sl   08:58   0:00 /usr/lib/gnome-shell/gnome-shell-calendar-server
ventric+  4939  2.2  5.0 2243228 154908 tty2   Rl+  09:04   0:08 /usr/bin/gnome-shell
ventric+  5906  0.0  0.0  21328  1008 pts/0    S+   09:11   0:00 grep --color=auto gnome-shell
ventrical@ventrical-System-Product-Name:~$ loginctl show-session 2 -p Type
Type=x11
ventrical@ventrical-System-Product-Name:~$ 

```

unless there is new terminal command .

regards..

---

### Post by ventrical on 2017-05-03
Ahh

```

ventrical@ventrical-System-Product-Name:~$ ps aux | grep wayland
gdm        870  0.0  0.1 197496  5352 tty1     Ssl+ 08:57   0:00 /usr/lib/gdm3/gdm-wayland-session gnome-session --autostart /usr/share/gdm/greeter/autostart
gdm        949  0.0  1.4 267320 45808 tty1     Sl+  08:57   0:00 /usr/bin/Xwayland :1024 -rootless -noreset -listen 4 -listen 5 -displayfd 6
ventric+  4901  0.0  0.1 197496  5396 tty2     Ssl+ 09:04   0:00 /usr/lib/gdm3/gdm-wayland-session gnome-session --session=gnome
ventric+  4944  0.8  2.4 378992 74828 tty2     Sl+  09:04   0:05 /usr/bin/Xwayland :0 -rootless -noreset -listen 4 -listen 5 -displayfd 6
ventric+  5953  0.0  0.0  21328  1008 pts/0    S+   09:16   0:00 grep --color=auto wayland
ventrical@ventrical-System-Product-Name:~$ 


```

---

