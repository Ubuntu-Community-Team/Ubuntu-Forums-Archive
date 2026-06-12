---
title: "Ubuntu server as host for guest Desktop"
date: 2010-08-15
forum: Server Platforms
---

### Post by joerg_ac on 2010-08-15
Hi,

I am going to set up an Ubuntu 10.04 server mainly to get a clean file-server with a big raid array. It is supposed to run without a desktop for most of the time. On top of this I would like to use KVM in order to use guests, which are desktops. So if I attach a monitor to my server I want it to serve me with a (virtualized) desktop system.

Questions:
- Can a desktop with GUI run in a VM on a server/host which does not have a GUI? 
More specifically: Will the Desktop guest be able to get the screen for graphical output? If yes, would this be hard to achieve?

- If this works, will I still get direct access to the server's console. I mean, by switching full-screen between the server console and the guest desktop's GUI. 

- In this setup, it would also be possible to run two desktop guests in parallel. Probably Windows and Ubuntu Desktop. Could I simply switch in-between them and the host's console for example by using a Keyboard shortcut.


Of course I could use Ubuntu desktop as the host, but the server is most of the time running standalone. I want a clean server and separate the desktop as much as possible. For remote server configuration I also plan to use eBox. Thus, I do not need to sit in font of the server except if I want it to provide a desktop to me. 

Does this plan sound very weird to you. To me it makes perfect sense, because the box the server is running on is much too powerful to be only a home-fileserver. Also, having the desktop in a VM allows playing with it without risking the well configured server. I like this way of getting a desktop much more than installing the Ubuntu-desktop package directly on top of the server as it is discussed often in this forum. 
I am a little bit worried that my plan does not work, because I read somewhere that KVM on top of Ubuntu server is mainly made for virtualized server guests. 

Many thanks in advance for your opinion and advice, Joerg

---

### Post by joerg_ac on 2010-08-15
Hi,

Let me rephrase my question:

Is it possible to run a guest system with GUI on a host (KVM, VirtualBox) without a GUI? Can the guest GUI be visible on a screen attached to this server box although the host system is only running a CLI?

I want to use Ubuntu server with eBox. Occasionally I want to be able to start a desktop (or even many desktops like a linux and a Windows one) on this same machine and work with it locally (not remotely) sitting in front of this server box. 

If this does not work well: should I better install Ubuntu desktop as host and use it as server (mainly file server). I would then have no problems running further desktops using Virtual Box. Does eBox support Ubuntu Desktop?

Another alternative might also be installing Ubuntu Server and adding a GUI to it. Then use Virtual Box or KVM to get the other VMs.

What do you think? What will be the best way to go? The central Idea is having a lightweight and remotely (eBox) managed server by default (Monitor stays off) and if I need a desktop of any type, I want this server to provide it to me locally. I also want  server as separated from the desktops as possible and to be flexible to run different desktop systems is needed.

best regards, Joerg

---

