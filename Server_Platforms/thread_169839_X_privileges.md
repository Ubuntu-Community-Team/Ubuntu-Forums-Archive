---
title: "X privileges"
date: 2006-05-03
forum: Server Platforms
---

### Post by towsonu2003 on 2006-05-03
Correct me if any of these assumptions are wrong here..

We run X with root privileges, right? as in
$ sudo /etc/init.d/gdm start

but we can also run X with user privileges by shutting down gdm and starting X with
$ startx
from a tty

Gnome launched like this will not even give you permission to shut down or restart the pc -only to log off. Gnome launched with sudo /etc/init.d/gdm start lets you shutdown or restart, hinting that it has more privileges that can be used. 

am I right so far? if yes, my question is: are there risks associated with running X with root privileges? 

PS. I'm not gonna say "let's change ubuntu". Just curious.

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=towsonu2003]Correct me if any of these assumptions are wrong here..

We run X with root privileges, right? as in
$ sudo /etc/init.d/gdm start[/quote]No, that runs the script /etc/init.d/gdm start.  That doesn't mean any services it starts will stay as root, as they could drop privilege after startup (e.g., SSHD).


> but we can also run X with user privileges by shutting down gdm and starting X with
$ startx
from a ttyNope.  I think you'll find your X Server is setuid root and runs as root all the time.

> Gnome launched like this will not even give you permission to shut down or restart the pc -only to log off.That's a design decision because it presumes it's not in total control.

>  Gnome launched with sudo /etc/init.d/gdm start lets you shutdown or restart, hinting that it has more privileges that can be used. **GDM** does sure, but I'm not sure what gnome-session does. At any rate, your actual applications don't run as root in either situation.  X certainly does.

BTW, this can be trivally verified by do 'ps axu' on the console.

> if yes, my question is: are there risks associated with running X with root privileges? There are plenty, but fixing it isn't easy without a large rewrite of xorg internals.  OpenBSD has done some work in this area, but it's probably not portable to Linux without giving up some features.

---

### Post by towsonu2003 on 2006-05-03
this was most informative, thanks :)

---

