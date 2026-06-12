---
title: "Installing VNC server"
date: 2009-12-18
forum: Server Platforms
---

### Post by TheAJ on 2009-12-18
Hello,

I recently installed a desktop environemnt (using sudo apt-get install ubuntu-desktop) But my server is not located at my house, so i have to access it via a SSH right now. Is there a VNC server i can use to see the desktop environment?

And if so, how do i create users

---

### Post by BkkBonanza on 2009-12-18
The desktop has VNC available by default. It's called "Remote Desktop" in the System, Preferences menu. You can enable that and then access it remotely using ssh as a tunnel for security. There's quite a few thread/tutorials around for that.

Another way, perhaps more native to Linux, is using X forwarding. With that you don't even have to install the desktop on the server. This is usually also done over ssh for security.

---

### Post by HermanAB on 2009-12-19
Hmm, just bear in mind that VNC is the favourite way to get your system hacked, since there are automated scripts out there that does it.

Why don't you just launch a gnome panel with SSH?
$ ssh -X -C -c blowfish user@server gnome-panel

That also works from Windows using Xming and PuTTY.

---

### Post by kadeous on 2009-12-19
[http://havetheknowhow.com/Configure-the-server/Install-VNC.html](http://havetheknowhow.com/Configure-the-server/Install-VNC.html)

This will walk you step by step.

---

### Post by holastickboy on 2009-12-19
I would recommend you use something a little more secure, and it just works better than vnc:

Nxclient and Nxserver

---

