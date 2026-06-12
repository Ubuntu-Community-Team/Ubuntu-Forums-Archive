---
title: "Firestarter assistance"
date: 2007-05-22
forum: Server Platforms
---

### Post by dachinster on 2007-05-22
Hi, i was trying to get Firestarter to launch on every bootup and i ended up screwing up a bit and i dont know if i posted in the right section

this is the line that i added sudo visudo
```
dachinster ALL= NOPASSWD: /usr/sbin/firestarter
```

then i went into sessions and i added
```
sudo firestarter --start-hidden
```
and gave it the title Firestarter

i rebooted to test it, but i dont see it...
do i have to remove the hidden part?


also, another thing
i think i screwed up somewhere because the only way i can run firestarter now is as root
i have to run sudo su
then put in my password <enter>
then type gksudo firestarter in a terminal in order to launch it
but if i close the terminal window where i typed gksudo firestarter, the application also closes
this also happens if i just try sudo firestarter in a root terminal

when i try to launch it from system>administration>firestarter
it no longer asks for the password but then it hangs
i see it in my taskbar saying "Starting FIrestarter" and then it crashes

if i type gksudo firestarter in a terminal, this is what i get:
```
dachinster@Ubuntu:~$ gksudo firestarter
No protocol specified

(firestarter:21788): Gtk-WARNING **: cannot open display: 
```

and nothing happens

if i try sudo firestarter in a terminal i get:
```
dachinster@Ubuntu:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:21889): Gtk-WARNING **: cannot open display: 
```

i tried purging firestarter and installing fresh but it does not change anything

---

### Post by dachinster on 2007-05-24
anyone can assist with this?
maybe i posted in the wrong forum...

---

### Post by ruy_lopez on 2007-05-24
Is there a script called firestarter in /etc/init.d ?

---

### Post by nomb on 2007-05-24
No there wont be a script. 

We'll get it working though.

First Off:  When you reboot, do an iptable -L and make sure your rules aren't applied.

Secondly:  I'm not good with sudo.  When you added that sudo line can you sudo firestarter and it works?

Thirdly: Instead of putting it into sessions, try /etc/rc.local.  And everything has to be the full paths, not 'sudo' or 'firestarter'

---

### Post by visio159 on 2007-05-26
```
dachinster ALL= NOPASSWD: /usr/sbin/firestarter

```

remove this line from sudoers, it will let u start the GUI interface.

---

### Post by frogotronic on 2008-01-19
> **visio159 said:**
> ```
dachinster ALL= NOPASSWD: /usr/sbin/firestarter

```

remove this line from sudoers, it will let u start the GUI interface.

Okay, that works...

---

