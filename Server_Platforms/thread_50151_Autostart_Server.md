---
title: "Autostart Server"
date: 2005-07-19
forum: Server Platforms
---

### Post by gibbylinks on 2005-07-19
I've acquired an old PIII 500mhz PC and have successfully installed UBUNTU on it. I've done the default install, not the server one, but now decided I'd like to set it up as a server and share files between the two existing computers in the house (both running XP Pro, although mine dual boots with Hoary).

I've got Samba working and played with VNC, my question is

Can I set the box up so I can access it from my PC without having do anything on the server. I'd like to remove the screen and keyboard from the server, and just have to switch it on. Then access it remotely and configure it etc, then shutdown remotely when finished. 

Is this possible.

Is there any other things I could use it for ?

At the moment I have a cable router with all 3 PC's connected to that, which I use as a hub as well as internet access

Look forward to hearing your answers / comments

Paul ;-)

---

### Post by doclivingston on 2005-07-19
If you install "openssh-server" with Synaptic/apt-get, you can log in to a command line remotely (via ssh).

If you want remote GUI access it's a little more tricky, you have the choice of remote X sessions, ssh-forwarded X, VNC, FreeNX and possibly others. They all have their different strengths, but my preferred option is ssh-forwarded X, but that is only because the machine I am connecting from runs X as well (they're both Linux boxes).

---

### Post by gibbylinks on 2005-07-19
Thanks for quick response. 

I'll start looking at my VNC as I've already used that

 :smile:

---

