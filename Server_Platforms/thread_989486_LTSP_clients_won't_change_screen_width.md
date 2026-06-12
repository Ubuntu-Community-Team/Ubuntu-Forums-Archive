---
title: "LTSP clients won't change screen width"
date: 2008-11-21
forum: Server Platforms
---

### Post by mrfr0g on 2008-11-21
I have been trying to get my users setup using light terminals. I have setup an Ubuntu LTSP server, with a remote desktop scrip that automatically launches the user in to an RDP session with the Windows Terminal that we have setup. The terminals can connect fine over the network, and get connected to the remote server. The problem is, I can't seem to make the clients use both monitors that are connected to the terminal.

Each box has a nvidia chipset, lspci shows it as nvidia 5500. I've tried to install the nvidia-glx package in /opt/ltsp/i386 which seems to cause the box to error out, and not display anything. I've added a MODE_0 2048x768 to the ltsp.conf file, but again that doesn't seem to do anything.

In a normal setup, I would just install nvidia-glx, and configure xorg.conf, but I'm unsure how to do that with the light client.

Any help on this would be greatly appreciated.

---

