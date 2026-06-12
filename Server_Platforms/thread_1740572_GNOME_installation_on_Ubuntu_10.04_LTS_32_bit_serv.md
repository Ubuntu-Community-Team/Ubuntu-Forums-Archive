---
title: "GNOME installation on Ubuntu 10.04 LTS 32 bit server"
date: 2011-04-27
forum: Server Platforms
---

### Post by rohitnagare on 2011-04-27
Hi,

I have created a vm on vmware and installed  Ubuntu 10.04 LTS 32 bit server. But i am getting graphical console. For that i need to install GNOME packages i dont have direct internet connection for this i am downloading the packages and installing. So can you you help me i need to install GNOME, VSFTPD and VNC package. From where shall i download and install.


Regards
Rohit

---

### Post by dtfinch on 2011-04-27
If you just need to run one gui program, and you're only accessing it remotely, you can get away with a lot less than gnome.

Without vnc, you can just ssh to any server, giving the -X option to enable X11 forwarding. When you run the program, assuming you're running an X server (on Windows that'd probably be Xming), the program will just display locally, even though it's running on a server.

If vnc is really needed, you can install just xvfb (headless (renders to memory instead of screen) x11 server) and x11vnc. I'm not sure what their dependencies are though, probably several. Then you'd have a startup script for that one program something like this:
```
#!/bin/bash
export DISPLAY=:1
Xvfb :1 -screen 0 1280x800x16 &
sleep 1
x11vnc -display :1 -bg -nopw -forever -xkb &
sleep 1
*run the program here*
killall x11vnc
killall Xvfb
```
You'd probably want to take out the "-nopw" and specify a password though. And change the resolution to match your preference. And in my case, I use it to run a full-screen program so window borders weren't needed, but if you need them you'll have to install a window manager and run it before your program.

As for installing without an internet connection, if you download them on one system (apt-get has a -d option for download-only), you can copy the packages from /var/cache/apt/archives. If you can ssh to it, you can upload files via scp (Gnome can mount and browse ssh, or on Windows you can use winscp)

---

