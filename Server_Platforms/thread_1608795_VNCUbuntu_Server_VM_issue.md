---
title: "VNC/Ubuntu Server VM issue"
date: 2010-10-29
forum: Server Platforms
---

### Post by etech22 on 2010-10-29
Hi,

I'm experiencing a strange keyboard issue which may be a bug. Here's the setup:

-VNC connection from Ubuntu 10.04 using Terminal Server Client,
connecting to an Ubuntu 10.04 Desktop host,
-I am accessing an Ubuntu Server 10.04.1 VM running in VirtualBox (v3.2.10), not directly, but through the VBox GUI running on the 10.04 host.

What is happening is: at any command line, key presses are preceded by "[P". So, if I want to type in "what", then the characters on screen appear as "[Pw[Ph[Pa[Pt".

The problem does not exist when using the VM from the local host terminal, rather than VNCing into the the host. Also, no other VMs on the host experience this problem while using VNC. Windows guests, or Ubuntu Desktop guests on the same host register key presses properly.

What could be causing this for Ubuntu Server guests?


etech

---

### Post by gordintoronto on 2010-10-29
I think you should use a VNC client.

---

### Post by david.garceau on 2010-10-29
that happened to me once, all i did was press like all your ctrl buttons, alt, shifts, (not all at the same time) and then click in and out of the window and keep trying it.

---

### Post by hantechbl on 2010-10-29
Use SSH it's easy and awesome and fast, I was a noob at this like a week ago but after you figure out the basic commands you get very comfortable (You can do things you couldn't do before).

---

### Post by CharlesA on 2010-10-29
Depending on what VNC server you are using, the keymappings might be screwed up.

I ran into [this bug]("http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html") with tightvnc server on 9.04, but since then I haven't bothered running a GUI on my server.

It would be easier to just forward X over SSH and start the VBox GUI that way.

---

### Post by etech22 on 2010-11-01
Thanks for the replies. Sorry for the late response.

> **hantechbl said:**
> Use SSH it's easy and awesome and fast, I was a noob at this like a week ago but after you figure out the basic commands you get very comfortable (You can do things you couldn't do before).

I've been using SSH since I setup the system, but it's for installing the VM guest on the server, that I need VNC access.

> **CharlesA said:**
> Depending on what VNC server you are using, the keymappings might be screwed up.

I ran into [this bug]("http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html") with tightvnc server on 9.04, but since then I haven't bothered running a GUI on my server.

It would be easier to just forward X over SSH and start the VBox GUI that way.

Tried a couple of these fixes on both the Desktop host, and the Server guest with no change :/.

I'm not sure if forwarding X over SSH will work for what I'm doing..unless you mean connecting to the Desktop host over SSH, then installing/setting up the Server VM guest via command line. I'll have to figure out how to get a VBox guest instance running over SSH..

thanks,

etech

---

### Post by CharlesA on 2010-11-01
> **etech22 said:**
> 
I've been using SSH since I setup the system, but it's for installing the VM guest on the server, that I need VNC access.

Depending on what VM software you are using, you don't *need* access to a GUI.

I've been running VirtualBox headless for a while, administering it via SSH and using phpvirtualbox for more complicated admin stuff (snapshots, import/export, etc).

I've also forwarded X over SSH to get to the GUI if I needed to, but I've found that phpvirtualbox works wonders for my setup (but you need to make sure it's secured properly, since it doesn't include authentication (yet).

> 
I'm not sure if forwarding X over SSH will work for what I'm doing..unless you mean connecting to the Desktop host over SSH, then installing/setting up the Server VM guest via command line. I'll have to figure out how to get a VBox guest instance running over SSH..

You can forward the VirtualBox GUI over SSH, just connect with ssh -X user@host and start VirtualBox.

Works like a charm. :)

---

### Post by etech22 on 2010-11-01
> **CharlesA said:**
> You can forward the VirtualBox GUI over SSH, just connect with ssh -X user@host and start VirtualBox.

Wow, this opens a whole new world of possibility. Thanks! :)

---

### Post by hantechbl on 2010-11-03
> **etech22 said:**
> Wow, this opens a whole new world of possibility. Thanks! :)

have you looked into phpvirtualbox?

---

