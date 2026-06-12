---
title: "Server gnome desktop"
date: 2009-05-19
forum: Server Platforms
---

### Post by FarehamWeather on 2009-05-19
Hey Guys,

I would like to know how to install the gnome desktop onto the server edition and enable it to work through SSH.

From my understanding you can send a command using SSH and it will start gnome in the SSH client?

If so is there any HOW-TO tutorials ?

Thanks!
Chris

---

### Post by jonabyte on 2009-05-19
To start gnome or any desktop from the cli, the command is:

```
sudo startx
```

if you want to connect to that desktop remotely, you may want to use vnc.

---

### Post by jonabyte on 2009-05-22
A new video on Linux Journal might help:

[http://www.linuxjournal.com/video/access-remote-gui-programs-using-ssh-forwarding]("http://www.linuxjournal.com/video/access-remote-gui-programs-using-ssh-forwarding")

---

### Post by jasonsjunk on 2009-05-22
To install the gnome desktop on the server edition you will need to use sudo apt-get install ubuntu-desktop  from the cli.  

I use the built in remote desktop Vino I believe to connect to my server remotely with a gui when needed.  I wouldn't recommend Vino for outside your network I would run VNC instead.

---

