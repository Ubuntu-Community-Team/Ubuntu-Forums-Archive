---
title: "xdmcp connection"
date: 2010-09-15
forum: Server Platforms
---

### Post by b.leduc on 2010-09-15
Hi,
I have a ubuntu server(10.04 Server Edition 64 bit) that my client wish to connect to in remote desktop. In older version of gdm you could easily setup a remote connection but now it's kind of a pain in the ***!!! And I can't manage to make it work! 
I fallowed this how to: [http://www.peppertop.com/blog/?p=712](http://www.peppertop.com/blog/?p=712). And read a few post in the forums but still noting. When I connect to the server with tsclient I get a black screen(See attached screen shot).
my /etc/gdm/custom.conf: 
```

[xdmcp]
Enable=true
DisplaysPerHost=2

[chooser]

[security]

[debug]

```If anyone could help me?
Thanks

---

### Post by b.leduc on 2010-09-16
Any idea of what I'm doing wrong?

---

### Post by JRV on 2010-10-07
My [xdmcp] section in /etc/gdm/custom.conf looks like this:

   [xdmcp]
   Enable=true
   MaxPending=4
   MaxSessions=16
   MaxWait=15

Use Xephyr instead of Xnest, it seems more stable.
Install it on the client machine with the command:

   sudo apt-get install xserver-xephyr

Open a terminal on the client machine, and start Xephyr with the command:

   Xephyr :1 -query REMOTEHOSTNAME -fullscreen -once

The XDMCP server seems to be broken in the 10.10 (Maverick) release candidate.

---

### Post by Jochus on 2010-10-25
I'm having the same problem.
[B]
Client:[/B] Ubuntu 10.04 Lucid
**Server:** Ubuntu 10.10 Meerkat

With Xnest AND Xephyr, I'm getting a black screen with nothing else ...

In the LOG file, I can see :

```
$ Xephyr :1 -query ##REMOTE_MACHINE## -once
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
Ignoring device from udev.
```

---

### Post by Tristan Schmelcher on 2010-11-01
@Jochus It won't work, the GDM developers broke the server-side XDMCP support in Maverick. No matter what client you use, if the server is running Ubuntu 10.10 with GDM then you can't connect successfully. Here are the bugs for reference:

[https://bugs.launchpad.net/gdm/+bug/669670](https://bugs.launchpad.net/gdm/+bug/669670)
[https://bugzilla.gnome.org/show_bug.cgi?id=627428](https://bugzilla.gnome.org/show_bug.cgi?id=627428)

---

