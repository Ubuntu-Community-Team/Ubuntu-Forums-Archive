---
title: "sudoers configuration for nice"
date: 2008-08-23
forum: Security
---

### Post by msknight on 2008-08-23
Hi Folks,

I'm running a game system that uses a java engine. It is running on a newly installed Hardy Herron server, 64 bit.  The normal command works to start the game engine, however, I want to get it to run with a higher priority, so I put "sudo nice -n -2" in front of it.

However, I keep getting asked for my password, and no matter how I enter the line in sudoers, I can't get it to stop.

The line is ...

michelle     ALL=NOPASSWD: /usr/bin/nice

I've also tried other versions like...
michelle     ALL=(ALL) NOPASSWD: /usr/bin/nice
michelle     ALL=(root) NOPASSWD: /usr/bin/nice
... as well as defining my user name as a variable, but I'm just not going anywhere.

Also if I include the nice but omit the sudo and run it as root, it also works, so I'm concluding that my sudoers is going wrong somewhere.

Any help greatly appreciated.

Michelle.

---

### Post by caljohnsmith on 2008-08-23
Even though running the nice command with sudo in front works, it's probably not a good idea since it will also run the game engine as root, which can be dangerous. So instead of messing with sudoers, I think what you really want to do is grant yourself the privilege to "nice" a process without using sudo. You can do that by opening up:
```
gksudo gedit /etc/security/limits.conf
```
And add the following line at the end:
```
<username>   -  nice   -20
```
Replace <username> with your username. You'll need to either reboot or log out and log back in. Then you can run your game engine with just:
```
nice -n -2 <game engine>
```

---

### Post by Gamma746 on 2008-08-24
I think you want something like ```
michelle ALL=(ALL) NOPASSWD: nice -n -2 <game engeine> 
```

---

### Post by msknight on 2008-08-24
Hi,

On the first command I get, Gtk-Warning **:Cannot open display:

This is a server version, and I usually telnet in to it. Do I have to have the X server installed and do this from the machine itself please?

---

### Post by msknight on 2008-08-24
Gamma, didn't work. Parse error in sudoers.

---

### Post by caljohnsmith on 2008-08-24
> **msknight said:**
> Hi,

On the first command I get, Gtk-Warning **:Cannot open display:

This is a server version, and I usually telnet in to it. Do I have to have the X server installed and do this from the machine itself please?
Do you mean you got that from running:
```
gksudo gedit /etc/security/limits.conf
```
If you are telnetting into the machine then the above command won't work, since it tries to open "gedit", which is a GUI text editor. Instead, try using nano:
```
sudo nano /etc/security/limits.conf
```

---

### Post by msknight on 2008-08-31
Thanks - I think that worked. The process shows as -2 in the process table.

---

