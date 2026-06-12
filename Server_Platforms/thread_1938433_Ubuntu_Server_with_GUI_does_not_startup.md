---
title: "Ubuntu Server with GUI does not startup"
date: 2012-03-09
forum: Server Platforms
---

### Post by Nick_C on 2012-03-09
I have just done a completely clean install of Ubuntu Server 11.10.  On top of that I have tried to add a GUI:
> sudo aptitude install x-window-system-core gnome-core gdm
At the end of theinstall the machine reboots automatically.

Now it boots to a GUI logon window but after I logon all I get is a black screen with a mouse pointer.  Any ideas?

Thanks,

---

### Post by jerrrys on 2012-03-09
x-window-system-core.  No such package in 11.10.  Think thats an old package your trying to install.  Try xorg

[ATTACH]214020[/ATTACH]

---

### Post by Nick_C on 2012-03-10
> **jerrrys said:**
> x-window-system-core.  No such package in 11.10.  Think thats an old package your trying to install.  Try xorg

[ATTACH]214020[/ATTACH]

Tried that, looks like xorg is already installed.  It must have been a dependent of something in my original install command.

---

### Post by Bradyhawke on 2012-03-10
Here's a link to a previous post - scroll down to my reply and check it out:

[* http://ubuntuforums.org/showthread.php?t=1673745 *]("http://ubuntuforums.org/showthread.php?t=1673745")

It basically sets up a minimum GNOME install on a 10.04 LTS server that I used for a time until I really got better with the command line.  I still keep it on one of my servers, but the other 3 now are command line only.

- Bradyhawke

:guitar:

---

