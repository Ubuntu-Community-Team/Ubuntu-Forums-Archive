---
title: "Gtk-WARNING **: cannot open display"
date: 2009-07-08
forum: Server Platforms
---

### Post by ethernaly on 2009-07-08
Hello, I've an Ubuntu 8.04 Jeos server.
I try to get running "Jchav". [http://jchav.blogspot.com/](http://jchav.blogspot.com/)

But, jchav give me this error:
```
(.:4074): Gtk-WARNING **: cannot open display: 
```


I think because a server haven't a "gui", but I try to install xorg and some libgtk, but nothing, the error is the same.

I can't install a DE like GNOME, or a WM like fluxbox (if it's possible), because only jchave need some gtk dependencies.

Can anyone help me to solve this problem?

---

### Post by Sub101 on 2009-07-08
Are you accessing your server over SSH?

If you are you must use the flag -X ie.
```
ssh -X server@123.123.1.1
```

---

### Post by ethernaly on 2009-07-08
the problem is that I want to automatize jchav, so I want to do a simple bash script like this:

#!/bin/bash
cd /path/to/jchave/
ant -f build-example.xml

and I want to put this script under a cronjob.

So, I can't use my "X".

---

### Post by Sub101 on 2009-07-08
Oh I see. In that case im not sure if it is possible? Other than if the program is allowed to run from command line.

---

### Post by ethernaly on 2009-07-08
mmm I think, that maybe, I can use the xmove package.

I've a virtual machine with GNOME.

maybe I can use that x11.

someone have experience with xmove? how to use it?

My configuration is:

virtualmachine jchav+jmeter: ubuntu server Jeos ip: 192.168.1.2
virtualmachine Gnome: ubuntu 8.04 hardy (DE: GNOME) 192.168.1.4

The problem is that jchav run Jmeter, and Jmeter request a lots of cpu and memory, so GNOME machine can't do that alone.

mmm maybe I can do:
export DISPLAY=192.168.1.4:0

but I think I need to do something before? maybe some configuration like rsa access?

---

### Post by ethernaly on 2009-07-08
Solved :)

I export the display with xhost authorization!

Thanks anyway ;)

---

