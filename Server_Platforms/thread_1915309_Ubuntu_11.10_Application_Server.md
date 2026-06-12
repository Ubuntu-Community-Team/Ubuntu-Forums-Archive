---
title: "Ubuntu 11.10 Application Server"
date: 2012-01-26
forum: Server Platforms
---

### Post by Monery on 2012-01-26
Hello everyone,
 
I am looking at building a Ubuntu Application Server mostly for fun, but also for the learning experience. I am curious if anyone else has tried to do a remote GUI from the 11.10 server and actually had it work correctly with Unity. 
 
My last attempt was to use XRDP but when trying to log into the server, all I got was a blue background with no text and/or controls on it. 
 
The only requirements that I have at the moment is that Windows 7 and Linux Mint 12 machines will be able to connect. Also, the remote connections will be on the LAN as well as over the Internet.
 
Any susgestions on how to start this project would be valuable

---

### Post by Wayne_V on 2012-01-26
I use x11vnc tunneled over ssh with no problems:

on the server:  /usr/bin/x11vnc -shared -bg -o /var/log/x11vnc.log -avahi -forever -auth /var/run/lightdm/root/:0 -rfbauth /home/<user>/.vnc/passwd -ncache 10 -xkb -display :0

you must create .vnc/passwd  with vncpasswd and you may need to change the -auth file and you may or may not need the -xkb option (tightvnc client on Mac seems to need it in order to get upper case characters).  see 'man x11vnc' for other possible options.

on the client system, forward the port over ssh (assuming server is using default port 5900 and you want to use 5902 on the client system):

ssh -N -t -L 5902:localhost:5900 <user>@<server>

and then just connect whatever vnc viewer you like to localhost port 5902

---

