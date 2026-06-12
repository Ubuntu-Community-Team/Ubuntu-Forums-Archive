---
title: "Dapper Server GUI"
date: 2006-06-11
forum: Server Platforms
---

### Post by Nyati on 2006-06-11
Hi

I've installed Lamp Server on my IBM T30 and am presented with a command prompt.

Is there a GUI to this server package?

I was under the impression that the LAMP Server installation would deliver the same package as the desktop and alternate cd's, with the exception that LAMP would also be installed.

Any help?

The reason I need a GUI is to help me activate my ethernet connection.

If anyone can help me do this using the command prompt - great, much appreciated in advance!:???:

---

### Post by olsonar on 2006-06-11
you can easily install the standard ubuntu gui. just use this command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Nyati on 2006-06-11
Thanks Olsonar

with a bit of help by Teckdeck on irc.dal.net I managed to get my internet connection through eth0.

Now running: apt-get install ubuntu-desktop

:lol:

---

### Post by lonetree on 2006-06-21
did it work after apt-get install ubuntu-desktop? I tried to install xcfe4 but it did start up in gui, anyone out there could help?

---

### Post by spifbv on 2006-06-21
[QUOTE=lonetree]did it work after apt-get install ubuntu-desktop? I tried to install xcfe4 but it did start up in gui, anyone out there could help?[/QUOTE]

Try this:

apt-get install gdm

That should give you a GUI login screen after reboot (or by running /etc/init.d/gdm start)

---

