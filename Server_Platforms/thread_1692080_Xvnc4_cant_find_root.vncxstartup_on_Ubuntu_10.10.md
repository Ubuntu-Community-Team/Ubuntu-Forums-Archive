---
title: "Xvnc4 cant find /root/.vnc/xstartup on Ubuntu 10.10"
date: 2011-02-20
forum: Server Platforms
---

### Post by waltercoan on 2011-02-20
Hi,
 
Im trying to reconfigurate my Ubuntu Server, to use VNC multsession clients. For this i'm using xinetd and vnc4server. Like i used on Ubuntu 8.4 and works fine. But in Ubuntu Server 10.10, when the Vnc Viewer Cliente conect to the server on port 5900 I just receved an grey screen, and the server dont run gnome-session. This occours with when i starting Xvnc using xinetd. But if i'm loggin using root user, and start the server in the commando line like this:
vnc4server -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -SecurityTypes None -Protocol3.3
the Xvnc4 reads /root/.vnc/xstartup and run gnome session.
 
This is my xinetd file:
service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/Xvnc4
server_args = -inetd -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -SecurityTypes None -Protocol3.3
port = 5900
}
 
Walter

---

### Post by scott8035 on 2011-03-21
Did you ever find an answer to this? I'm having the same problem.

---

### Post by scott8035 on 2011-03-24
I finally gave up on this, started fresh from a snapshot of my system, and installed xrdp and vnc4server. Worked right out of the box. Very frustrating. I will be trying VNC again when 11.04 comes out.

---

