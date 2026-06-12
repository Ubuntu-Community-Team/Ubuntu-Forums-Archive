---
title: "Install GUI on Ubuntu Server?"
date: 2011-07-23
forum: Server Platforms
---

### Post by Semek on 2011-07-23
Hey,
I'm new to Ubuntu, and i have a simple question.
I just want to know if there's an option to install VNC Server or something like that
on Ubuntu 10.04 so i can use it's GUI interface? Or it's not possible.
I have only SSH access that i got from the company i bought the server.

I hope there's a way,
thanks in advance.

---

### Post by CharlesA on 2011-07-23
You can install a GUI, yes, but it's usually better to use X11 forwarding unless you absolutely need a GUI.

See here: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Also, VNC is quite insecure, so if you really do want to run a GUI, take a look at FreeNX.

---

### Post by Semek on 2011-07-23
> **CharlesA said:**
> You can install a GUI, yes, but it's usually better to use X11 forwarding unless you absolutely need a GUI.

See here: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Also, VNC is quite insecure, so if you really do want to run a GUI, take a look at FreeNX.

Hey, thanks.
But before i try this, i need to understand something...
i tried first this one,
	[COLOR=#4F4F4F][FONT=Arial]sudo apt-get install xorg lxde

someone recommended it to me.
But the thing is i don't get it how to view the desktop after i install it,
I'm using Windows 7. Do i need some application so i can view the desktop?

Thanks. 
[/FONT][/COLOR]

---

### Post by CharlesA on 2011-07-23
That would install a basic GUI, yes.

You'd need either NXclient or vnc viewer to connect if you installed FreeNX or vnc, respectfully.

---

