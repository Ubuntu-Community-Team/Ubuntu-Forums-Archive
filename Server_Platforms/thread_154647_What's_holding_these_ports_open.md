---
title: "What's holding these ports open?"
date: 2006-04-03
forum: Server Platforms
---

### Post by Aglarond on 2006-04-03
I'm an Ubuntu newbie and I'm trying to lock my machine down as much as possible. I have a couple of ports open I'm not sure about, though.

# netstat -na | grep LIST | grep -v STREAM
tcp        0      0 127.0.0.1:55528         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53422         0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN

# netstat -na | grep EST | grep -v STREAM
tcp        0      0 127.0.0.1:43860         127.0.0.1:53422         ESTABLISHED
tcp        0      0 127.0.0.1:53422         127.0.0.1:43860         ESTABLISHED
tcp        0      0 192.168.0.10:42265      72.14.205.19:80         ESTABLISHED
tcp6       SSH CONNECTION

# lsof -Pi
COMMAND     PID      USER   FD   TYPE DEVICE SIZE NODE NAME
firefox-b blah blah blah


What's using 43860 and 53422? It's not a security problem; I'm just curious what these ports are for. I've never run GNOME before, so I'm thinking it might have something to do with that.

Thanks
Mike

---

