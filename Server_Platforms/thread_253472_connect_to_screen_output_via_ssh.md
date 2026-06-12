---
title: "connect to screen output via ssh"
date: 2006-09-08
forum: Server Platforms
---

### Post by alanandhispc on 2006-09-08
Hi,

i left an apt-get install process running on the screen output of my ubuntu server.
is there a way i can ssh into the server and then be given the session that goes to the monitor, so i can carry on with apt-get install?


Alan

---

### Post by bswilson on 2006-09-08
Not that I'm aware of, unless you use **screen** first.  Screen is a cool program that allows you to detach and later reattach to shell sessions.

I have trained myself that when I open a terminal session to kick off screen first thing.  You can name the sessions, too.  Try this:

```
screen -S mysession
```

You'll have a new shell called 'mysession' that you can detach from and later reattach from anywhere (locally, remotely, whatever).  Check out the man pages for screen to learn the commands you want.

---

