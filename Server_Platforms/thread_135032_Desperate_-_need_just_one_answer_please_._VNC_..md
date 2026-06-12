---
title: "Desperate - need just one answer please .: VNC :."
date: 2006-02-23
forum: Server Platforms
---

### Post by CosMix on 2006-02-23
Hey there,

Im just curious about one thing...can i set another port on which vnc server would accept connections in order to be able to have two or more simultaneous connections on one vnc server ?...like...can i add another port in this conf file ?


service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
port = 55566
port = [COLOR="Red"]can i add another port here?[/COLOR]
}

And btw Tichondrius, great howto! Wish there were more ppl like you...willing to help and above all, able to help.

Gorazd

---

### Post by suRoot on 2006-02-23
Just start another instance of vncserver.  You can then connect to <ip_address>:1 ...  start yet another & you can connect to <ip_address>:2 ...  so on & so on.

---

